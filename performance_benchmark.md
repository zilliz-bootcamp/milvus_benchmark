# Performance Benchmark

This topic displays the performance of different index types in Milvus 0.10.0 for reference purposes. 

## Hardware

**CPU**: Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz (12 Cores)

**GPU**: GeForce GTX 1060 6GB 、 GeForce GTX 1660 6GB



## data

The test data uses an open source dataset, sift1B, with 1,000 million 128-dimensional vectors. For more information about this data set, please refer to: [Datasets for approximate nearest neighbor search](http://corpus-texmex.irisa.fr/).



## Description

The following table displays the terms used in this topic:

| Term   | Description                                    |
| ---------- | ---------------------------------------- |
| nq         | Number of vectors to query. The value is defined during search.    |
| topk       | The most similar topk search results.  |
| accuracy   | Recall rate of query results.                 |
| time       | Average search time per vector.       |
| nprobe     | Number of buckets to search during a query. The value is defined during search.  |

Performance is correlated with nprobe. The greater the value of nprobe, the lower the performance, but the higher the accuracy. You can set nprobe per specific scenarios. In this topic, nprobe is set to 32.

Refer to [https://medium.com/@milvusio/how-to-choose-an-index-in-milvus-4f3d15259212](https://medium.com/@milvusio/how-to-choose-an-index-in-milvus-4f3d15259212) to learn how to choose indexes.



## Test results navigation

[SiFT1m test result](Performance_bench.md# sift1m): In this test, the first 1,000,000 vectors from the sift1B data set are selected.

[SiFT10m test results](Performance_bench.md# sift10m): In this test, the first 10,000,000 vectors from the sift1B dataset are selected.

[Results of the SIFT100M test](Performance_bench.md# sift100m): In this test, the first 100,000,000 vectors from the sift1B dataset are selected.

In this test, the data was imported into Milvus in batches of 100,000, and the import time of 100,000 128-dimensional vectors was approximately : 1S



> parameter settings: nlist=4096, index_file_size=2048
>
> The following test results are queried by cpu and indexed by gpu.



## Sift1m

##### index：ivf_sq8

(Index creation time: 27s)

(nprobe: 256)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 98.2% | 98.3%  | 98.2% |
| topk=10  | 98.3% | 98.2%  | 98.4% |
| topk=100 | 98.4% | 98.4%  | 98.5% |
| topk=500 | 98.0% | 87.9%  | 98.0% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0026 | 0.0024  | 0.0025   | 0.0023   |
| nq=10   | 0.0099 | 0.0101  | 0.0106   | 0.0122   |
| nq=100  | 0.0699 | 0.0708  | 0.0706   | 0.0763   |
| nq=500  | 0.3356 | 0.3351  | 0.3567   | 0.439    |
| nq=1000 | 0.907  | 0.93    | 0.9226   | 0.9735   |



##### index ivf_sq8h

(Index creation time: 30s)

(nprobe: 256)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 98.8% | 98.0%  | 98.2% |
| topk=10  | 98.4% | 98.1%  | 98.5% |
| topk=100 | 98.6% | 98.7%  | 98.6% |
| topk=500 | 97.8% | 98.0%  | 97.8% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0027 | 0.0028  | 0.0029   | 0.003    |
| nq=10   | 0.011  | 0.0118  | 0.0119   | 0.0116   |
| nq=100  | 0.0638 | 0.0669  | 0.0657   | 0.0693   |
| nq=500  | 0.2852 | 0.2939  | 0.3013   | 0.354    |
| nq=1000 | 0.5974 | 0.603   | 0.6514   | 0.718    |



## sift10m

##### index ivf_sq8

(Index creation time: 138s)

(nprobe:128)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 97.2% | 97.6%  | 97.2% |
| topk=10  | 98.2% | 98.0%  | 97.8% |
| topk=100 | 98.4% | 98.9%  | 97.7% |
| topk=500 | 97.7% | 97.1%  | 97.3% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0048 | 0.0054  | 0.0057   | 0.0044   |
| nq=10   | 0.0433 | 0.0431  | 0.0442   | 0.0466   |
| nq=100  | 0.2653 | 0.2975  | 0.3053   | 0.2312   |
| nq=500  | 1.4938 | 1.4782  | 1.4198   | 1.5075   |
| nq=1000 | 2.9571 | 3.0626  | 3.1267   | 3.2935   |



##### index ivf_sq8h

(Index creation time: 143)

(nprobe:128)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 97.8% | 97.6%  | 98.4% |
| topk=10  | 98.1% | 98.3%  | 98.0% |
| topk=100 | 98.2% | 98.2%  | 98.1% |
| topk=500 | 97.6% | 97.3%  | 97.7% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0051 | 0.0047  | 0.0048   | 0.006    |
| nq=10   | 0.0499 | 0.05    | 0.0461   | 0.4812   |
| nq=100  | 0.3306 | 0.3263  | 0.3252   | 0.3379   |
| nq=500  | 1.4227 | 1.4162  | 1.5058   | 1.5132   |
| nq=1000 | 2.6893 | 2.7907  | 2.9995   | 3.0086   |

## sift100m

##### index ivf_sq8

(Index creation time: 229s)

(nprobe:64)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 96.6% | 96.8%  | 96.6% |
| topk=10  | 96.5% | 96.6%  | 96.2% |
| topk=100 | 94.8% | 95.2%  | 94.8% |
| topk=500 | 92.6% | 92.8%  | 92.6% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0194 | 0.0193  | 0.0203   | 0.0237   |
| nq=10   | 0.1592 | 0.1596  | 0.1632   | 0.1708   |
| nq=100  | 0.8353 | 0.8549  | 0.8732   | 0.9299   |
| nq=500  | 3.7656 | 3.7797  | 3.875    | 4.2264   |
| nq=1000 | 7.1181 | 6.9993  | 7.2212   | 7.7575   |

##### index ivf_sq8h

(Index creation time:  237)

(nprobe:64)

**Accuracy**

The department randomly took out 500 vector queries from the vector set to be queried, and the average value of the 500 results was taken out for recall rate, which was tested for a total of three times. The 500 vectors taken out each time were not completely the same.

| accuracy | first | second | third |
| -------- | ----- | ------ | ----- |
| topk=1   | 96.8% | 96.0%  | 96.4% |
| topk=10  | 96.3% | 95.8%  | 96.2% |
| topk=100 | 95.5% | 94.9%  | 95.3% |
| topk=500 | 93.5% | 92.4%  | 92.9% |

**Performance**

| time(S) | topk=1 | topk=10 | topk=100 | topk=500 |
| ------- | ------ | ------- | -------- | -------- |
| nq=1    | 0.0193 | 0.0195  | 0.0204   | 0.024    |
| nq=10   | 0.0856 | 0.0857  | 0.086    | 0.092    |
| nq=100  | 0.5063 | 0.5042  | 0.5212   | 0.6316   |
| nq=500  | 2.3709 | 2.3793  | 2.4304   | 2.6234   |
| nq=1000 | 4.3712 | 4.3877  | 4.4647   | 4.8881   |

















