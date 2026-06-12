---
title: "Help Please! I appear to have completely distroyed my computer setup and can't logon."
date: 2007-12-29
forum: Dell  Ubuntu Support
---

### Post by crazyfish666 on 2007-12-29
Ok, so I have been having a lot of sound trouble lately, and decided to fix it once and for all as it all started with some changes I made to the alsa drivers. I went into synaptic and uninstalled alsa-base, alsa-utils, gnome-alsamixer, lib64asound2, libpt-plugings-alsa and linux sound base and as a result had to uninstall ubuntu-minimal, fast-user-switch-applet, gdm, ubuntu-desktop and ekiga as they were dependant. This I figure would be ok as I would reinstall them before rebooting. I went to [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") site and followed the instructions to reinstall alsa up to where it said 'reboot' being an idiot I did just that forgetting that I had planned on reinstalling all the necesary packages before rebooting. Now I am stuck, I cannot figure out how to log onto my computer to reinstall everything. When I power up I get a screen similar to one big version of terminal which says 

> 
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/cee693df-e84a-4bda-9231-53902901a2c7) = sda6(8,6)
kinit: trying to resume from /dev/disk/by-uuid/cee693df-e84a-4bda-9231-53902901a2c7
kinit: No resume image, doing normal boot...

Ubuntu 7.10 artemis tty1

artemis login:


At which I type in my login and password and get 

> 
artemis login: fae
Password:
Last login: Sat Dec 29 20:43:54 EST 2007 on tty1
Linus artemis 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubunto comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
fae@artemis:~$


From here I am pretty sure I can install all I need to get Ubuntu to boot up properly but when I put in 

> 
fae@artemis:~$ Install ubuntu-minmal


I get

> 
install: missing destination file operand after 'ubuntu-minimal'
Try 'install --help' for more information.


so I put in

> 
fae@artemis:~$ Install ubuntu-minmal ~/downloads


and get

> 
install: cannot stat 'ubuntu-minimal': No such file or directory


beyond that I have no idea what to do, I am rather a newbie! Any help would be appreciated and if it were as idiot proof as possible that would be even better :) .

---

### Post by dasunst3r on 2007-12-29
The command to install stuff is *apt-get install* (you're missing the apt-get portion), so if you wish to reinstall the Ubuntu desktop, you would want to issue the command *sudo apt-get install ubuntu-desktop*.

---

### Post by crazyfish666 on 2007-12-29
> **dasunst3r said:**
> The command to install stuff is *apt-get install* (you're missing the apt-get portion), so if you wish to reinstall the Ubuntu desktop, you would want to issue the command *sudo apt-get install ubuntu-desktop*.

Ok, I have done that for everything I uninstalled, but I still get the same stuff come up when I power up. What would y'all recommend?

---

### Post by crazyfish666 on 2007-12-31
> **crazyfish666 said:**
> Ok, I have done that for everything I uninstalled, but I still get the same stuff come up when I power up. What would y'all recommend?

Is there a command that would power me back up into visual mode as opposed to terminal?

---

### Post by Sef on 2007-12-31
> Is there a command that would power me back up into visual mode as opposed to terminal?

startx.   If you get to a command prompt, type in startx.  That is the command to start the GUI.

---

### Post by crazyfish666 on 2008-01-02
> **Sef said:**
> startx.   If you get to a command prompt, type in startx.  That is the command to start the GUI.

OK, I did that and all I got was a black screen. It flashed up some text that dissapeared too fast for me to read and gave me a black screen. I have reinstalled all the missing packages using 'apt-get install' but I seem to still be missing something that will allow it to start the GUI, do I need to do something to build the installed packages? And if so what?

---

### Post by melvis02 on 2008-01-02
This is just a stab in the dark, but it could be that GDM (Gnome Display Manager) isn't started.  try:

```
sudo /etc/init.d/gdm start
```

If it says that GDM is already started, then you'll know I'm wrong :) but you might as well try doing 

```
sudo /etc/init.d/gdm restart 
```

to see if that works.

---

### Post by crazyfish666 on 2008-01-03
> **melvis02 said:**
> This is just a stab in the dark, but it could be that GDM (Gnome Display Manager) isn't started.  try:

```
sudo /etc/init.d/gdm start
```

If it says that GDM is already started, then you'll know I'm wrong :) but you might as well try doing 

```
sudo /etc/init.d/gdm restart 
```

to see if that works.

Oh thank you thank you thank you!!! It is working!! :D I had no idea how hard it would be to live without computer access and now I know! Thanks again!

---

