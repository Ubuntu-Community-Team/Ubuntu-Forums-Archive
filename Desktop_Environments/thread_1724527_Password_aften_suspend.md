---
title: "Password aften suspend"
date: 2011-04-08
forum: Desktop Environments
---

### Post by Azyx on 2011-04-08
I have in System-->Administraytion-->Login Screen setting checked  'Log as Azyx automatically' so then the computer boot up I don't need to  type password.

But when my laptop have going to suspend and wakeup I have to type my login password. How do I change so I don't need to do that?

/Cheers

---

### Post by metalf8801 on 2011-04-08
Try this and please report back on whether or not it works.

[http://ubuntuforums.org/showpost.php?p=2061391&postcount=4](http://ubuntuforums.org/showpost.php?p=2061391&postcount=4)

---

### Post by metalf8801 on 2011-04-08
Just found a better answer here [http://ubuntuforums.org/showthread.php?t=298944](http://ubuntuforums.org/showthread.php?t=298944)

I just cleaned up the solution a little 

1. Open gconf-editor it's not in the menu so press Alt-F2 and type or past in gconf-editor 

2. Open the fallowing folders Apps > gnome-power-manager > lock 

3. Uncheck the box next to suspend and/or anything else you want 


I hope this helps
Dan

---

### Post by Azyx on 2011-04-08
> **metalf8801 said:**
> Just found a better answer here [http://ubuntuforums.org/showthread.php?t=298944](http://ubuntuforums.org/showthread.php?t=298944)

I just cleaned up the solution a little 

1. Open gconf-editor it's not in the menu so press Alt-F2 and type or past in gconf-editor 

2. Open the fallowing folders Apps > gnome-power-manager > lock 

3. Uncheck the box next to suspend and/or anything else you want 


I hope this helps
Dan

Thanx for a quick responce :) I saw that there have being some change in gconf-editor, since the link. But unfortunally it did not work :( I change both in gconf-edit as user and after 'sudo', but I still get a inlogging promt. :(

PS. And also made a reboot after change

---

### Post by Azyx on 2011-04-08
I uncheck all boxes in lock.
And do you know how it how it affect the system if i user sudo or not? Other security risks or so?

---

### Post by metalf8801 on 2011-04-08
Give this a try
[http://ubuntuforums.org/showpost.php?p=9756347&postcount=11](http://ubuntuforums.org/showpost.php?p=9756347&postcount=11)

Thanks for replying that you have tried it as both root and as a regular user so I don't have to try that myself.

---

### Post by Azyx on 2011-04-08
Thanx :)  That did the trick :)

---

