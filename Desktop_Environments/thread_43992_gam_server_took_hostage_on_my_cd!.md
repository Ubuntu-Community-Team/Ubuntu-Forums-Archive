---
title: "gam_server took hostage on my cd!"
date: 2005-06-24
forum: Desktop Environments
---

### Post by antony7777 on 2005-06-24
Hi,

I'm a very new user to Linux itself. Tried it a couple of times a couple of years ago, but only for 3-4 hours.

Ok.. so I insert a cd. It showed automatically on desktop.  From nautilus I click on the cd. And then I close the nautilus. after that I tried the eject button, no response.  So I remember that Linux/Unix uses mount for cds. After searching a while I found umount command. But it told me: device is busy!

No application is using the cd. So I had to resort to reboot just to change the cd.

After some search on the internet I found out about disabling automatic mount and fuser. I disabled automatic mount. And tried this:
1. Mount it from shell, and then try to umount. Success. 
2. Mount from shell, then click the cd on nautilus. close the nautilus, umount: failed.

fuser /media/cdrom shows a process id. from System monitor I found it was: gam_server opening the /media/cdrom0 dir.
I said: "what's this? GAME server?"

Another quick search from the internet found out that it was a part of Gamin. From  synapse (applicagtion installer), I conclude that this gamin is quite important, so I didn't try to uninstall it. 

I did tried to kill the gam_server. The first time I killed it, I successfully umount and eject the cd. After that everytime I kill the gam_server, a nother gam_server process will appear. So still cannot umount.

So after I wasted 5 hours just to learn how to read and then eject a cd, I conclude that for new user the eject button is the restart computer button! So here I am again on a Windows box!

Question:
a. best practice for using cd?? How do you experts do it? Mount a cd, do stuffs, umount, change cd etc...?
c. Is this gamin is a must have?
b. Is there any petition out there that I can sign so linux will let us use the eject button?

---

### Post by sickdude on 2005-06-24
if you have the gnome desktop de cdrom should mount itself and it works just like windows. in this way you can eject with the hardware button to. well i can on my box

if you mount it yourself then the eject button is diabled and you can only eject it textbased


please correct me if im wrong but this is how i experienced it on my own machine

---

### Post by antony7777 on 2005-06-24
[QUOTE=sickdude]if you have the gnome desktop de cdrom should mount itself and it works just like windows. in this way you can eject with the hardware button to. well i can on my box
if you mount it yourself then the eject button is diabled and you can only eject it textbased
please correct me if im wrong but this is how i experienced it on my own machine[/QUOTE]

I do have the gnome desktop, but the cdrom can't be ejected with eject button before umount. Did the behabiour you described is since you first install??

Once I saw it automounted to /media/cdrecorder. Could this be the prob ?

And one more thing I have 3 hard drives and a CD-RW, due to something I switched the CD-RW from secondary slave to primary slave. And then I saw the fstab referring to hdd as cdrom. I changed it hdb. 

Or should I scrab the whole thing and reinstall?? :( I hate having to redownload all the applications..

---

### Post by sickdude on 2005-06-24
well if you know what drive is where the you can edit your fstab ([www.ubuntuguide.org](www.ubuntuguide.org), ctrl F "fstab") 

and i dont have any problems with the eject of my cdrom in gnome it works like a charm and it should work for you to if you press the eject button on the drive it shoud unmount i think

---

### Post by antony7777 on 2005-06-27
[QUOTE=sickdude]well if you know what drive is where the you can edit your fstab ([www.ubuntuguide.org](www.ubuntuguide.org), ctrl F "fstab") 

and i dont have any problems with the eject of my cdrom in gnome it works like a charm and it should work for you to if you press the eject button on the drive it shoud unmount i think[/QUOTE]

Am I the only one having problem with this cd-umount-failure thing? ](*,)  Will a reinstall cure this?

---

