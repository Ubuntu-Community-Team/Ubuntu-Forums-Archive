---
title: "LXDE under Ubuntu 8.04 - on start-up, &quot;Error: unable to connect to FAM"
date: 2008-09-23
forum: Desktop Environments
---

### Post by MatheoDJ on 2008-09-23
I recently installed ubuntu 8.04 on an old compaq Armada E500S. Unbearably slow, so I installed LXDE (this was my intention from the start). With no functional network manager, I installed Knetworkmanager via Add/Remove, which works fine except that there's no icon in the menu and it doesn't start up on login like it does under KDE... I tried putting a script in inid.d, tried adding it to etc/modules, nothing would get it to work on start up. I ended up finally taking the script from init.d and moving it to the desktop so that I can just double click it when I want to use the internets. Other than that it works just fine, with one small exception:

on start-up, I get the following error:

"Error: unable to establish connection with FAM
Do you have "FAM" or "Gamin" installed and running?"

fam is not installed, and when I looked at installing it via apt, it wanted to uninstall gamin, and with it the entire ubuntu desktop. Not my idea of fun.

I don't know if these two problems are interrelated or not, and I don't know how to fix either one. Neither are covered on the forum, at least from what I can tell from an hour or two searching via google. The only other weird thing about this computer is that I'm using a Dynex brand PCMCIA card for 801.11g wireless, and it comes up as a Broadcom on the restricted drivers program.works fine, though.

Thanks for your help!

---

### Post by ugm6hr on 2008-11-08
You could try Gnome's network manager - which definitely works with LXDE:
**[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession)** (see the section about Autostarting Apps)

Or LXDE's own NM: *sudo aptitude install lxnm*

I'm sure Wicd should work too.

---

### Post by MotleyPhule on 2008-12-28
I've been running 8.04 with LXDE. I've found WiCD to be really good.

I've also had that error message. I've found that if I ignore the FAM error message and just restart it, it will generally work fine.

I know that's not terribly helpful :|

---

### Post by h4mx0r on 2009-01-15
Ubuntu compiles FAM a bit differently than usual and also installs portmap as dependency. Perhaps you should try gamin, xubuntu uses that by default and its rather light weight.

---

### Post by juggarnatha on 2009-11-06
Hmm. I'm kind of a newbie here, but I've been having this problem for a while. I would reboot or just ignore the problem in the past, and it would go away but this morning it irritated me so I found this thread. 

Before trying anything that was suggested here, I poked around . . .

In addition to the error message, I notice that my wallpaper and desktop do not present themselves at all, and the GUI doesn't seem to work the same. When I right click on the desktop, I get a black menu with LXDE at the top and just a few unfamiliar options. One of these was "Reload Config Files" . . . I tried that and a few seconds later my desktop icons and wallpaper reappeared, as well as "normal" right-click-on-desktop behavior. 

Anyone have any idea what this may mean? I would like to know how to have accomplished this in a terminal as well, just to know what is happening under the hood. 

Also, what would FAM or Gamin have to do with config files and the desktop / wallpaper not loading? 

Thanks, O guru.

---

### Post by n2stc on 2010-03-27
> **juggarnatha said:**
> 
In addition to the error message, I notice that my wallpaper and desktop do not present themselves at all, and the GUI doesn't seem to work the same. When I right click on the desktop, I get a black menu with LXDE at the top and just a few unfamiliar options. One of these was "Reload Config Files" . . . I tried that and a few seconds later my desktop icons and wallpaper reappeared, as well as "normal" right-click-on-desktop behavior. 
......
Also, what would FAM or Gamin have to do with config files and the desktop / wallpaper not loading? 

Thanks, O guru.

I have the same symptoms. There's no need to reboot.  I have PCMANFM in the quick launch tool bar.  One click on that restores normal operation.  It does seem to be tied to the network manager, as it happens more frequently now that I have gone to a higher security level.  I am afraid to change though, since it took so long to get wireless working on this thing in the first place.

---

