Managingv Hbase with Hive:
--------------------------
HIVE:
....
>> [training@localhost ~]$ hive

>> hive> create external table hbaserating (userid int,movieid int,rating int) stored by 
    > 'org.apache.hadoop.hive.hbase.HBaseStorageHandler' with serdeproperties ("hbase.columns.mapping"=":key,cf1:movieid,cf1:rating") tblproperties ("hbase.table.name"= "hbaserating");
    
>> hive> select * from hbaserating;

-----------------------------------------------------

HBase:
......

>> [training@localhost ~]$ hbase shell

>> hbase(main):001:0> list

>> hbase(main):002:0> create 'hbaserating','cf1'

>> hbase(main):003:0> put 'hbaserating', 'row1', 'cf1:movieid','42'

>> hbase(main):004:0> put 'hbaserating', 'row2', 'cf1:rating','5'

>> hbase(main):005:0> put 'hbaserating', 'row3', 'cf1:rating','21'

>> hbase(main):006:0> put 'hbaserating', 'row4', 'cf1:movieid','32'

>> hbase> scan '.META.'

>> hbase(main):009:0> scan 'hbaserating'
