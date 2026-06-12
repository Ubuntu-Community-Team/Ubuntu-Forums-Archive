---
title: "Getting the iPod nano to work in Amarok"
date: 2005-12-20
forum: Desktop Environments
---

### Post by jaon on 2005-12-20
Hi there.  Before I start, let me just say I did a quick search of the forums and it seems I'm not the only one having trouble getting iPods to work correctly.  I wasn't able to find any thread which had a problem (and a solution) that could help me though, so I'm posting here.  If someone else has already had (and solved) this problem, just let me know, thanks. :) 

Okay, I'm running Kubuntu 5.10 and I have a 4gig iPod Nano.  When I plug it in, it correctly identifies it is an iPod, mounts the device, and puts the iPod icon on the desktop.  It even name's the icon correctly ("Jason's iPod").
When I tried to run it in Amarok however, it didn't work, saying that the iPod wasn't mounted.  I couldn't get Amarok to give me any more detail than this.

So I checked the filesystem, and it was mounted.  The iPod was mounted to /media/ipod/ where all the other usb devices where.  The help file in amarok said that the ipod needed to be mounted to /mnt/ipod/, so I tried that, by adding a line to fstab, but even with the ipod mounted to /mnt/ipod/, amarok still couldn't detect it.

A few other threads mentioned yamiPod, so I downloaded that and tried to run it, but it also simply claims the iPod is not mounted.

In case anyone needs to know, the device the ipod is running on at the moment is "sda2", though at times it has also run on sdb1 and sdb2.  The KDE version I'm using is 3.5.0, and Amarok 1.3.1

I'm stuck for ideas at to what else to try.  Anyone got any suggestions?

---

### Post by 23meg on 2005-12-20
Do you have the "ipodslave" package installed?

---

### Post by ltmon on 2005-12-20
Give gtkpod a go also.

Amarok will be switching to use the same library as gtkpod in future versions, so getting it working with gtkpod will give good value for money.

L.

---

### Post by 23meg on 2005-12-20
The new lib is actually already implemented in SVN, which the amarok devs recommend to people who are unable to get their ipods working.

jaon, as a last resort, try transferring one file to your ipod via gtkpod, with extended info enabled, and then switching to amarok. That fixed things for me once.

---

### Post by Mudbream on 2005-12-21
I saw an article in the free online Tux online magazine explaining iPods and Amarok. I don't have an iPod so have no idea how good the article is.

Just go to [http://www.tuxmagazine.com/](http://www.tuxmagazine.com/) and join (its free and I've never got any spam from them) and download the June edition (number 3 I think).
Hope that helps.

---

### Post by jaon on 2005-12-21
Thanks 23meg and ltmon.

I installed GTKPod, and that led me to the source of my problems.  Basically, from GTKPod I was able to see that it could find the iPod, but couldn't find some of the files needed to read the database.  
I figured this meant my software on the actual iPod was corrupted somehow (maybe by unplugging it while it was still transferring something?? :confused: ) So I went on a different computer running XP and used the apple software to restore the iPod.  

I was then able to open it and write to it using GTKPod, which was great.  Amarok can read the files on the iPod, and it appears to be transferring them correctly, but then it crashes when the transfer meter reaches 100%.  I'm not going to worry about it for now.  I'll just use GTKPod.

Thanks for your help though... this is the first issue I've posted on the ubuntu forums and I'm impressed with you guys already.  Thanks.

For future reference, does anyone know if there's a way to restore your ipod from linux, so I don't have to find a windows machine to do it?

-Jason

---

### Post by ltmon on 2005-12-21
[QUOTE=jaon]Thanks 23meg and ltmon.

I installed GTKPod, and that led me to the source of my problems.  Basically, from GTKPod I was able to see that it could find the iPod, but couldn't find some of the files needed to read the database.  
I figured this meant my software on the actual iPod was corrupted somehow (maybe by unplugging it while it was still transferring something?? :confused: ) So I went on a different computer running XP and used the apple software to restore the iPod.  

I was then able to open it and write to it using GTKPod, which was great.  Amarok can read the files on the iPod, and it appears to be transferring them correctly, but then it crashes when the transfer meter reaches 100%.  I'm not going to worry about it for now.  I'll just use GTKPod.

Thanks for your help though... this is the first issue I've posted on the ubuntu forums and I'm impressed with you guys already.  Thanks.

For future reference, does anyone know if there's a way to restore your ipod from linux, so I don't have to find a windows machine to do it?

-Jason[/QUOTE]

I think gtkpod will have this functionality soon.

Until then, use "gnupod".  It's command line only and a little cryptic... but it works.

L.

---

