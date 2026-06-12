---
title: "Can't get permission to modify Frets on Fire"
date: 2008-10-10
forum: Gaming &amp; Leisure
---

### Post by jordanae on 2008-10-10
I'm not sure if this goes here, but I'm just thinking that maybe others have had this problem with Frets on Fire.

I just downloaded Frets on Fire and cannot put songs into the songs folder. It says that I don't have permission to modify the folder. I tried going to Properties and then Permissions, but that didn't work either.

So my question is how can I get permissions for this folder? Is there a sudo command that I can run or something?

---

### Post by roadtr1p on 2008-12-14
I'm having the same problem. Were you able to figure it out?

---

### Post by linuxguymarshall on 2008-12-14
I do not know where you placed your folder but run this in terminal 
```
gksudo nautilus
```

now you can move your files very easily

---

### Post by sbennettgso on 2008-12-20
Learn to use the chmod command.  It's needed for this and very helpful in general (but can be dangerous so be careful).  There are plenty of references that do a much better job of explaining this than I can.

Thanks,
Scott

---

### Post by Perfect Storm on 2008-12-20
Installing it in /home as $user instead of globally installation would be the proper way in this case.

---

