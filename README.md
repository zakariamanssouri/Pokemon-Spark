# Pokemon Spark

Practicing the Manipulation of  Spark RDDS  with the Pokemon Example.

## Dataset

i used the dataset from kaggle ,you can find it from the project folder.

## Load the dataset into an RDD

```bash
val data = sc.textFile("hdfs://localhost:9000/spark/Pokemon/Pokemon.csv")
```

## Remove the schema from the dataset

```bash
val header = data.first()
val datanoheader = data.filter(line=> !line.equals(header))
```

## Find and show all water pokemons

```bash
val waterPokemons = datanoheader.filter(line=> line.contains("Water"))
```
![image](https://user-images.githubusercontent.com/80859231/162544028-b5f9bdb7-d36b-4042-a52b-69bf1820663d.png)

## Find and show all Fire pokemons

```bash
val FirePokemons = datanoheader.filter(line=> line.contains("Fire"))
```
![image](https://user-images.githubusercontent.com/80859231/162544158-cf095465-4122-4c01-96d1-ab427063b610.png)

## Get and show the defense pokemons
```bash
val defenseList = datanoheader.map(x=>x.split(",")).map(x=> (x(6).toDouble,x(1)))
```
![image](https://user-images.githubusercontent.com/80859231/162544732-133daebc-96c4-41da-a36f-de4c67b9e789.png)
