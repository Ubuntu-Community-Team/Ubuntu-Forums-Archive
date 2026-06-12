---
title: "Cannot access mysql prompt"
date: 2009-02-27
forum: General Help
---

### Post by satish_j on 2009-02-27
I installed mysql5 on Hardy from tar.bz file and iam not able to start the mysql command prompt window.
I can start the daemon,but on typing 'mysql',I get error as follows:'The program 'mysql' is currently not installed.  You can install.....'

Any answers....

```

satish@TITAN:/usr/local/mysql$ bin/mysqld_safe &
[1] 6922
satish@TITAN:/usr/local/mysql$ nohup: ignoring input and redirecting stderr to stdout
Starting mysqld daemon with databases from /usr/local/mysql/data
mysql
The program 'mysql' is currently not installed.  You can install it by typing:
sudo apt-get install mysql-client-5.0
bash: mysql: command not found
satish@TITAN:/usr/local/mysql$ killall mysqld 
satish@TITAN:/usr/local/mysql$ STOPPING server from pid file /usr/local/mysql/data/TITAN.pid
090228 00:09:54  mysqld ended



[1]+  Done                    bin/mysqld_safe

```

---

### Post by cariboo on 2009-02-27
Is there a reason why you didn't use the version that is in the repositories?

Jim

---

### Post by satish_j on 2009-02-27
Yes,I need to install the same from source for learning more about package installation on Linux without synaptic

---

### Post by satish_j on 2009-02-27
Got the cause of the problem..
Had not set the Environment variable for mysql...
tried with the entire path of mysql i.e instead of typing just 'mysql' at prompt,I typed '/usr/local/mysql/bin/mysql' and the Mysql prompt was displayed.
Prob solved..

---

