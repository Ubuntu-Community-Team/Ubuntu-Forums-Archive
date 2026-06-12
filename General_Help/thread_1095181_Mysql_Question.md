---
title: "Mysql Question"
date: 2009-03-13
forum: General Help
---

### Post by huntzcom on 2009-03-13
Hello,

I have installed Ubuntu and setup Mysql on a server and have successfully setup DBTools on my own pc to remote administer mysql databases on this server.

I have given myself root access remotley and within Mysql Administrator I've given full permissions to the three current databases ie information_schema, lost+found and mysql. I can create tables within these databases but when I try to create a new database it says "Access denied for user 'root'@'server' to database 'mynewdatabase'.

Does anyone know what I need to do to allow myself to create a database remotely. I feel its a permissions thing.

Thanks in advanced :)

---

### Post by justleen on 2009-03-13
by default root has only access from localhost..
you have to edit root permissions on tyour DB server to allow it to connect from other hosts then localhost

---

### Post by huntzcom on 2009-03-13
Sorry if I've miss understood you, I have already got root access remotely.

If I haven't understood you how can I give root permission to create a database.

Thanks

---

### Post by ahop on 2009-03-13
Where is your mysql being located, remotely? With a webhosting company?

---

### Post by huntzcom on 2009-03-14
No its a server i created and installed Mysql. Im accessing it over the network with dbtools on my pc. I can see the three tables that are there by default and I can edit them but I can't create a new database. It's saying no permissions.

---

### Post by huntzcom on 2009-03-16
No one have any idea about this? 

Thanks

---

### Post by LoneWolfJack on 2009-03-16
```

REVOKE ALL PRIVILEGES ON * . * FROM 'root'@'127.0.0.1';

GRANT ALL PRIVILEGES ON * . * TO 'root'@'127.0.0.1' WITH GRANT OPTION;

```

---

### Post by huntzcom on 2009-03-16
After I ran the first query I lost the permissions to run the second. Can anyone tell me how to get them back?

---

### Post by LoneWolfJack on 2009-03-16
you should still be able to log in to mysql by typing this on the shell:

```
mysql -uroot -p<pass>
```

then run the second command from above from there.

---

### Post by huntzcom on 2009-03-16
Access denied for user 'root'@localhost'. Uh oh.

---

### Post by unutbu on 2009-03-16
I'm not sure how to solve your original question, but I think I can help you get back your root privileges. Log into the machine running  the mysql server.
Then type the following lines. Lines that start with "mysql>" are commands typed into the mysql client application (as opposed to shell commands). Do not type "mysql>"; only type the stuff after that.

```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> update mysql.user set Super_priv='y' where user='root';

```
I'm not entirely sure this is the only privilege that you need to change. If the "GRANT" command below still does not work, post back here and I'll give you a longer command which I think is sure to work.
```

mysql> flush privileges;
mysql> quit;
sudo /etc/init.d/mysql start
mysql -u root -p
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'127.0.0.1' WITH GRANT OPTION;
mysql> quit;
```

---

### Post by LoneWolfJack on 2009-03-16
assuming you entered the right pass, you will probably have to reset the root password:

[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix]("http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix")

---

### Post by LoneWolfJack on 2009-03-16
ok, for speed's sake try unutbu's variant first and let us know if that did the trick :)

---

### Post by huntzcom on 2009-03-16
Im confused about the line below.
```

sudo mysqld --skip-grant-tables &
mysql

```

Is it
```

sudo mysqld --skip-grant-tables & mysql

```

?

---

### Post by stephenclarke on 2009-03-16
Hi,

They are two different commands.

Run the first line (including the &) and press enter.

Then run mysql after.

The & simply means to run the first process in the background.

Regards,
Steve

---

### Post by huntzcom on 2009-03-19
> **unutbu said:**
> I'm not sure how to solve your original question, but I think I can help you get back your root privileges. Log into the machine running  the mysql server.
Then type the following lines. Lines that start with "mysql>" are commands typed into the mysql client application (as opposed to shell commands). Do not type "mysql>"; only type the stuff after that.

```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> update mysql.user set Super_priv='y' where user='root';

```
I'm not entirely sure this is the only privilege that you need to change. If the "GRANT" command below still does not work, post back here and I'll give you a longer command which I think is sure to work.
```

mysql> flush privileges;
mysql> quit;
sudo /etc/init.d/mysql start
mysql -u root -p
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'127.0.0.1' WITH GRANT OPTION;
mysql> quit;
```

Im getting this message when running the GRANT line.

Access denied for user 'root'@'localhost'

---

### Post by huntzcom on 2009-03-19
At this point it might not be an idea to remove mysql and install it again. Anyone know whats the easiest way to do this? :cry:

---

### Post by unutbu on 2009-03-19
I think I might have made a minor mistake in my previous post: the command
```

sudo /etc/init.d/mysql start

```
does not kill the "mysqld --skip-grant-tables" process. I think this might lead to errors when trying to use the GRANT command.
So, perhaps the easiest thing to try is 

```

sudo /etc/init.d/mysql restart
mysql -u root -p
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'127.0.0.1' WITH GRANT OPTION;
mysql> quit;
```

If you get the same error, then try the following:
Save this in restore_root_privileges.sql
```

update mysql.user set Super_priv='y' where user='root';
update mysql.user set Select_priv='y' where user='root';
update mysql.user set Insert_priv='y' where user='root';
update mysql.user set Update_priv='y' where user='root';
update mysql.user set Delete_priv='y' where user='root';
update mysql.user set Create_priv='y' where user='root';
update mysql.user set Drop_priv='y' where user='root';
update mysql.user set Reload_priv='y' where user='root';
update mysql.user set Shutdown_priv='y' where user='root';
update mysql.user set Process_priv='y' where user='root';
update mysql.user set File_priv='y' where user='root';
update mysql.user set Grant_priv='y' where user='root';
update mysql.user set References_priv='y' where user='root';
update mysql.user set Index_priv='y' where user='root';
update mysql.user set Alter_priv='y' where user='root';
update mysql.user set Show_db_priv='y' where user='root';
update mysql.user set Super_priv='y' where user='root';
update mysql.user set Create_tmp_table_priv='y' where user='root';
update mysql.user set Lock_tables_priv='y' where user='root';
update mysql.user set Execute_priv='y' where user='root';
update mysql.user set Repl_slave_priv='y' where user='root';
update mysql.user set Repl_client_priv='y' where user='root';
update mysql.user set Create_view_priv='y' where user='root';
update mysql.user set Show_view_priv='y' where user='root';
update mysql.user set Create_routine_priv='y' where user='root';
update mysql.user set Alter_routine_priv='y' where user='root';
update mysql.user set Create_user_priv='y' where user='root';
flush privileges;
```

Then run ```

sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql < restore_root_privileges.sql

sudo /etc/init.d/mysql restart
mysql -u root -p
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'127.0.0.1' WITH GRANT OPTION;
mysql> quit;

```
Hope that helps.

---

### Post by huntzcom on 2009-03-19
Where would I save the restore_root_privileges.sql
 file?

Thanks for all your help btw.

---

### Post by unutbu on 2009-03-19
Save it in your normal user home account directory. 
When you open a terminal as a normal user, it will automatically use your home account directory as its current directory.
That way, the command 
```

mysql < restore_root_privileges.sql
```

will find restore_root_privileges.sql.

If you choose to save it somewhere else, like /root/restore_root_privileges.sql, then simply change the command to 

```

mysql < /root/restore_root_privileges.sql
```

---

