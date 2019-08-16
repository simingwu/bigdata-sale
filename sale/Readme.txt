1、分析数据为/file/SalesJan2009.csv

    上传到hdfs文件系统：$hadoop fs -put /home/hadoop/testData/SalesJan2009.csv  /user/hadoop/SalesJan2009/
    /home/hadoop/testData/SalesJan2009.csv 为linux目录下的文件
    /user/hadoop/SalesJan2009/ 为hdfs的文件目录


2、打包成jar：mvn package

      上传到hadoop集群环境：
      运行： $hadoop jar sale-0.0.1.jar /user/hadoop/SalesJan2009/SalesJan2009.csv /user/output/ 
  /user/hadoop/SalesJan2009/SalesJan2009.csv  为hdfs系统的数据源
  /user/output/   为hdfs系统的分析结果集
  
      运行结束后，从HDFS下载文件到本地
  $hadoop fs -get /user/output/part-r-00000 /home/hadoop/testData/
      
      查看结果： $cat /home/hadoop/testData/part-r-00000  