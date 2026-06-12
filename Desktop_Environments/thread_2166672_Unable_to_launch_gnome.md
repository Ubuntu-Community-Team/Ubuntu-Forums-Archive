---
title: "Unable to launch gnome"
date: 2013-08-10
forum: Desktop Environments
---

### Post by EMP19E on 2013-08-10
After some tinker i have borked gnome......when i try to log in i get the following error
 
: unable to launch "gnome-session --session=ubuntu" X session ---
"gnome-session --session=ubuntu" not found; falling back to default session.

have done some searching and still have not found a solution to my problem

---

### Post by ibjsb4 on 2013-08-10
Hi emp19e, welcome to the forums :)

At boot, do you get the option to go to safe mode?  If not, try clicking on the "shift key" while booting.

Also you can try after the boot up to nothing:

Ctrl + Alt + F1

Did that get you to a terminal (text only screen)?

---

### Post by EMP19E on 2013-08-10
> **ibjsb4 said:**
> Hi emp19e, welcome to the forums :)

At boot, do you get the option to go to safe mode?  If not, try clicking on the "shift key" while booting.

Also you can try after the boot up to nothing:

Ctrl + Alt + F1

Did that get you to a terminal (text only screen)?

Thank You.

I can boot up but only using GNOME Flashback (no effects)

---

### Post by ibjsb4 on 2013-08-10
Ok, thats good enough.  You should be able to pull up a terminal from there and change you session.  Im thinking that your session is mislabeled and just needs to be corrected.  Give it a try and see what happens next :)

[https://wiki.ubuntu.com/LightDM#Change_the_Default_Session](https://wiki.ubuntu.com/LightDM#Change_the_Default_Session)

---

### Post by toggles on 2014-02-06
I managed to fix this by doing the following:

```
gksudo gedit /usr/share/xsessions/ubuntu.desktop
``` 

Remove the --session=ubuntu from this line:

```
Exec=gnome-session --session=ubuntu
```

Cheers.

---

