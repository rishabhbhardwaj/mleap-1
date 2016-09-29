# Running MLeap with Jupyter (on Mac)

## Install Jupyter and Toree

We are going to assume you already have the following installed:

1. Python 2.x
2. Docker (required to install Toree)

### Install Jupyter

```python
virtualenv venv

source ./venv/bin/activate

pip install jupyter
```

### Build and install Toree

Clone master into your working directory from Toree's [github repo](https://github.com/apache/incubator-toree/blob/master/README.md).

For this next step, you'll need to make sure that docker is running.

```bash
$ cd incubator-toree

$ make release

$ cd dist/toree-pip

$ pip install toree-0.2-dev.tar.gz

SPARK_HOME=$HOME/Lib/Spark jupyter install toree
```

### Launch Notebook and Include MLeap

If you built MLeap locally, you should first publish your jars to .m2:

```bash
sbt publishM2
```

Then in your notebook, you can include the jars by using AddDeps Magics:

 ```
 %AddDeps ml.combust.mleap mleap-spark_2.11 0.1-SNAPSHOT --transitive --repository file:///<path to .m2 directory>
 ```
 
 If you want to use the release version, then use this AddDeps Magic:
 
 ```
 %AddDeps ml.combust.mleap mleap-spark_2.11 1.0.0 —transitive
 ```
 