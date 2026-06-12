---
title: "HELP me please.. im freaking out over here!!!"
date: 2009-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amanda729 on 2009-07-24
Okay yesterday i was messing around trying to download the extras so i could hear music on myspace well i did it all and then i found a video on you tube on how to actually do it right soo i followed the instructions and he had me delete some files.. and clean up thru the terminal... well i did it.. and i restarted the computer.. now there is no desktop!!!! no icons no nothing just a screen with a background! i dont know what to do please help!!!!! i tried starting it with the command line by pressing esc when booting and the command line came up and didnt recognize anything i kept getting error 27. This was my first time using the computer it came with ubuntu on it.. its a dell mini..
 
SOMEONE HELP!!!! please!!!:confused:

---

### Post by bacil on 2009-07-24
can you press Ctrl+Alt+F1 while you see your background ?
log in to console.

ad first try to restart your desktopmanager

gnome
```
 sudo /etc/init.d/gdm restart
```
kde
```
sudo /etc/init.d/kdm restart
```
then i guess you need to look to logfiles for error messages

---

### Post by amanda729 on 2009-07-24
nothing happens when i press those keys

---

### Post by philcamlin on 2009-07-24
well it looks like you did a number on your pc

id boot into the live cd backup and reinstall...

sorry :(

---

### Post by bacil on 2009-07-24
> **amanda729 said:**
> nothing happens when i press those keys

oops, can you try any athor Fkeys (except F7) it should let you go to console

---

### Post by amanda729 on 2009-07-24
well we were supposed to be sending it in today to get it looked at because we have replaced the battery twice nd still get no power unless plugged into the wall. and the battery and power light are continuously flashing... maybe they can fix it... its under warranty

---

### Post by amanda729 on 2009-07-24
ctrl alt F9 sends me to login page but once i put in password and hit enter nothing happens
 
and if i click switch user it says input user name and sends me to an ubuntu page with an options tab in the corner

---

### Post by amanda729 on 2009-07-24
is there any way i fould possibly down load the files to make it better or something.... or fix it thru the terminal..

---

### Post by sammyboy405 on 2009-07-25
> **amanda729 said:**
> nothing happens when i press those keys

She is on a Mini so she will need to do

CTRL+ALT+FN+F1


When using Fkeys on the Mini you need to use the FN key else default are the multimedia Functions.

---

