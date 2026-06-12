---
title: "gnome won't boot"
date: 2005-05-18
forum: Desktop Environments
---

### Post by simple on 2005-05-18
well ubuntu was fine until i installed the kernel headers and then alsa and configured alsa, now after a reboot it would boot to the command prompt and not gnome desktop, i could login as my user accout..but can't get a graphical gnome running, all i did were those two things i've mentioned, any ideas how to get it back?

---

### Post by dave9191 on 2005-05-18
If you had gnome working b4 and now it stopped, try logging into the command line and typing startx as the command. 

Dave

---

### Post by simple on 2005-05-18
[QUOTE=dave9191]If you had gnome working b4 and now it stopped, try logging into the command line and typing startx as the command. 

Dave[/QUOTE]
 that did something, that started up the screen that's blank and greycrisscross with an X as the cursor and freezes there, i can't restart, i can wait 20 minutes nothing happens, i need to hit the power button it beeps...i don't know what happened :/ i didn't do anything...so weird

---

### Post by d-n-r on 2005-05-18
hi simple,

is the right session type selected in the login screen? unlikely i know but possible.  :) 

d-n-r

---

### Post by simple on 2005-05-18
[QUOTE=d-n-r]hi simple,

is the right session type selected in the login screen? unlikely i know but possible.  :) 

d-n-r[/QUOTE]there is no login screen, just starts up and boots right to the command prompt then "simplelogin@$" or whatever, simple mypass then simple@root$: is my ubuntu x:

> Starting powernowd
CPU Frequency scaling not supported
Starting anac(h)conistic cron: anacron
Starting deferred execution scheduler
Starting periodic command scheduler

uh the last five lines when ubuntu is booting up

---

### Post by compmodder26 on 2005-05-18
[QUOTE=simple]that did something, that started up the screen that's blank and greycrisscross with an X as the cursor and freezes there, i can't restart, i can wait 20 minutes nothing happens, i need to hit the power button it beeps...i don't know what happened :/ i didn't do anything...so weird[/QUOTE]

Sounds like an X Server config issue.  Try running xorgconfig or manually editing your xorg.conf file.  Both are simple enough.  But I would recommend you making a backup of your xorg.conf before trying either one.

---

### Post by simple on 2005-05-18
[QUOTE=compmodder26]Sounds like an X Server config issue.  Try running xorgconfig or manually editing your xorg.conf file.  Both are simple enough.  But I would recommend you making a backup of your xorg.conf before trying either one.[/QUOTE]didn't work

---

### Post by simple on 2005-05-18
well i just reinstalled ubuntu, and i'm saying the problem i had was installing the headers, so which one will i want to install witht his output?
> root@ubuntu:/home/simple # uname -a
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux


---

### Post by tpischke on 2005-08-21
Having exactly the same problem after uninstalling and reinstalling alsa-base via apt-get.  

I get the terminal login and nothing more.  If I log in and type 'gdm', the command isn't recognized.  startx brings up a blank desktop screen, but that doesn't help much.

I suspect this problem is related to alsa, but reinstalling alsa and restoring my backup conf files didn't help.

Did you ever solve your problem?

---

