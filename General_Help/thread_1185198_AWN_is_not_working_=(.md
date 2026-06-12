---
title: "AWN is not working =("
date: 2009-06-12
forum: General Help
---

### Post by KEE on 2009-06-12
:popcorn: AWn from system package manager isnt working or its not starting up please help =) oh yeah ~interped

---

### Post by ramjet_1953 on 2009-06-12
Are you also running Compiz Fusion?
AWN will not run without Compiz.
This also means that you need to have the appropriate driver loaded for your video card.

Regards,
Roger :)

---

### Post by KEE on 2009-06-13
> **ramjet_1953 said:**
> Are you also running Compiz Fusion?
AWN will not run without Compiz.
This also means that you need to have the appropriate driver loaded for your video card.

Regards,
Roger :)

ccsm is installed and it still wont show up =( was working before =S

---

### Post by synapsys on 2009-06-13
What happens when you run:

```
avant-window-navigator &
```

from terminal?

---

### Post by KEE on 2009-06-13
how would you configure the drivers? its not in the system's drop menu =S   there is a system/administration/hardware drivers drop menu but when i click it its blank and says there is no drivers available =S

---

### Post by KEE on 2009-06-13
> **synapsys said:**
> What happens when you run:

```
avant-window-navigator &
```

from terminal?

LOL that worked but it doesnt stay after i close the terminal...is this a new set up?

---

### Post by synapsys on 2009-06-13
```
sudo apt-get install ubuntu-restricted-extras
```are you sure you put the '&' at the end..... this tells it to run in the background so you can close the terminal.......

if you can start using this command, go into preferences and tell it to 'start with system'

---

### Post by raymondh on 2009-06-13
> **KEE said:**
> ccsm is installed and it still wont show up =( was working before =S

Hello KEE,


Try these various checks;

-RT Click on your desktop > change desktop appearance > visual effects.  See if you have Normal or Extra set.  If you have NONE and have tried to set Normal or Extra but cannot, see if you need to re-enable hardware drivers (system > administration)

-Alt + F2 and type compiz or AWN to bring either up

-Check your preferences and see if AWN is set to start-up

Also, here is the link for AWN and Forlong's blog on compiz (which may give you some tips)

[http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)
[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

I hope these help. If not, post back and we'll try to troubleshoot from there :)

Regards,

---

### Post by KEE on 2009-06-13
its working but terminal needs to be left on. if I close it so does AWN. hmm the AWN i have doesnt have a startup option. lol a different version ok what version works because this AWN is  just from synaptic package manager```
me@me-desktop:~$ avant-window-navigator &
[1] 6336
me@me-desktop:~$ Screen is composited.
LOADED : /usr/share/applications/awn-manager.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/share/awn/applets/trash.desktop

```

---

### Post by KEE on 2009-06-13
I dont know anymore, I have nothing under system>administration>hardware Drivers it says "no proprietary drivers are in use on this system" just seems that my version of Linux (intrepid) I have got broke =S that wiki doesnt really help either because of the steps dont work.

It might the version of AWN i tried to install before [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

if this is a problem then it should be removed form the database because it causes problems. I cant launch the uninstall ```
me@me-desktop:~$ sudo apt-get remove --purge avant-window-navigator-bzr awn-manager-bzr awn-core-applets-bzr libawn0-bzr
[sudo] password for me: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@me-desktop:~$ 

```

---

### Post by synapsys on 2009-06-13
Close synaptic before you run that command. If synaptic isn't open reboot and run again.

I've heard a lot of people are having problems with AWN. I've also heard a lot of good things about Gnome-do....maybe try that? If you MUST have a dock (i think they're ugly)

---

### Post by KEE on 2009-06-13
> **synapsys said:**
> Close synaptic before you run that command. If synaptic isn't open reboot and run again.

I've heard a lot of people are having problems with AWN. I've also heard a lot of good things about Gnome-do....maybe try that? If you MUST have a dock (i think they're ugly)

you know where a working version can be found? yeah i did remove it for a little while but then I want it again and now I found that I have a mess

---

### Post by KEE on 2009-06-13
OK i got AWN running. I tried Gnome do But i didnt like the functionality as too AWN or what AWN use to be.  so AWN is running but adding the apps to the Launcher is not responding somewhat or ubuntu is not functioning well with it. ill have to read more about this but any problems ill come back here =)

---

### Post by KEE on 2009-06-16
Ok one problem, I m not able to add to the dock =S drag doesnt work and entering the execute command (like in ALT+F2) in AWN Manager>launcher Preferences tab doesnt work either. please help =( and thank you

---

### Post by KEE on 2009-06-16
lol nvm I got working i was missing the AWN manager on the dock XD all is good hanks all =)

---

