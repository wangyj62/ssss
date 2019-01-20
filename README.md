# ssss
2.0版本风控系统，修改测试单风控状态由拒绝到通过的说明
=======
修改已经拒绝(reject)的借款单为通过(success)步骤
------
### 第一步
    修改原借款单的状态为10(审核中)。
    sql语句： update cl_borrow set state = '10' where id = xxx ;
### 第二步
    往mq上名称为cashloan_risk_control_result的topic上放入json字符串
    json字符串为: {"black":"no","borrowId":"xxx","decision":"success"}
#### 注意：第一步和第二步中的xxx应对应真实的借款单ID
