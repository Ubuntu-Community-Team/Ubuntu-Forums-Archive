---
title: "cant write to hfs+ partition"
date: 2009-05-31
forum: General Help
---

### Post by rcmx on 2009-05-31
i JUST downloaded the ubuntu live cd and this is basically my 1st time booting into ubuntu

im currently in ubuntu
and when i try to copy files to my hfs+ partition, it tells me its read only

supposedly "root" is the owner and only "root" can change permissions

and im not logged in as "root"

how do i log into "root" so i can write files into my hfs+ partition?

ps. i CAN write to ntfs partition, if this makes a difference
heres a screenshot

[IMG]http://i39.tinypic.com/r0s55f.png[/IMG]

and heres a screenshot of the properties
[IMG]http://i40.tinypic.com/al0msp.png[/IMG]

any help would be appreciated
thanks

---

### Post by rcmx on 2009-05-31
bump! i really need help!

---

### Post by coffeecat on 2009-05-31
You can't write to the journalled version of hfs+, only the non-journalled version. Sorry. I found this out the hard way by much dint of formatting and reformatting an old drive and swapping it between my Mac and Linux. This was after I discovered that an hfs+ partition I had created with Gparted in Ubuntu I could read and write to in Ubuntu (and with my Mac), but not t'other way round. Or at least, not until I noticed the non-journalled option in Disk Utility in MacOS.

I think the other problem is that the root of the hfs+ partition is mounted and owned by root (root the superuser, that is). You get the same with a Linux ext3 partition.

Please describe exactly what you are trying to do. It sounds as though you are trying to write to the main root partition of a Mac. There may be another way of doing what you want to do.

---

### Post by rcmx on 2009-05-31
well
the xbox 360 can only read fat32 (4 gig limit =\) and hfs+

so i formatted my external hard drive (500gb) into 2 partitions
1 ntfs (for personal use) and one hfs+ (for my 360)

i partitioned using the gparted live cd

and then thats where my 1st post starts
im basically trying to copy some videos to the hfs+ partition

im not sure the 360 reads hfs if that was my only hope =\

---

### Post by coffeecat on 2009-05-31
> **rcmx said:**
> i partitioned using the gparted live cd

Hmm, that's interesting. Try this, but you need a good internet connection in the live session. From the live CD, open System > Administration > Synaptic. From Synaptic, install the packages hfsplus, hfsprogs and hfsutils. I believe you need only one of them to be able to write to the hfs+ partition, but I'm not sure which one. They're all fairly small anyway. With a live CD you'll be installing to RAM and will lose the apps as soon as you power down, but this is for a one-time use anyway.

Now open Gparted with your external drive plugged in. First thing, go to Device > Create Partition Table. Click on advanced and choose a 'Mac' partition table. Gparted can create a hfs+ partition in an msdos partition table, but a Mac can't cope with that - I don't know about the Xbox. Trouble is - I don't know whether an NTFS partition will work with a Mac partition table. You'll just have to try. If you go ahead and create the new partition table, this will erase everything on the external drive. Now create your hfs+ partition, and this *should* now be writeable by the Ubuntu live CD.


> **rcmx said:**
> im not sure the 360 reads hfs if that was my only hope =\

As far as I understand, hfs is an older version of hfs+. hfs+ comes in both journalled and unjournalled versions. When you create an hfs+ partition with Gparted it's the unjournalled version of hfs+, not hfs. If your 360 can read a journalled hfs+ filesystem, it should be able to read an unjournalled one.

---

### Post by rcmx on 2009-05-31
will i have to do this every time?
as in opening gparted, creating partition table, and all that?

---

### Post by rcmx on 2009-05-31
it didnt work
i cant format to hfs+

and i think its because i didnt install hsfprogs
i cudnt find it
it was on synaptic or w/e

[[IMG]http://img17.imageshack.us/img17/4623/screenshotjye.th.png[/IMG]](http://img17.imageshack.us/my.php?image=screenshotjye.png)

---

### Post by rcmx on 2009-05-31
so i tried this
[IMG]http://i40.tinypic.com/fwknpy.png[/IMG]
and still didnt work

im sure its hfsprogs that needs to be installed cause i already have the other ones

---

### Post by Fzang on 2009-05-31
You'll have to disable journaling in linux in order to write to HFS+ partitions I think,

I don't know how to do that though...

---

### Post by asmoore82 on 2009-05-31
> **rcmx said:**
> well
the xbox 360 can only read fat32 (4 gig limit =\) and hfs+

Xbox360 refuses to read NTFS?? can anyone else confirm this??

Micro$oft never ceases to piss me off.

you need a root nautilus session just once:
```
gksudo nautilus
```
and either 1. give your personal account ownership of the top level hfs folder
or 2. create a folder on the hfs as root and give your account ownership of that.

I prefer option 2 to stick closer to Unix roots, you would have the same
issue on an ext3/4 formatted external drive, so it's like creating a
"home away from home" folder for each user on the external drive.

---

### Post by rcmx on 2009-05-31
i know right?
why they chose macs format instead of their own is just ridiculous...

only reads fat32 and hfs+
ive been trying to work this out for at least a week

---

### Post by rcmx on 2009-05-31
i did sudo apt-get update
and 
[http://i44.tinypic.com/o8gehf.png](http://i44.tinypic.com/o8gehf.png)

---

### Post by coffeecat on 2009-05-31
It seems that hfsprogs is in the Universe repository, so you'll have to enable that before you can get hfsprogs. Strange - Universe is enabled in a default hard disk install, but not in the live CD. Goodness knows why.

Anyway, I've had another look at the Synaptic package description, and I don't think it's going to help you. hfsplus and hfsutils seem to be the important ones, and if they're not helping you I'm sorry, I'm out of ideas.

---

### Post by rcmx on 2009-05-31
damn
well i installed hfsprogs if that makes a difference

and when i try to format (making a partition table w/ MAC) i get this
[http://i43.tinypic.com/nox37t.png](http://i43.tinypic.com/nox37t.png)

i tried under msdos this time
and i get this
[http://i41.tinypic.com/4zw86q.png](http://i41.tinypic.com/4zw86q.png)
but it continues to load after i clicked okay
[http://i41.tinypic.com/14x0w0l.png](http://i41.tinypic.com/14x0w0l.png)
seems like the problem is ntfs

---

### Post by rcmx on 2009-05-31
someone REALLY beautiful at what.cd helped me

heres the solution

sudo apt-get install hfsutils
or

[http://packages.ubunut.com/jaunty/amd64/hfsutils/download](http://packages.ubunut.com/jaunty/amd64/hfsutils/download)

---

### Post by rcmx on 2009-05-31
nvm, it worked
but the 360 didnt detect it
i think its formatting as unjournalled

i formatted w/ macdrive7 on windows, and it formats it as journalled
so im guessing xbox only detects journalled

is there a way to format it as journalled in ubuntu?

---

### Post by asmoore82 on 2009-05-31
> **rcmx said:**
> is there a way to format it as journalled in ubuntu?No, AFAIK

I'm sure that Micro$oft did extensive compatibility testing on Xbox360 vs. Linux
before the 360 was released - of course when any other company does such testing,
they are trying to make sure it will work - with M$, the opposite would be true.

---

