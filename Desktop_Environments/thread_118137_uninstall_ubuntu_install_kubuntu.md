---
title: "uninstall ubuntu install kubuntu"
date: 2006-01-16
forum: Desktop Environments
---

### Post by Hotchilli on 2006-01-16
kubuntu-5.10-install-i386 released on 14/12/2005

Because of a small problem ongoing for a month now with
synapic and apt-get no working please tell how to uninstall
unbuntu and install kubuntu

if you need to my problem threds here they 

[http://www.ubuntuforums.org/showthread.php?t=108603](http://www.ubuntuforums.org/showthread.php?t=108603)

hc:smile: :smile:

---

### Post by Sef on 2006-01-16
> install kubuntu

from the terminal:  sudo apt-get install kubuntu-desktop

> uninstall unbuntu

from the terminal: sudo apt-get remove --purge ubuntu-desktop

From a post by Aysiu: > As you may or may not know, if you install the package called kubuntu-desktop, a lot of other packages will be installed so that you get the full KDE experience in addition to Gnome.

If, however, you uninstall kubuntu-desktop, none of the other "full KDE experience" packages will be uninstalled. You may have installed kubuntu-desktop to get the KDE experience but then found it cluttered things up too much.

Link to post:  [http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+terminal]("http://ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+terminal")

Note: Same situation would exist with Ubuntu leaving meta-packages on Kubuntu's desktop.

---

### Post by Hotchilli on 2006-01-16
thanks for post but if you read my thread apt-get is not working

hc:smile: :smile:

---

### Post by w2vy on 2006-01-16
What is the difference between ubuntu and kbuntu?

(yeah I know 'k' :)

seriously...

---

### Post by Hotchilli on 2006-01-16
bright colour for one.
if thats what you prefer but lots more I hope:smile: :smile: 
hc

---

### Post by JAwuku on 2006-01-16
[QUOTE=w2vy]What is the difference between ubuntu and kbuntu?

(yeah I know 'k' :)

seriously...[/QUOTE]

Ubuntu and kubuntu have essentially the same base system, but Ubuntu uses Gnome and Kubuntu uses KDE.

---

### Post by mips on 2006-01-17
Backup your data and install from scratch deleting your existing ubuntu partitions and creating new ones for kubuntu. Thats what I did on my laptop.

Just boot from the install cd....

---

### Post by lamego on 2006-01-17
And what about reporting your problem with apt and synaptic instead ?
Kubuntu also depends on APT which means you need to understand your current problem.

---

### Post by bulldogzerofive on 2006-01-19
[QUOTE=mips]Backup your data and install from scratch deleting your existing ubuntu partitions and creating new ones for kubuntu. Thats what I did on my laptop.

Just boot from the install cd....[/QUOTE]

yes, you are going through more trouble than it is worth to fix something that a clean install will fix.

You do not necessarily need to delete all the partitions.  If you want to save your home partition and your settings and such, do this:

1.  Log in with your sudo-enabled account.
2.  In a terminal: 
```
sudo mv -r /home/*username/* /home/*username*_transition/
```
3.  repeat 2 for all users
4.  open up the user and group administration tool and write down all the users and groups you have created, including their UIDs and GIDs.
5.  Reinstall (k)ubuntu from the install cd.  During this process **only** format the partition you intend to use as /.  Don't forget to select the mount point the partition you have been using as home as /home.
6.  In the create users and groups dialouge in your new install, re-create the users and groups you had before with the same UIDs and GIDs.
7.  in a terminal: 
```
sudo mv -r *username*_transition/ [i]username/
```
just to be safe:
```
sudo chown -R *username*:*groupname* /home/*username*
```

Also to be safe, you probably should not do this with your first account, just subsequent user accounts.  There you go... a fresh install and all your data and settings are intact.

If anyone knows a better way to do this, I personally would very much like to know...

---

### Post by Hotchilli on 2006-01-19
the problem was fixed by removing kerio mail server.

hc:smile:

---

### Post by bulldogzerofive on 2006-01-19
That is weird.

Just out of curiousity, how did you remove it without apt?  just delete the binary?

---

### Post by Hotchilli on 2006-01-19
dpkg  --purge kerio-mailserver

hc:smile:

---

