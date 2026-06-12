---
title: "mysql in amarok"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Josef K. on 2006-02-10
I'm trying to activate mysql support in amarok
unfortunately the wiki don't explain anything :(
however, I've apt-get install mysql-client mysql-server (guess I need it, right?) 
then the wiki says to setup a password
> set password for root@localhost = password('xxxxxxx');
with your password instead of xxxxxx
but I got this error
> bash: syntax error near unexpected token `('
can somebody help me?

---

### Post by Mopatop on 2006-02-10
Hey

That command is for the MySQL shell, not the command line. Run "mysql -u root" first, then do set password etc...

---

### Post by Josef K. on 2006-02-10
I'm afraid I'm still missing something :-k

> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by trawler on 2006-05-02
I seem to be having the same problem.

Although I'm using KDE (3.5.2) and installed amarok from source, It won't connect to mysql db either.

I kept getting "access denied" when connecting to the db. Now amarok simply crashes before it loads up.

I've enabled mysql log, and here's why i think it won't connect:

```
060502 17:40:19       5 Connect     Access denied for user 'amarok'@'localhost'                                  (using password: YES)
```

This is how the log looks when I try to log into the mysql db manually:
```
060502 17:41:01       9 Connect     amarok@localhost on
060502 17:41:15       9 Quit
```

Seems like amarok isn't sending the correct string, and therefore, unable to connect. 

Anyone knows how to workaround this?

---

