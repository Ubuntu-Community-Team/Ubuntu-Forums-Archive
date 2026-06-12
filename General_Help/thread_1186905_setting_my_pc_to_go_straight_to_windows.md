---
title: "setting my pc to go straight to windows"
date: 2009-06-14
forum: General Help
---

### Post by suffery on 2009-06-14
hey guys.
i was wondering if there was a way to make my computer go straight to windows as it usually would and say if i pressed a hotkey or something at startup it would allow me to go to ubuntu

without the choosing wich os to go into.

if it were my choice i would leave it as it is but i have a few computer illiterate people in my house..and i generally dont like kids startiong up my pc and clicking away..

any solutions?

---

### Post by Chemical Imbalance on 2009-06-14
You can install startup-manager to edit your GRUB settings.

Open up Terminal under Accessories and paste this in and press enter:
```
sudo aptitude install startup-manager
```

It appears under System, Administration.

Once there you can set the default option to boot Windows.

---

### Post by suffery on 2009-06-14
john@Linux-pc:~$ sudo aptitude install startup-manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package whose name or description matched "startup-manager"
Couldn't find any package whose name or description matched "startup-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

it didnt show up..
know the probem?

---

### Post by Chemical Imbalance on 2009-06-14
Hold on a second...

try this:

```
sudo aptitude install startupmanager
```

---

### Post by suffery on 2009-06-14
yea i checked
its not there
what will the name be?

i also tryed to grav a screenshot and it said error no room left on disk or something liek that
yet i have a 160gb hard drive


hold on
that command you just gave me is doing alot more than the old one
hold up a sec

---

### Post by Chemical Imbalance on 2009-06-14
I changed the syntax.  Try this code:

```
sudo aptitude install startupmanager
```

It's startupmanager, not startup-manager.

---

### Post by suffery on 2009-06-14
its on there now
but gave me "unable to copy the users xauthorization file"

how do i fix this?

---

### Post by Chemical Imbalance on 2009-06-14
When does it say this?  After changing something or just after opening it?

---

### Post by suffery on 2009-06-14
after trying to open it.

---

### Post by Chemical Imbalance on 2009-06-14
You said earlier your disk was full.  This seems it could be that.

Open up System Monitor (System, Administration) and go to the Filesystems tab and see if any are full.

---

### Post by suffery on 2009-06-14
yea it says its full..i dont know how eathier
yet i have 70 something gigs left on windows xp

how can i add more?

---

### Post by Chemical Imbalance on 2009-06-14
Ooh, that's really unfortunate.  How big is the partition you have assigned to Ubuntu?

You might have to reinstall and resize your Windows partition smaller to give more room to Ubuntu.

---

### Post by suffery on 2009-06-14
apparently windows got greedy and only gave it 2.3 gibs..

am i going to have to reinstall this thing?

---

### Post by Chemical Imbalance on 2009-06-14
> **suffery said:**
> apparently windows got greedy and only gave it 2.3 gibs..

am i going to have to reinstall this thing?

Yes.  When you go through the installer, you will have to choose "Manual".

There you will have to resize your Windows partition to something a bit smaller, say take 10 gbs off.

Windows didn't "take" your space.  You have to manually choose how much space each operating system gets when you install.






Here is a good guide you should read first: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and this too: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Be careful.

---

### Post by suffery on 2009-06-14
ah ok

ill be back when ever then

---

### Post by synapsys on 2009-06-14
Either way you're going to have to shrink the windows partition which could have some negative results. Be sure to fire up windows and run a defrag, then backup all your important files, as a resize could cause data loss.

Then boot up a live cd and fire up gparted. 

You can then shrink your windows partition to something more reasonable, and grow your ubuntu partition.

---

### Post by Chemical Imbalance on 2009-06-14
Just make sure you backup all your important files first and read the guides I posted.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and this too: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

