---
title: "Help creating hard drive image"
date: 2009-04-20
forum: General Help
---

### Post by kacike76 on 2009-04-20
HI all, 

I have a dv7-1025nr HP pavilion laptop that I need to send for service (something related to the screen). Before doing so, I need to make sure I back up my entire hard drive. I have a dual boot hard drive with Vista x64 and Ubuntu 8.10 x64. I was looking at using acronis true image home 2009 for the job of creating an entire image of the hard drive with both partitions that I can restore if HP decides to give me a new laptop. I would then write this image to my Netgear ReadyNAS duo, and restore it if needed. I bought acronis yesterday, but after reading some reviews online, I am not sure I’ll work. 
So, does anyone have any experience creating images of entire harddrives for dual boot systems? And how do I know it worked after I create the image? I would really like to test the image to make sure i will be able to restore it on an identical laptop if needed. I would hate to create an image and get a new laptop (identical hardware) and find that I lost my ubuntu partition. I've done tremendous amount of work to get my ubuntu configured the way it is now

Please help
Thank you

---

### Post by Wayne_V on 2009-04-20
I've used mondorescue and it worked great.  It also let's you restore your partitions to a disk of a different size if need be.

[http://www.mondorescue.org/](http://www.mondorescue.org/)

apt-cache show mondo

---

### Post by edthefox on 2009-04-20
If you have another computer, you can remove the hdd and attach it to your other computer and then use dd to dump the image to a file and then restore it when you get the new/repaired notebook back.

---

### Post by aeiah on 2009-04-20
on a livecd id do:

```

dd if=/dev/sda of=/home/root/backupdrive/hdd.img

```

this will do a bit-for-bit copy of /dev/sda to an image file. you'd have mounted your ext formatted external hard drive to /home/root/backupdrive/ first of course. you might want to add other options to your dd command so it compresses it on the fly or something. you'd just reverse the process to dump the image back onto the harddrive and in theory, your computer and its operating systems wont know the difference. you might want to add byte count options and all that stuff to it. there are loads and loads of dd examples flying around.

make sure your external drive is the same size or bigger than the drive you're copying from too. you may be able to get away with a smaller one if you're compressing on the fly since there's bound to be some free space on some of your existing partitions.

last thing, dont mix up input file (if) and output file (of)!

:o

---

### Post by kacike76 on 2009-04-20
Thank you all for your replies.  

The dd command sounds like a good option, but would it also copy over my vista partition?

Also, because is doing a bit by bit copy of the hard drive, does that mean that the hardware has to be identical for the restore procedure to be successful? Again, i am just trying to ensure that there were no errors in the dd by loading this image onto a different computer.  

Is the created image the same size as the copied hard drive if you don't compress?

Thanks again...

---

### Post by Wayne_V on 2009-04-20
Yes, with dd the new drive would have to be (nearly) identical.  And the uncompressed size would be the size of the disk --- you are backing up everything - whether it's data or not.

If you use something like mondorescue you create a bootable CD of your backup that you can then restore from.  And you can resize linux partitions on the fly (but not ntfs partitions).

---

### Post by peyre on 2009-04-20
I've recently switched over from Windows, so my imaging solution is still Windows-based.

What I've been using the past few years is DriveImageXML.  It's free, and comes on the Ultimate Boot CD for Windows ([http://www.ubcd4win.com/](http://www.ubcd4win.com/)).  Download and install the UBCDWin builder on your Vista machine, use it to make an ISO, then burn that to a CD.  Boot with the CD, tell it to enable networking and accept the defaults, map a drive to wherever you want to save the image, then run DriveImageXML and back up your disk there.

---

### Post by kacike76 on 2009-04-20
Any thoughts, ideas or sugestions on using Acronis True Image, i already bought the sotfware :) but i heard there are some problems using this software with Intrepid 64 bit.

---

