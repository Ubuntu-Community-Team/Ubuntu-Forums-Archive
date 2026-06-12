---
title: "Rescue fails to install the base system"
date: 2009-02-17
forum: General Help
---

### Post by Sleepy-zz-John on 2009-02-17
Hi,

   I installed my Intrepid Ibex from an alternate text-install CD and had it all working fine.    But then I did a silly thing and removed evolution-plugin packages and lost my Gnome Desktop,  so now I'm trying to recover my broken system by booting from my original CD and using its rescue mode.   

Everything seems to go OK with the rescue until it comes to the "Install the base system" step.   This step runs for a while but then reports:

Unable to install busybox-initramfs 

so it's at this point that I become lost :confused:

Don't know if it's relevant, but one possible clue is that just a few days prior to me removing those evolution-plugins I thought I didn't need,  I did an upgrade which according to logs changed:

busybox-initramfs from (1.1.10.2 -ubuntu6) to (1.1.10.2 -1ubuntu7)

A possible theory I can throw in here is that perhaps this upgrade is incompatible with earlier version files that are still on my rescue CD.

If this theory is correct,  it might be useful that I've found a copy of pre-upgrade busybox-initramfs (1.1.10.2 -1ubuntu6) in var/cache/apt/archives,  and maybe for the purposes of finishing my rescue it would be worth going back to my pre-upgrade version, and re-doing the upgrade again later.  

But this theory is only speculation, and basically I'm lost.  That's why I'm seeking advice here on what steps I could do to get back on track with rescue.

---

### Post by Sleepy-zz-John on 2009-02-17
Forgot to mention thread 1062823 that I posted in Absolute Beginners Talk "How to restore lost panels in Gnome"  last week,  which explains what led up to trying to recover my broken system with the rescue mode on the original installation CD.

---

### Post by teaker1s on 2009-02-22
```

```Two ways you may be able to repair your system.
firstly make sure you have wired network connection

1) forget the rescue option on install iso
Start machine at grub boot screen select recovery kernel. This will bring you to a black and white screen.

Previously I have repaired several machines by using a meta package (one that causes all desktop required files to get installed) 

Try these commands

```
sudo apt-get update
``` updates package information

```
sudo apt-get install ubuntu-desktop
``` meta package to install desktop

```
sudo apt-get install ubuntu-base
``` believe  now redundant but try
```
 sudo reboot
``` restart your machine
2) use live cd to repair install,maybe someone can point you to a good tutorial or clear guide.

---

### Post by Sleepy-zz-John on 2009-02-23
Many thanks for your suggestions,  Teaker1s.   I'm not quite there yet,  so I'd just like to run through some of the suggestions and give my feedback, if I may, please.

First,  with the No 1 way:

> firstly make sure you have wired network connection...
....forget the rescue option on install iso
Start machine at grub boot screen select recovery kernel. This will bring you to a black and white screen.

My LAN is plugged in and works OK in other shell configurations that I've set up in Rescue Mode,  but not in the recovery kernel.  The recovery mode kernel fails with 

"*configuring network interfaces ...
modeprobe: FATAL:  Could not load /lib/modules/2.6.27.11-generic/modules.dep"

Beyond that point I couldn't log-in with my user and pw because the system (not me) seemed to have forgotten it.   However I could press enter and get a root prompt there, so as suggested I tried:

> Code:
sudo apt-get update 

Without any network I suppose this step was doomed to failure;   it gave me:  

"E: dpkg was interrupted;  you must manually run 'dpkg --configure -a' to correct"  

so I ran that dpkg code, and it reported:  

"Cannot find /lib/modules/2.6.27-11-generic"

I was able to look in /lib/modules/ and confirm that it was completely empty 

Since I can get a network connection working OK from a shell prompt in Rescue mode, I again tried:

> Code:
sudo apt-get update

but it gave the same result as above,  i.e. that dpkg was interrupted and /lib/modules/2.6.27-11-generic could not be found. 

So I think the question I need to ask now is what ought I to have in my /lib/modules directory and where can I get it from? 

I'm also having a stab at your second suggestion:

> 2) use live cd to repair install,maybe someone can point you to a good tutorial or clear guide. 

I've downloaded a live CD and can use it to easily see all my originally installed directories,  and I'm now trying to get the hang of mounting commands so I can save all my original home directory on an independent drive with a view to replacing it back in a new installation later.   

A snag it seems to me with both Live CD and my Rescue mode disc,  though, is that they are only up to 2.6.27-7-generic,  so they can't match my installed 2.6.27-11-generic.   My guess is that whatever it is that I need to replace in my broken installed system would have to come from network, not from CD.  

Anyway, thanks again for the suggestions.   Any further ideas based on this feedback would of course be very welcome.

---

### Post by teaker1s on 2009-02-23
Okay lets try this another way, boot recovery kernel then 
```
sudo apt-get -f install
``` 
```
sudo dpkg --configure -a
```
it's possible you have broken or partially installed packages that can cause issues.

then


```
sudo apt-cdrom add
```
place alternate cd in drive we are going to use it as our sources, because the network is broken
```
sudo apt-get update
```

```
sudo apt-get install ubuntu-minimal
``` lets try and get a commandline with networking 

```
sudo apt-get install ubuntu-desktop
```
now lets see if we can get a desktop

---

### Post by jenkinbr on 2009-02-24
Just to note: sudo isn't required at the root recover consol - you are already root.

---

### Post by Sleepy-zz-John on 2009-02-25
> **jenkinbr said:**
> Just to note: sudo isn't required at the root recover consol - you are already root.
Yes,  I had noticed that,  but thanks anyway;  it's just as well because the system doesn't recognise my user and pw any more when I try to log-in with Ctrl +D in recovery mode, so I guess providing a pw for sudo would equally be a problem.  

OK,  I'm going to come back in a seperate response to the latest suggestions from teaker1s very soon.     Many thanks   :|

---

### Post by Sleepy-zz-John on 2009-02-25
> **teaker1s said:**
> Okay lets try this another way, boot recovery kernel   .....*SNIP*.....
it's possible you have broken or partially installed packages that can cause issues....
You are right!   I've certainly got something fairly basic that's missing or broken because during a recovery mode boot, I'm now always seeing:

"modprobe: FATAL:  Could not load /lib/modules/2.6.27-9-generic/modules.dep:  No such file or directory"   (- or whatever number kernel I've booted in).  

> then

```
sudo apt-cdrom add
```
place alternate cd in drive we are going to use it as our sources, because the network is broken  ....

OK, this yields the following:

"Identifying .. [6572c137944babfa05d64ca9d78dcfcb-21]
Scanning disc for index fields ..
Found 0 package indexes, 0 source indexes, 0 translation
E: unable to locate any package files"

So it seems to be finding my drive but I don't understand why it's not finding anything on the CD.  A check with ls -a cdrom yields only  . ..

So in a recovery boot like this I don't have access either to my alternate cd files nor to network.

>  lets try and get a commandline with networking 

I've found two ways of doing that.  One is using Rescue mode on my alt cd, and the other is using a Live CD.

Taking the Rescue mode way first,  I found two sub-choices,  one is a shell rooted on /dev/sda1, and the other is a shell rooted in an installation environment.   In the first of those two subchoices I come back to the problem I've described in an earlier post:

[QUOTE} Code:
sudo apt-get update[/QUOTE]
Yields "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct", and then I'm back to "Cannot find /lib/modules/2.6.27-11-generic"

In the second of those two subchoices, I'm running in BusyBox with only a limited set of commands that doesn't include apt-get.   With this, though, I not only have network access, but I can also see all the files on my alternate cd.  For example I can find /cdrom/pool/main/g/gnome-panel there,   but I don't know how to use BusyBox commands to install it.  

Using Live CD,  I can see /lib/modules/2.6.27-7-generic directory is there in Live CD, but it's missing in my installed /ext 3/lib/modules/  Trying to move a copy across to my installed system runs into permission problems that I'm still trying to figure how to overcome. 
   
```
sudo apt-get install ubuntu-desktop
```
now lets see if we can get a desktop[/QUOTE]

Yes,  Absolutely!   That's what I'm aiming for,   but so far still remains only a dream

My gut feeling is that my solution ought to lie somewhere in Rescue mode, but with my limited knowledge am finding that a bit hard going.       

Anyway, thanks once again for the suggestions, and I'm still telling myself it's all good fun   :lolflag:

---

### Post by teaker1s on 2009-02-25
**This isn't my area of expertise using live cd to repair corrupted system-would have liked a better howto to point to, but this is all I could find**

You could try


> ***for those all kind of situation or other situation that make you can't log on after restart even using 'safemode' ....so you need livecd to repair it...

put you livecd in and restart...then just log on to livecd....

then open terminal

type

sudo mkdir /mnt/repair

sudo mount /dev/?d?? /mnt/repair

*noted that ?d? mean part of your ubuntu root partition....it might be sda1...or hdb1 or sdb or whatever...depend where you install your ubuntu....

sudo chroot /mnt/repair su

sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade


exit
sudo reboot

take out your livecd...with luck you should can run your ubuntu as usual 

At this point, If we can't get any further I'm not sure what to recommend except a new thead asking how to repair using live cd
or
 using knoppix live iso to boot and rescue your home folder and data.

---

### Post by jenkinbr on 2009-02-25
> **Sleepy-zz-John said:**
> You are right!   I've certainly got something fairly basic that's missing or broken because during a recovery mode boot, I'm now always seeing:

"modprobe: FATAL:  Could not load /lib/modules/2.6.27-9-generic/modules.dep:  No such file or directory"   (- or whatever number kernel I've booted in).  



OK, this yields the following:

"Identifying .. [6572c137944babfa05d64ca9d78dcfcb-21]
Scanning disc for index fields ..
Found 0 package indexes, 0 source indexes, 0 translation
E: unable to locate any package files"

So it seems to be finding my drive but I don't understand why it's not finding anything on the CD.  A check with ls -a cdrom yields only  . ..

So in a recovery boot like this I don't have access either to my alternate cd files nor to network.
In recovery mode, you need to manually mount media.  Try ```
mount /dev/cdrom /media/cdrom
```

---

