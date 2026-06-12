---
title: "GDM boot problem"
date: 2005-12-21
forum: Desktop Environments
---

### Post by meenfreem on 2005-12-21
I'm totally new when it comes to linux, so here is my runlevel question.

It seems that during a install of a program, my runlevel has been changed, and now it won't start up x automaticly during start-up. I have to login through terminal and startx by hand... how do I change this back so that x starts automaticly again?

As far as I can see, I am still in runlevel 2 (intitab file says so anyways), so I think I have somehow disabled my GDM. 

After running BUM... it seems that GDM is activated (as it does during start up too, it shows the ubuntu logo and all the texts etc), but just before the login screen should come, it switches back to terminal. In BUM-Summary, GDM shows with a red light next to it, this should be green?

I get the feeling that GDM is killed sometime during the boot up, or my rcS file has somehow been altered to not start gdm at all. I'm very confused, but I don't want (read: dare) to muck about with the system too much because everything works fine, besides this minor boot problem.

Thanks

---

### Post by codejunkie on 2005-12-21
[QUOTE=meenfreem]I'm totally new when it comes to linux, so here is my runlevel question.

It seems that during a install of a program, my runlevel has been changed, and now it won't start up x automaticly during start-up. I have to login through terminal and startx by hand... how do I change this back so that x starts automaticly again?

As far as I can see, I am still in runlevel 2 (intitab file says so anyways), so I think I have somehow disabled my GDM. 

After running BUM... it seems that GDM is activated (as it does during start up too, it shows the ubuntu logo and all the texts etc), but just before the login screen should come, it switches back to terminal. In BUM-Summary, GDM shows with a red light next to it, this should be green?

I get the feeling that GDM is killed sometime during the boot up, or my rcS file has somehow been altered to not start gdm at all. I'm very confused, but I don't want (read: dare) to muck about with the system too much because everything works fine, besides this minor boot problem.

Thanks[/QUOTE]
try running 
```
sudo update-rc.d -f gdm remove
```
and then 
```
sudo update-rc.d -f gdm defaults
```
from a terminal
the first one will remove the current system startup links for gdm
and the second one will set them to there default values hopefuly this will fix it.

---

### Post by meenfreem on 2005-12-21
thanks, I'll post the results here... need to do some actual work first though!

---

### Post by meenfreem on 2005-12-21
problem remains :(

could it be that something kills the gdm?

---

### Post by codejunkie on 2005-12-21
[QUOTE=meenfreem]problem remains :(

could it be that something kills the gdm?[/QUOTE]
i don't really know for sure, maybe something damaged the gdm package try reinstalling gdm through synaptic or with 
```
sudo apt-get install --reinstall gdm
```
and reboot or press ctrl+alt+F1 and entering
```
sudo /etc/init.d/gdm stop
```
then
```
sudo /etc/init.d/gdm restart
```
to restart gdm.

---

### Post by meenfreem on 2005-12-21
thanks again, I'll give it a go and report back after lunch

---

### Post by meenfreem on 2005-12-21
Everything back on track again! 

Turns out that GDM got uninstalled at some point?! How is that possible though?! This stuff happened after I tried to install the owl ftp program, which went pearshaped for some reason... 

So after reinstalling GDM, everything is working perfectly again! 

Thanks for the help.

---

### Post by codejunkie on 2005-12-21
[QUOTE=meenfreem]Everything back on track again! 

Turns out that GDM got uninstalled at some point?! How is that possible though?! This stuff happened after I tried to install the owl ftp program, which went pearshaped for some reason... 

So after reinstalling GDM, everything is working perfectly again! 

Thanks for the help.[/QUOTE]
glad to help.

---

### Post by meenfreem on 2005-12-21
more GDM problems!

My colleague runsw the same system as I do, but his display gets bugged a few times a day. We both have a nVidia graphics card. I don't have the problem anymore since I managed to install the latest nvidia driver. But when he tried to install that driver, he ended up having to reinstall ubuntu entirely (hey, we're noobs). Now I had this idea that it might be GDM which triggers this bug in ubuntu?

any off the wall ideas what the problem could be or how to fix it safely (with out running the risk of having to reinstall again).

---

### Post by codejunkie on 2005-12-21
[QUOTE=meenfreem]more GDM problems!

My colleague runsw the same system as I do, but his display gets bugged a few times a day. We both have a nVidia graphics card. I don't have the problem anymore since I managed to install the latest nvidia driver. But when he tried to install that driver, he ended up having to reinstall ubuntu entirely (hey, we're noobs). Now I had this idea that it might be GDM which triggers this bug in ubuntu?

any off the wall ideas what the problem could be or how to fix it safely (with out running the risk of having to reinstall again).[/QUOTE]
i doubt that gdm is the main cause of his problems, but exactly what do you mean by it gets bugged, it won't start, or gdm dies it freezes? a little more info would help.

---

### Post by meenfreem on 2005-12-21
the computer doesn't freeze, but the colour go absolutely haywire. Like a snowscreen on a tv but then in colour and with vertical coloms. The way he gets around it now is to log-out and log-in again. Which resets whatever it is that freaks out. Seems to only happen while browsing the internet and/or while there are images displayed (gimp or firefox).

as I said, I had the same problem, but after installing the nvidia drivers, the problem disappeared. We do have a 'brand new' card N6600 DeLuxe so it might be just that 5.10 is not uptodate with that specific card. 

We're going to try this [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) this afternoon and see if that soves it.

Ubuntu is really great though :D We're very happy with it (as complete noobs we managed everything, except for this problem)

---

### Post by codejunkie on 2005-12-21
[QUOTE=meenfreem]the computer doesn't freeze, but the colour go absolutely haywire. Like a snowscreen on a tv but then in colour and with vertical coloms. The way he gets around it now is to log-out and log-in again. Which resets whatever it is that freaks out. Seems to only happen while browsing the internet and/or while there are images displayed (gimp or firefox).

as I said, I had the same problem, but after installing the nvidia drivers, the problem disappeared. We do have a 'brand new' card N6600 DeLuxe so it might be just that 5.10 is not uptodate with that specific card. 

We're going to try this [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) this afternoon and see if that soves it.

Ubuntu is really great though :D We're very happy with it (as complete noobs we managed everything, except for this problem)[/QUOTE]
[INDENT]It's the video card, not gdm. just make sure before you install the offical nvidia driver you open synaptic click on search and enter nvidia in the search field and completely remove all nvidia packages listed, because they can conflict with the offical nvidia driver. everything except for this package **[COLOR="Red"]xserver-xorg-driver-nv[/COLOR]** do not remove this package it will remove the xserver.
and that guide is kind of out dated you'll have better luck following this guide if your using breezy [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074) hope this helps and if you need any help let me know and i'll try my best.[/INDENT]

---

