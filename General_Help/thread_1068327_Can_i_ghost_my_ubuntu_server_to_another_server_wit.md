---
title: "Can i ghost my ubuntu server to another server with diff specs"
date: 2009-02-12
forum: General Help
---

### Post by cjtjamandra on 2009-02-12
Our company has upgraded our servers and now i need to transfer my whole system(ubuntu server) to the new server with higher specs than the old server.

is it possible to ghost my ubuntu server to the new server with different specs, higher processor and higher Hard disk capacity? plese help, thx in advance

---

### Post by jrusso2 on 2009-02-12
It often works if you can get a ghost program that works with Linux.

---

### Post by cjtjamandra on 2009-02-12
is the "Different specs" not an issue in ghosting? iam thinking mybe the system will only perform based on the specs of the old server, and the partition sizes?

---

### Post by jrusso2 on 2009-02-12
> **cjtjamandra said:**
> is the "Different specs" not an issue in ghosting? iam thinking mybe the system will only perform based on the specs of the old server, and the partition sizes?

Some ghost programs let you resize partitons.  The hardware usually works unless its so different it locks up.

---

### Post by amauk on 2009-02-12
Take a look at Remastersys
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

It'll take an existing Ubuntu (or Debian) install, complete with settings and changes, and make a customised install disk that you can then install on different hardware

---

### Post by jrusso2 on 2009-02-12
Nine times out of ten it will reprobe and identify the new hardware and keep going.

---

### Post by cjtjamandra on 2009-02-12
will you suggest a ghost program that features diff specs and hard disk size?

I will try the remastersys, please stay on track in case i've come up with a problem :)

---

### Post by cybergalvez on 2009-02-12
What about clonezilla? that worked recently for me and a couple of windoz pc we were building

---

### Post by cjtjamandra on 2009-02-12
> **cybergalvez said:**
> What about clonezilla? that worked recently for me and a couple of windoz pc we were building

I have seen clonezilla and it looks fine, can i use it even if my destination hard disk is larger? and have different specs?

---

### Post by haddog on 2009-02-18
CJ. Use G4L (Ghost for Linux). It is an open source imaging program similar to Symantec Ghost. 

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have an Ubuntu 8.04.2 LTSP server that I was bulding. Was using an old small quantun 20 gig ide hard drive for testing. Got everything config'd and then thought "what was I thinking? Why did I use this small 20 gig drive?" 

Needed to upgrade to an 250 gig sata drive. Created a G4L boot cd. Booted from the cd. Imaged the 20 gig to the 250 gig. Done. I unhooked the 20 gig, booted off the 250 gig with no issues.

---

### Post by cjtjamandra on 2009-02-19
> **haddog said:**
> CJ. Use G4L (Ghost for Linux). It is an open source imaging program similar to Symantec Ghost. 

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have an Ubuntu 8.04.2 LTSP server that I was bulding. Was using an old small quantun 20 gig ide hard drive for testing. Got everything config'd and then thought "what was I thinking? Why did I use this small 20 gig drive?" 

Needed to upgrade to an 250 gig sata drive. Created a G4L boot cd. Booted from the cd. Imaged the 20 gig to the 250 gig. Done. I unhooked the 20 gig, booted off the 250 gig with no issues.

Can you provide a step by step procedure how you did this? Even if i have many separate partitions in one disk:

my /usr/local/ has different partition.


Will this be an issue? or will it ask me the size that i will set to another partition?

---

### Post by cjtjamandra on 2009-02-20
I have just tested clonezilla on my server, followed the steps here:

[http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live-p2]("http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live-p2")

It generated some files but to my surprise the total size of the files are only 733 MB!!! it seemed that there is a problem because the total hard disk size of the hard disk i want to ghost is 72 GB and the used space is more than 7 GB.

Can someone explain why the size is so small?? is it ordinary? Iam not yet using the image to ghost my other server because of this.

---

### Post by cjtjamandra on 2009-02-20
> **haddog said:**
> CJ. Use G4L (Ghost for Linux). It is an open source imaging program similar to Symantec Ghost. 

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have an Ubuntu 8.04.2 LTSP server that I was bulding. Was using an old small quantun 20 gig ide hard drive for testing. Got everything config'd and then thought "what was I thinking? Why did I use this small 20 gig drive?" 

Needed to upgrade to an 250 gig sata drive. Created a G4L boot cd. Booted from the cd. Imaged the 20 gig to the 250 gig. Done. I unhooked the 20 gig, booted off the 250 gig with no issues.

Do G4L features saving the image on a USB External hard disk and then loading it to another machine using the external disk again?

---

### Post by haddog on 2009-02-20
Not sure ubout the G4L to a external USB. G4L appears to have many features though. When you boot it up, there are some pretty good discriptions of what it does.

---

### Post by cjtjamandra on 2009-02-20
> **haddog said:**
> Not sure ubout the G4L to a external USB. G4L appears to have many features though. When you boot it up, there are some pretty good discriptions of what it does.

You mean i need to have another hard disk to put my image on it while ghosting? and i cant use external drives?


do g4l features saving through samba? iam having a problem with clonezilla because it says that my network card is not supported.

---

### Post by Woody1987 on 2009-02-20
Im no expert but couldnt you just start fresh, install what you need and then copy over the /etc and /home directories to copy over the settings?

---

### Post by cjtjamandra on 2009-02-20
> **Woody1987 said:**
> Im no expert but couldnt you just start fresh, install what you need and then copy over the /etc and /home directories to copy over the settings?

sigh... my server has so many installed dependencies and by the way my ubuntu version is 7.10 and some on the dependencies for php, mysql, gd, and so many libraries are so hard to find and install.


it took me weeks to complete those installations. so i really need to ghost it badly, and i think that's what the purpose of ghosting is.

---

### Post by Woody1987 on 2009-02-20
couldnt you put the old hard drive into the new server, do a low level copy onto the new hard drive and then use a livecd to grow and mess with the partitions of the new drive?

---

### Post by cjtjamandra on 2009-02-22
> **Woody1987 said:**
> couldnt you put the old hard drive into the new server, do a low level copy onto the new hard drive and then use a livecd to grow and mess with the partitions of the new drive?


The old and new server has different hard disk type.. so i think i cant do that..

i have installed partimage, but i think it only backups per partition and can't backup a whole hard disk at once.

---

### Post by haddog on 2009-02-23
CJ. Have you tried to use G4L yet? It does allow you to do backups across a network. Nothing to install. It is a live cd created from an iso image. G4L can backup entire hard drives.

---

### Post by cjtjamandra on 2009-02-23
WIll G4L support my NIC? because clonezilla dcan't detect my NIC.

---

### Post by haddog on 2009-03-06
I haven't tried to image over a network. But I know G4L does have the capability.

---

### Post by haddog on 2010-04-02
> **cjtjamandra said:**
> WIll G4L support my NIC? because clonezilla dcan't detect my NIC.

I was just able to use clonezilla to clone a pc over a home network. Source is a dell mini 10v, target is an old dell optiplex, 2 Ghz processor maxed out with 2 gigs ram.

---

