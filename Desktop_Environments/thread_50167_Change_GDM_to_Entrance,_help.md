---
title: "Change GDM to Entrance, help"
date: 2005-07-19
forum: Desktop Environments
---

### Post by songochain on 2005-07-19
Hi all! i'm with E17 now and i want to know how can i make entrance my default display manager.
Thanks!

---

### Post by SGC on 2005-07-19
Try this command:
dpkg-reconfigure entrance

---

### Post by songochain on 2005-07-19
Done, but i've used this 
```
update-rc.d entrance start 99 2 3 4 5 . stop 01 0 1 6 .
```
I've a problem, always boot in gnome if i use entrance. I choose enlightenment in entrance but anyway i always boot in gnome

---

### Post by cutOff on 2005-07-19
[QUOTE=songochain]Done, but i've used this 
```
update-rc.d entrance start 99 2 3 4 5 . stop 01 0 1 6 .
```
I've a problem, always boot in gnome if i use entrance. I choose enlightenment in entrance but anyway i always boot in gnome[/QUOTE]
Maybe this help you  [http://ubuntuforums.org/showpost.php?p=216038&postcount=74](http://ubuntuforums.org/showpost.php?p=216038&postcount=74)

---

### Post by songochain on 2005-07-19
I can boot into e17 using gdm but with entrance not

---

### Post by cutOff on 2005-07-19
How did you install E17 and Entrance? If you follow this [howto](http://ubuntuforums.org/showthread.php?t=46105) you probably will not have any problem to loging in from Entrance.

---

### Post by wrtrdood on 2005-07-19
I had trouble with this too and the suggested fix didn't work for me.  I ended up adding a .xsession file to my login directory and kicking off Enlightenment from there.  I've not had the time to figure out why it's not reading the system files correctly.

---

### Post by songochain on 2005-07-19
[QUOTE=cutOff]How did you install E17 and Entrance? If you follow this [howto](http://ubuntuforums.org/showthread.php?t=46105) you probably will not have any problem to loging in from Entrance.[/QUOTE]
Yes, I did it following this how-to. It's rare, with gdm it's ok but with entrance not...

---

### Post by songochain on 2005-08-03
I think the problem is that i dont know add user to entrance so...

---

### Post by vladuz976 on 2005-08-17
i am having similar trouble.
i installed e17 from cvs and also entrance i get my entrance to run but i can't log into e17 from it. it always falls back to entrance.
i used edb_gtk_db to edit /etc/entrance_config.db file but everything in there looks right to me. anybody know what to do?

---

