---
title: "How to change the log-in screen"
date: 2007-07-08
forum: Desktop Environments
---

### Post by alexv305 on 2007-07-08
I have Ubuntu Fiesty and I was wondering how to change the login. I recently installed beryl and its incredible runs smooth and barely affected my system performance on my AMD FX-55.

Also what is fluxbox, blackbox, fission, and what do they do? Same thing as beryl?

And how do I change the log-in screen where users log in? I dont like the Ubuntu presets that came with the OS.

Thanks.

---

### Post by Vajra Vrtti on 2007-07-08
> And how do I change the log-in screen where users log in?
*System -> Administration -> Login Window*, *Local* tab.
More themes at [gnome-look.org]("http://www.gnome-look.org/") (GDM themes).

---

### Post by ayoli on 2007-07-09
> **alexv305 said:**
> 

Also what is fluxbox, blackbox, fission, and what do they do? Same thing as beryl?



fluxbox and blackbox are window managers/desktop environement.
by fission, do you mean fusion ? compiz-fusion ? if yes it's the merge of compiz and beryl.

---

### Post by alexv305 on 2007-07-09
Yes I was talking about Fusion sorry.

How do i change the log-in splash screen? I downloaded a .png but how do I put it to show that as the splash screen on log-in? And what about the boot screen how do I change that?

Your help is appreciated.

Thanks,
Alex

---

### Post by Vajra Vrtti on 2007-07-09
> **alexv305 said:**
> How do i change the log-in splash screen? I downloaded a .png but how do I put it to show that as the splash screen on log-in?
As I told before:
> *System -> Administration -> Login Window, Local *tab.
Click the **Add** button.

> **alexv305 said:**
> And what about the boot screen how do I change that?
[ HowTo: theme your desktop]("http://ubuntuforums.org/showthread.php?t=203093")

---

### Post by ayoli on 2007-07-09
> **alexv305 said:**
> 
How do i change the log-in splash screen? I downloaded a .png but how do I put it to show that as the splash screen on log-in? 

if you mean the splash image just after login, these splash images are stored in /usr/pixmaps/splash
btw , you can change it also with gconf editor, hit ALT+F2 and type in:
```
gconf-editor
```
then find this key:
```
/apps/gnome-session/options/splash_image
```
and put the path of your custom splash.

---

### Post by princemanjee on 2007-07-16
Ok how do I change the login screen from a TTY Terminal... cant get into x because of some setting i changed when i WAS in X... a setting at the Login Change Dialog....  rebooted to see the effects and... no more X session.... HELP!!!

---

### Post by Vajra Vrtti on 2007-07-17
I can't help you, but I suggest you to report you problem in a new thread. Probably you won't get many people reading this old one. Describe clearly what you changed, where you changed it, and the error you're getting now.

---

### Post by princemanjee on 2007-07-18
I figured it out... i replaced my gdm.conf file with the factory default settings and I was able to get back into X jsut fine...  its a hassle though... thanks for your help any ways....


FYI
/etc/gdm/gdm.conf  replace with the factory default copy already in the folder ....

---

