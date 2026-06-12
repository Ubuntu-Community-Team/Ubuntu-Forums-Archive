---
title: "how to change default desktop from lxde to lubuntu"
date: 2011-09-27
forum: Desktop Environments
---

### Post by cedardoc on 2011-09-27
How can I change the default desktop from lxde to lubuntu in Lubuntu 10.10?  I've searched for this and can't seem to find a straight forward answer.  My computer boots up to the vanilla lxde desktop environment even when I shut down from the lubuntu environment.

thanks

---

### Post by garvinrick4 on 2011-09-27
At the login screen should give you a button to select what you want and should boot back
into that until you change it.

---

### Post by cedardoc on 2011-09-27
Yes its there, and its even preselected for Lubuntu when I log out to log back in (and it does  successfully re-log in to Lubuntu at that time) but the computer still boots up into the lxde environment every time I start up the computer regardless of what I do.

---

### Post by amjjawad on 2011-09-28
> **cedardoc said:**
> Yes its there, and its even preselected for Lubuntu when I log out to log back in (and it does  successfully re-log in to Lubuntu at that time) but the computer still boots up into the lxde environment every time I start up the computer regardless of what I do.

Hi,

Please correct me if I'm wrong.

1- You start up your machine
2- Your try to login to Lubuntu 10.10
3- No matter what session you select, your machine logs in always to LXDE Desktop.
4- You log out
5- Change the session (not rebooting) to Lubuntu
6- Log back in and you get Lubuntu Desktop
7- In case you reboot, you go back to step 3

Am I right?

---

### Post by cedardoc on 2011-09-29
not quite, I have it set to automatically log in to Lubuntu on startup.  It does automaticaly log in, but instead of Lubuntu it logs in to Lxde.

---

### Post by amjjawad on 2011-09-29
> **cedardoc said:**
> not quite, I have it set to automatically log in to Lubuntu on startup.  It does automaticaly log in, but instead of Lubuntu it logs in to Lxde.

If you haven't changed anything then by default, it should login to Lubuntu.

Honestly, I'm not sure how to fix this issue. I guess it has to do with lxdm but again, I'm not sure.

---

### Post by pixnaps on 2011-10-16
I've noticed the same problem (after converting my wife's netbook from ubuntu to lubuntu).  It looks like an old bug described [here]("https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/561377/") as allegedly "solved", so I'm not sure why we're still seeing this...

Any help would be much appreciated!

---

### Post by James Keating on 2011-11-13
I fixed this by editing /etc/xdg/lubuntu/lxdm/lxdm.conf. (The man page says it is /etc/lxdm/lxdm.conf for standard lxdm, /etc/xdg/lubuntu/lxdm/lxdm.conf for Lubuntu.)

The third section begins 
## default session or desktop used when no systemwide config

Change it to
session=/usr/bin/startlubuntu

Mine already said that, but I wanted to boot into FVWM. Changing it to session=/usr/bin/fvwm worked for me, so if yours doesn't already specify startlubuntu, I think it will work for you.

---

### Post by mikexgough on 2011-12-09
I changes my default set as Lubuntu to LXDE default by using the Alternatives Configurator If I remember I downloaded from synaptic#


under lxdm.conf you can amend... works for me

My Lubuntu is a family storage device/Print server from Windoze machines, so I have it on auto login..all they do is start up....then they can print etc as they please when I am not home

---

### Post by idef1x on 2012-01-04
> **James Keating said:**
> I fixed this by editing /etc/xdg/lubuntu/lxdm/lxdm.conf. (The man page says it is /etc/lxdm/lxdm.conf for standard lxdm, /etc/xdg/lubuntu/lxdm/lxdm.conf for Lubuntu.)

The third section begins 
## default session or desktop used when no systemwide config

Change it to
session=/usr/bin/startlubuntu

Mine already said that, but I wanted to boot into FVWM. Changing it to session=/usr/bin/fvwm worked for me, so if yours doesn't already specify startlubuntu, I think it will work for you.

Thanks! I was just looking for this and indeed the /etc/lxdm/lxdm.conf didn't do anything.
The /etc/xdg/lubuntu/lxdm/lxdm.conf did do the trick to start xbmc :)

---

