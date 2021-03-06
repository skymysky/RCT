## 新增RDB分析配置
只有先创建了redis节点之后，才能进入到RCT工具导航页面。
1.  点击导航RDB Analyze
2.  如若一直没有添加过RDB信息，则可在页面弹出的框中进行完善信息，或者点击下方的Add按钮进行添加
3.  点击edit则可以对RDB 信息进行修改
4.  如若已经完善了RDB信息，则点击打开switch开关，则是对RDB直接进行定时任务的开启和关闭 
5.  点击Analyze，则是对RDB信息进行手动分析，分析进行的状态可在status中查看，可以通过status后面的链接进入到实时查看rdb分析任务的进度状态 

## RDB Add页面参数说明
1.  **Automatic Analyze**：是否开启定时任务
2.  **Schedule**：cron 表达式（填写完成之后，可以点击右侧的图标进行查看定时表达式执行的时间）
3.  **Analyzer**:分析器 （依次是生成报表，根据filter导key，根据preix导key）
4.  **Data Path**:rdb文件的目录（eg:/opt/app/redis/9002/dump.rdb,data path应为/opt/app/redis）
5.  **Prefixes**:key的前缀，可为空，但是在选择了分析器中的根据preix导key，则必须填写prefixes
6.  **Report**：是否生成报表
7.  **Mail**：生成报表之后的收件人，平台将会将报表做为附件发送给收件人，如果收件人有多个，请用;隔开
## RDB 主页面参数说明
RDB主页面参数与add页面参数基本相同，在此不再做赘述，唯一有区别的是：
Status：分析RDB文件的进度状态，分为成功，正在分析，失败三种状态，status为正在分析状态时，可通过点击后面的链接进入到实时分析页面，查看实时状态。

##分析器介绍
1.生成报表：对rdb文件的数据进行分析并将结果写入数据库中，如果配置了Report，结果会以excel报表的形式发送邮件给用户
2.根据filter导key：在对rdb文件分析的时候，根据过滤器导出相应的key，将数据写入到EleasticSearch中
3.根据prefix导key：在对rdb文件分析的时候，根据制定的前缀key导出相应的key，将数据写入到EleasticSearch中