---
title: "akonadi server error"
date: 2014-03-29
forum: Desktop Environments
---

### Post by papapenguin on 2014-03-29
[COLOR=#000000][FONT=sans-serif]hi, I'm new to Kubuntu...just came over from Gentoo...help! [/FONT][/COLOR][IMG]https://www.kubuntuforums.net/images/smilies/grin.gif[/IMG]

[COLOR=#000000][FONT=sans-serif]I tried to import my Kmail and other Kontact info from my old hard drive, but with no luck...[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I then copied ALL of my home folder into the new home folder and most works without a hitch...except this Akonadi error...this may have been the wrong way to do things, I realize...[/FONT][/COLOR]
[http://pastebin.com/Gp2wxsBb](http://pastebin.com/Gp2wxsBb)

[COLOR=#000000][FONT=sans-serif]thanks![/FONT][/COLOR]

---

### Post by papapenguin on 2014-04-02
anyone?

bump?

Bueller?

---

### Post by oldos2er on 2014-04-02
```

InnoDB: Your database may be corrupt or you may have copied the InnoDB
InnoDB: tablespace but not the InnoDB log files. See
InnoDB: http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html
InnoDB: for more information.
```

Did you check the URL in the above?

---

### Post by papapenguin on 2014-04-03
thanks...I did look at that, but that may be way above my pay grade...

Is there a program that I can use to repair? I was looking at mysqlcheck...

```
donald@donald:~$ mysqlcheck -Amysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect



```

are there any other options?

---

