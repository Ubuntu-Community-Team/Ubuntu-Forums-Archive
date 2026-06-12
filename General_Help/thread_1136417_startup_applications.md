---
title: "startup applications"
date: 2009-04-25
forum: General Help
---

### Post by 123456789123456789123456 on 2009-04-25
HI all, I found the startup applications section, I would like someone to explaine how to add one to the list.  I have a firewall program called firestarter installed on the system.  Everytime the system restarts, it is not loaded, I have to manually open the program every time.  This does get tedious.  When I go to add, it asks for the name, command, with a browse button beside it, and a discription under that.  Can someone help me in finding the command to run the program?
oh, system running is 9.04

---

### Post by AdamShumpisxXx on 2009-04-25
Go into Settings > Administration.

Click on Sessions and add an entry for Firestarter.

---

### Post by CatKiller on 2009-04-25
As I understand it, Firestarter configures iptables (which is included in the kernel and so is running all the time). As such, you don't need to have Firestarter running unless you are actually changing the configuration.

If you want to find out where a program's executable is kept, you can run

```
which *programname*
```

---

### Post by 123456789123456789123456 on 2009-04-25
thanks for all the help.  I can't get it added, when I add the entry, it tells me that root must have been logged in, in order to run the program.  I will trust that it is working, all the time, The thing I like about it, is that I can see at a glance what things have been blocked, and other information.  but I can live with it the way it is.

---

### Post by TheExplorer on 2009-04-25
1) Have you looked here: [http://www.fs-security.com/docs/persistence.php](http://www.fs-security.com/docs/persistence.php) ?
2) Google?
3) As far as I'm concerned **sudo /usr/sbin/firestarter** should be added to the startup list.

---

### Post by oldos2er on 2009-04-25
It's my understanding running Firestarter all the time is a security risk. See [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

