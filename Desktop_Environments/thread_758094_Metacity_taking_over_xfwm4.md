---
title: "Metacity taking over xfwm4"
date: 2008-04-17
forum: Desktop Environments
---

### Post by ultranoize on 2008-04-17
Hi I'm trying to run on XFCE but metacity is loaded instead  of xfwm4.  Any suggestions on how to solve this??  I've tried to remove xubuntu-desktop and all the packages related to xfce. No luck there either...

---

### Post by Triggerhapp on 2008-04-17
Do you use Metacity at all?

---

### Post by Triggerhapp on 2008-04-17
Do not use this if:
1) You use Gnome/metacity elsewhere
2) You are unsure what the commands do

```

sudo mv /usr/bin/metacity /usr/bin/metacity.bk
sudo ln -s /usr/bin/xfwm4 /usr/bin/metacity

```

This makes any calls to "metacity" actually call xfwm4, although this may need repeating if you update metacity, and there is likely a better way, I just dont know better :P

---

### Post by ultranoize on 2008-04-18
I do use Metacity once in a while, so I don't think this is a good solution..Thanks anyway....

---

### Post by kpkeerthi on 2008-04-18
> **ultranoize said:**
> Hi I'm trying to run on XFCE but metacity is loaded instead  of xfwm4.  Any suggestions on how to solve this??  I've tried to remove xubuntu-desktop and all the packages related to xfce. No luck there either...

In a XFCE session, open a terminal and run this command ```
xfwm4
``` 

XFCE's default window manager should automatically work next time you reboot.

---

### Post by ultranoize on 2008-04-18
This is what I get:

** (xfwm4:29469): WARNING **: Another Window Manager is already running

---

### Post by Triggerhapp on 2008-04-18
```
killall metacity && xfwm4 &
``` Do that in an alt-f2 dialog, not a terminal :) if you close the terminal with an x then it will close xfwm4 too

---

### Post by Tomatz on 2008-04-18
There is an option in the xfce settings somewhere to use nautilus instead of thunar. I think this is your problem. ;)

---

### Post by ultranoize on 2008-04-18
Yes I have by default nautilus as file manager. But I have no idea where to go to change it to Thunar.

---

### Post by Tomatz on 2008-04-18
> **ultranoize said:**
> Yes I have by default nautilus as file manager. But I have no idea where to go to change it to Thunar.

Funny question but is thunar installed?

---

### Post by ultranoize on 2008-04-18
Yes I have Thunar 0.8.0

---

### Post by Tomatz on 2008-04-18
Got kind of a workaround.

Download this and install it:

[http://ubuntuforums.org/showpost.php?p=3163821&postcount=8](http://ubuntuforums.org/showpost.php?p=3163821&postcount=8)

Then add the command **fusion-icon** To (menu) *system, preferences, sessions, startup*.

logout then login

Now you will have a systray applet that will allow you to switch between compiz, metecity and more importantly **XFWM4**

Hope that helps ;)

---

### Post by ultranoize on 2008-04-19
```
killall metacity && xfwm4
```

did work. But the machine hangs after a  while. This has never happened before. The question  is how do I find out what is making the machine hang?  There must be some log file somewhere right ??

---

### Post by Tomatz on 2008-04-19
Have never tried it but the following might work.

```
xfwm4 --replace
```

---

### Post by Triggerhapp on 2008-04-19
> **Tomatz said:**
> Have never tried it but the following might work.

```
xfwm4 --replace
```

xfwm4 doesnt replace. Its the only one i know of that doesnt :P

---

### Post by Tomatz on 2008-04-19
> **Triggerhapp said:**
> xfwm4 doesnt replace. Its the only one i know of that doesnt :P

Crud :(

Fusion-icon would be his best bet then. It works fine on my eeepc/xubuntu. I can switch between xfwm4, metacity and compiz fine with it.

By the sounds of it it could be a problem with the xfce startup scripts.

---

