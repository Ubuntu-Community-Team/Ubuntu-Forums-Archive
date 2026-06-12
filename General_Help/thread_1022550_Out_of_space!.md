---
title: "Out of space!"
date: 2008-12-26
forum: General Help
---

### Post by DBQ on 2008-12-26
Hi everybody.

I have a problem.  My laptop has limited space, and I tired to install Eclipse Ganymede on it by following the these steps: [http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/](http://jhcore.com/2008/06/26/eclipse-34-ganymede-on-ubuntu/).

When installing openjdk-6-jdk, it demanded like 143 megabytes.  So generally speaking, I installed open-6-jdk.  Then I realized I will not have enough space to install the entire application. Hence I decided not to go through with it.  When I did apt-get remove openjdk-6-jdk, only like 40 megabytes were freed.  WHY??? I now cannot do anything on the laptop -- It does not even have enough room to save a text file.  Anybody would like to offer some wisdom on how to get out of this predicament?  Thank you all.

---

### Post by Sin@Sin-Sacrifice on 2008-12-26
sudo apt-get autoclean

localepurge

Go into synaptic and clean out the residual packages

Clean up that thing man.... get rid of anything that isn't important and even if it is.... put it on a CD or DVD or flashdrive or something. how big is the hard drive?

---

### Post by DBQ on 2008-12-26
Although it deleted some stuff, it still says my drive has 0 bytes free space.  How could that be?

---

### Post by DBQ on 2008-12-26
The problem is not that my drive is cluttered.  My partition is small - I never thought that I would grow so attached to Ubuntu. My partition is like 8 gigabytes.

---

### Post by Sin@Sin-Sacrifice on 2008-12-26
You try moving things to other partitions? Movies and whatnot? The larger files can be linked from a windows partition to the players and you could always make links to the folders. Clear out all media and see what you got. If it's apps that are taking up the space then you should think about making that partition larger.

---

### Post by wootah on 2008-12-26
How many kernel updates have you done? Maybe you have residual kernels laying around?

---

### Post by DBQ on 2008-12-27
This is strange -- it seems not matter what I move around, or which applications I unistall, it still says I have 0 bytes of space -- I cannot even save a simple textfile.

---

### Post by jerome1232 on 2008-12-27
huh what's the output of these two commands
```
df -h
sudo du -hx --max-depth=1 /
```

---

### Post by DBQ on 2008-12-27
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             7.1G  6.8G     0 100% /
tmpfs                 442M     0  442M   0% /lib/init/rw
varrun                442M  128K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M  2.7M  440M   1% /dev
tmpfs                 442M  104K  442M   1% /dev/shm
lrm                   442M   39M  403M   9% /lib/modules/2.6.24-22-generic/volatile
overflow              1.0M  136K  888K  14% /tmp

---

### Post by DBQ on 2008-12-27
118M	/etc
3.8G	/usr
4.0K	/srv
524K	/root
0	/sys
0	/dev
16K	/lost+found
1012M	/lib
736M	/home
0	/proc
12K	/media
4.0K	/opt
0	/tmp
4.0K	/initrd
4.0K	/mnt
7.2M	/sbin
669M	/var
146M	/boot
6.1M	/bin
6.7G	/

---

### Post by jerome1232 on 2008-12-27
Well you have almost 1 GB in /lib whereas I only have 207M so there's way to much there.

What about doing a "sudo apt-get autoremove" It should remove any programs that were installed as dependencies to already removed programs.

---

### Post by DBQ on 2008-12-27
Thank you.  This freed some space.  Is there anything else I can do?

---

### Post by jerome1232 on 2008-12-27
Just a few idea's to gain a few byte's here and there.

Remove some old kernels, keep at least 2 though.

To remove them open Synaptic and filter for installed applications, then search for linux-image, remove some of your older ones. (this might get you 100 MB's though at best)

/var is kinda big at 600 MB (mine on my 1.5 year old server sits at 400 MB) Perhaps you can delete some old logs? I don't know much about how one manages log rotation unfortunately. (200 MB's at best)

Other than that really your programs are what's using up the space, just find apps you don't really use and remove them, follow it up with an autoremove to get rid of any dependencies you don't need as well.

I'm still amazed at how big your /lib is.

---

### Post by wootah on 2008-12-27
> **jerome1232 said:**
> 
...

/var is kinda big at 600 MB (mine on my 1.5 year old server sits at 400 MB) Perhaps you can delete some old logs? I don't know much about how one manages log rotation unfortunately. (200 MB's at best)

...

Try logsave, logrotate and logd facilties along with the crontab :)

EDIT: Most of mine was in apt-get 's cache :) sudo apt-get clean fixed that up nicely

---

### Post by DBQ on 2008-12-27
So how do we use these lovely utilities?

---

