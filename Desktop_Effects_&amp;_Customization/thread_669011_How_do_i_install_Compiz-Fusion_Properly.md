---
title: "How do i install Compiz-Fusion Properly?"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by Reswel on 2008-01-16
I have tried to install Compiz-Fusion countless amounts of times. All that i receive in the end is a screwy computer that won't even load any more. I'm going to wipe all data from the computer and try to reinstall Compiz-Fusion. Please help me with this new install that i'm perhaps not going to install correctly again. I tried just about every website's instructions with no luck whatsoever.:confused::frown::-({|=

Distribution: Ubuntu 7.10
CPU: Genuine Intel(R) CPU  T2060  @ 1.60GHz
Memory: 1382 MB
Graphics Card: ATI Radeon Xpress 200M Series.
Experience With Windows: 15 Years
Experience With Ubuntu: Complete Newb With A Decent Understanding How Everything Works In Linux.
Luck: None

I thank you folks for helping me out, and thank you for letting me be a part of this magnificent forum.:guitar:

---

### Post by meindian523 on 2008-01-16
C-F comes preinstalled with Gutsy,you just need to install the fglrx drivers from Restricted Drivers Manager and Xgl.

```
sudo apt-get install xserver-xgl
```

and put these scripts:
1]startxgl.sh
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session


```
in /usr/local/bin/

and 
2]xgl.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```
in /usr/share/xsessions/

Make both of them executable with 

```
sudo chmod a+x <respective_filename>
```

trust me,I've got the same card and am enjoying Compiz-Fusion without any problems.

---

### Post by xfearxnxloathing on 2008-01-16
real quick and real easy!

first if you're using gutsy which is very stable go, System>Administration>Synaptic Package Manager.  next, click search and type compiz fusion and hit enter.  it will now bring up several compiz fusion packages, select the ones you want and mark for install.  all that's left is ctrl+alt+backspace and log back in.

you should now see under System>Preferences :  Advanced Desktop Effects Settings.  click that and there you have the CompizConfig Settings Manager. =]

do make sure you have the right driver for your graphics card and that under System>Preferences>Appearence, that custom is now an option and is selected.

hope this helps!

ps "once you get it to work i reccomend: http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"

---

### Post by Reswel on 2008-01-17
xfearxnxloathing, Emerald started working correctly, but there is an issue with compiz. In the image i provided, "CompizConfig Settings Manager" Appears but there is no feedback when i click on it. It's like it never happened in the first place. meindian523 I couldn't find those files under the locations you gave me. So i made them from an empty document and inserted the data inside of them. I tryed to place them under their locations with a message claiming that i could not move/create files there. Now what guys, i have enabled "Visual Effects" to extra. In the image i provided, i only have compiz manager and the files meindian523 told me to move there.

---

### Post by Espreon on 2008-01-17
Creating a separate XGL session is no longer necessary, when you install XGL in Gutsy XGL gets started up with all sessions...

---

### Post by meindian523 on 2008-01-17
> **Reswel said:**
> xfearxnxloathing, Emerald started working correctly, but there is an issue with compiz. In the image i provided, "CompizConfig Settings Manager" Appears but there is no feedback when i click on it. It's like it never happened in the first place. meindian523 I couldn't find those files under the locations you gave me. So i made them from an empty document and inserted the data inside of them. I tryed to place them under their locations with a message claiming that i could not move/create files there. Now what guys, i have enabled "Visual Effects" to extra. In the image i provided, i only have compiz manager and the files meindian523 told me to move there.

You ARE supposed to make them anew.To place them you need to have root privileges,attained by using sudo.

---

### Post by Reswel on 2008-01-18
> **meindian523 said:**
> You ARE supposed to make them anew.To place them you need to have root privileges,attained by using sudo.

Please explain how. (Thank you guys for bearing with me)

---

### Post by meindian523 on 2008-01-18
Basically,you did it correctly but you have to just move those files into the locations I gave you.But,according to Espreon,those files are not required("Creating a separate XGL session is no longer necessary, when you install XGL in Gutsy XGL gets started up with all sessions..."),so just ignore those files for the present and retry enabling advanced desktop effects.

---

### Post by xfearxnxloathing on 2008-01-18
> **Reswel said:**
> xfearxnxloathing, Emerald started working correctly, but there is an issue with compiz. In the image i provided, "CompizConfig Settings Manager" Appears but there is no feedback when i click on it. It's like it never happened in the first place. meindian523 I couldn't find those files under the locations you gave me. So i made them from an empty document and inserted the data inside of them. I tryed to place them under their locations with a message claiming that i could not move/create files there. Now what guys, i have enabled "Visual Effects" to extra. In the image i provided, i only have compiz manager and the files meindian523 told me to move there.


forgot that if you previously had it installed when it bugged out that you need to go into the Synaptic Package Manager and do the search for compiz and remove (uninstall) those packages.  the packages for compiz fusion you already have installed that are rightnow "bugged or broken" are already shown with a green box.  re-mark them for removal (will now show red box).  next, hit Ctrl+Alt+Backspace to log out and then sign back in.  now follow my original instructions and everything should be good.

> System>Administration>Synaptic Package Manager. next, click search and type compiz fusion and hit enter. it will now bring up several compiz fusion packages, select the ones you want and mark for install. all that's left is ctrl+alt+backspace and log back in.

you should now see under System>Preferences : Advanced Desktop Effects Settings. click that and there you have the CompizConfig Settings Manager. =]

notice after the log back in, before reinstalling that "Advanced Desktop Effects Settings" no longer appears (this means you've successfully uninstalled those packages).  with the final logout/login session your "Advanced Desktop Effects Settings" shall now be clickable.

---

### Post by giok13 on 2008-01-18
did u by any chance first install compiz with git. cause tht is wat causes the problems. wen i looked at the screenshot, instead of the thing saying advanced desktop effect settings it said compiz manager. i kept having the same problem like tht after installing with git. and since git isnt connected with synaptic and it installs files almost everywere u cant uninstall it. so if u did install with git u need to reformat ubuntu ( not sure how) but wat i did was reinstall ubuntu and just went into synaptic and installed from thr and everything works fine now.

---

