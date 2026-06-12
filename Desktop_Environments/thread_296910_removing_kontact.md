---
title: "removing kontact"
date: 2006-11-10
forum: Desktop Environments
---

### Post by feest on 2006-11-10
Hi, i've installed 'kubuntu-desktop' over ubuntu because i wanted to check out kde howerver i dont want to use all the mail clients (i only need one) irc (i dont irc) book collectors (i don't read) music collectors (i use mp3's) movie collections (i dont make a movie database) bluetooth chat programs (even if my pc had a bluetooth device i wouldn't like to use it)

well you got the point.

I CAN SAVE A LOT OF DISK SPACE BY REMOVING UNNECCESAIRY APPS

however since all these apps are part of the K Desktop Environment (KDE) i don't know if this will damage my kde installation or even X. i can remember (a long time ago when i was still running windows 3.1) i thought i didn't need ms exel so i removed it, it cause entire office suit to crash (yeah yeah i know it microsoft but still i thought why...) so can i remove safely kde apps without removing kde or performing system crashes or other failures?

---

### Post by an.echte.trilingue on 2006-11-10
The function that kubuntu-desktop serves is to depend on all the elements of the desktop environment so that you can install KDE in one click.  You can remove it safely.

The advantage of the apt package manager (synaptic and aptitude are a GUIs for apt) is that if a package needs something to work right, apt will install it for you automagically.  So, you can remove as much as you want.  If you remove something that, say, OpenOffice depends on, syaptic will warn you if and then uninstall openoffice rather than leaving it broken.  Then, you can reinstall OpenOffice and apt will install its dependancies for you.  Cool, huh?

By the way, adept is less good at warning you about things it is going to remove: be sure to check that specifically before hitting the apply button.

Take care,

mat

Edit:  Still, don't get too click happy about removing stuff:  if you have no idea what something does, it probably does something important.

---

### Post by feest on 2006-11-10
well i'm not a complete linux newb so i know enough to know what i'm doing (however i would'nt say i'm a pro or something) i don't use adept because i can run synaptic from my gnome installation (i don't like adept :P) but nice to know that i can 'drop a flop' what's not neccesary so i can remove all that useless book collectors bluetooth thentists etc.

thx :)

---

### Post by TheWizzard on 2006-11-10
> **feest said:**
> well i'm not a complete linux newb so i know enough to know what i'm doing (however i would'nt say i'm a pro or something) i don't use adept because i can run synaptic from my gnome installation (i don't like adept :P) but nice to know that i can 'drop a flop' what's not neccesary so i can remove all that useless book collectors bluetooth thentists etc.

thx :)

the way linux is build allows you to remove packages if other packages do not depend on that particular package. 

if you start uninstalling packages, you may leave a lot of unused packages because they were dependencies. (if you used aptitude you won't have this problem).

you can find and unistall unused packages with gtkorphan

---

