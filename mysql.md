## mysql 条件递增

```
        $sql = "INSERT INTO communication (`uid`,`dept_id`,`sort`,`duty_id`) 
        VALUES ({$uid},{$dept_id},(SELECT IFNULL((MAX(a.sort)+1),0) as sort from communication as a where a.dept_id={$dept_id}),{$duty_id})";
```

## 分页

```
  $sql = "select SQL_CALC_FOUND_ROWS id,full_name,short_name,allpid FROM dept WHERE deleteflag=0 AND pid={$dept_id} ".$like ." limit $start, $page_size";

        $list = db_slave() -> fetchAll($sql);
        $count = db_slave() -> fetchColumn('select FOUND_ROWS()');
```

