---
title: "Mysql 4.1 Rollback is not working, why ?"
date: 2005-01-15
forum: General Help
---

### Post by ulefr01 on 2005-01-15
i have installed mysql-server-4.1 and mysql-client-4.1 (in fact it is 4.1.8a-4)

mysql> use test;
Database changed
mysql> set autocommit = 0;
Query OK, 0 rows affected (0.00 sec)

mysql> create table tran_test (a int, b int) type = InnoDB;
Query OK, 0 rows affected, 2 warnings (0.04 sec)

mysql> begin;
Query OK, 0 rows affected (0.00 sec)

mysql> insert into tran_test (a,b) values (1,2);
Query OK, 1 row affected (0.00 sec)

mysql> select * from tran_test;
+------+------+
| a    | b    |
+------+------+
|    1 |    2 |
+------+------+
1 row in set (0.00 sec)

mysql> rollback;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> select * from tran_test;
+------+------+
| a    | b    |
+------+------+
|    1 |    2 |
+------+------+
1 row in set (0.00 sec)

mysql> quit

Confer the Mysql Manual i should have an empty table after the second 'select' statement , but i haven't
The 'rollback' gives me 'Query OK, 0 rows affected, 1 warning (0.00 sec)' , why ?
Any ideas are welcome.

---

### Post by ulefr01 on 2005-01-16
problem is solved now.
My my.cnf file contains the entry "skip-innodb"
If i adapt this file and put this entry in comment.
Restart mysqld
Redo test
It works now

---

