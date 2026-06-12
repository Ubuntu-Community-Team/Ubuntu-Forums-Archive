---
title: "how do I partion"
date: 2008-12-28
forum: General Help
---

### Post by jprice19 on 2008-12-28
I have the current ubuntu 8.10 on my laptop. I have an xp cd and am wanting to download that and then partion my computer so that I can have xp and ubuntu on my computer. I need xp cause there are a couple different programs that won't work with ubuntu. I put in the cd and it brings up a cd on my desktop and the cd has a lot of files, but I can't get it to run. What do I need to do?

---

### Post by gettinoriginal on 2008-12-28
Depends on what size HD you have.  You can burn a live CD from Gparted that will partition you HD

---

### Post by jprice19 on 2008-12-28
I have a 250gb hard drive. The main thing is, the cd won't just boot. I don't know how to get it working. I was figuring I could download xp and then re-do ubuntu all together and just do the partioning through there. How would I get that cd working?

---

### Post by Jammanuser on 2008-12-28
> **jprice19 said:**
> I have the current ubuntu 8.10 on my laptop. I have an xp cd and am wanting to download that and then partion my computer so that I can have xp and ubuntu on my computer. I need xp cause there are a couple different programs that won't work with ubuntu. I put in the cd and it brings up a cd on my desktop and the cd has a lot of files, but I can't get it to run. What do I need to do?

You can use Gparted to partition your hard drive. This is already on your LiveCD, and so all you have to do is boot from the CD, and then go to System>Administration>Partition editor 
to open up Gparted. After that, the process to resize your main partition, and then create a new partition with the free space is fairly straightforward. 

As for the XP CD...you will first have to boot from it, by putting the CD/DVD drive first in the BIOS, in order to install XP. You can't install it from the desktop...;)

Hope this helps! :popcorn:

-Jam man

:guitar:

P.S. I can give you more detailed instructions if you need them.

---

### Post by Jammanuser on 2008-12-28
> **jprice19 said:**
> I have a 250gb hard drive. The main thing is, the cd won't just boot. I don't know how to get it working. I was figuring I could download xp and then re-do ubuntu all together and just do the partioning through there. How would I get that cd working?

Like I said above, you will need to put your CD/DVD drive first in the BIOS in order to boot from the CD, which will allow you to install XP. To do this, simple press F2 at startup, while still at the manufacturer's startup page (in my case, the Dell startup page) and then you will enter the BIOS, where you can put the CD/DVD drive first in the drive order, by simply selecting it, and moving it up to the top by pushing "u" a few times.

Hope I helped! :)

-Jam man

:guitar:

---

### Post by skern03 on 2008-12-28
> **jprice19 said:**
> I have the current ubuntu 8.10 on my laptop. I have an xp cd and am wanting to download that and then partion my computer so that I can have xp and ubuntu on my computer. I need xp cause there are a couple different programs that won't work with ubuntu. I put in the cd and it brings up a cd on my desktop and the cd has a lot of files, but I can't get it to run. What do I need to do?

You can also run VirtualBox from Sun, and install XP as a virtual instance under Linux. You'll need about 10 GB, if memory serves me correctly. 

There are two versions, OSE (open source edition) and PUEL (personal use). You'll want the latter:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
If you decide to do this, there are some threads on this forum that describe how, also on the kubuntu forums. Make sure you set up the repositories - there are directions on Sun's VirtualBox site that will guide you through it.

HTH...

---

### Post by Jammanuser on 2008-12-28
> **skern03 said:**
> You can also run VirtualBox from Sun, and install XP as a virtual instance under Linux. You'll need about 10 GB, if memory serves me correctly. 


Yes...and there is also that method! :) Though I prefer installing XP to a separate partition, rather than to a virtual machine, simply because some things wont work right on a virtual setup, though they work just fine on a real install of XP. ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

