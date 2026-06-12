---
title: "starting things at boot"
date: 2006-10-02
forum: Desktop Environments
---

### Post by pwrstick on 2006-10-02
Hello,

How do you get a program to load at boot?

I seem to understand that init.d and rcx.d have something to do with it (x being a number seemingly from 0 to 6).  Also, I seem to understand that there are symbolic links in the rc* folders that point to scripts in /etc/init.d.

OK so maybe I get that part, but how the hell do you add something correctly?! :-D

Also, what's up with the K and S, and two digit number code in those directories?  Here's partial output for 'find ssh rc* |grep ssh' while in /etc/

```
rc0.d/K20ssh
rc1.d/K20ssh
rc2.d/S20ssh
rc3.d/S20ssh
rc4.d/S20ssh
rc5.d/S20ssh
rc6.d/K20ssh
```

Why are some K and some S?  And why do they all seem to be the same thing?

Thanks so much for helping me understand.

Cheers,
-Phil

---

### Post by liquilife on 2006-10-02
Can't answer your other question but in Gnome if you want to load anything at boot you can go to System > Preferences > Session. From there select the "Startup Programs" tab. Hope that helps :D

---

### Post by pwrstick on 2006-10-02
Well I'm sure people that were unaware of that will find that helpful.  Right now I'm in command line only so not so much for me :-D

---

### Post by donatell0 on 2006-10-02
You use the > #update-rc.d <scriptname> defaults to make the script run at bootup. Just man for details. Its really simple.

---

