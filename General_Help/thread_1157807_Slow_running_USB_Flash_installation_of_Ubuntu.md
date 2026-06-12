---
title: "Slow running USB Flash installation of Ubuntu"
date: 2009-05-13
forum: General Help
---

### Post by solorize on 2009-05-13
Hi,

I have installed Ubuntu 8.10 on my
SanDisk Cruzer Micro (8gig) Flash USB stick.

It all runs ok from the stick, but it runs very very slow. 
It takes an age for say firefox to load up and allow me
to start typing anything in.

Does anyone know if it is possible to speed things up
somehow ?

I did read somewhere about enabling laptop mode?
but am unsure if that would help or how to do it.


Regards,

Mark

---

### Post by salvachn on 2009-05-13
Did you use your entire flash drive to install Ubuntu? I mean, did you partition the whole disk with ext3 and a swap? If you want to speed things up, take a look here:
[http://queasyquagmire.wordpress.com/2009/05/10/my-jackalope-jogs-jauntily-again/](http://queasyquagmire.wordpress.com/2009/05/10/my-jackalope-jogs-jauntily-again/)

---

### Post by solorize on 2009-05-13
Hi salvachn,

I did partition the drive into a 3meg ext3 and a 1meg swap.

I will have a look at the link now.


Regards<

Mark

---

### Post by snowpine on 2009-05-13
Yuck. Swap on a flash drive is a bad idea. It will be very slow and will wear out the drive. Also it sounds like you did a full install (designed for a hard drive install), rather than using the usb-creator utility (designed for flash drives).

Ubuntu runs much faster when installed to your hard disk.

---

### Post by Legace on 2009-05-13
If you need a fast, portable operating system, get Puppy Linux.

If you want to install Ubuntu and use it only on ONE machine, install it to your internal harddisk. It will speed things up quite a bit :)

---

### Post by umuro on 2009-05-13
> **solorize said:**
> Hi,

I have installed Ubuntu 8.10 on my
SanDisk Cruzer Micro (8gig) Flash USB stick.

It all runs ok from the stick, but it runs very very slow. 
It takes an age for say firefox to load up and allow me
to start typing anything in.

Does anyone know if it is possible to speed things up
somehow ?

I did read somewhere about enabling laptop mode?
but am unsure if that would help or how to do it.


Regards,

Mark

I do use SansDisk 16G without any problem. 

However, there are a few things to do

directories like /tmp, /var/run, etc has to be in RAM (not on USB!)

See here for the tmpfs recipe: (USB stick for more (K)Ubuntu performance) [http://conceptspace.wikidot.com/blog:20](http://conceptspace.wikidot.com/blog:20)

Then the USB stick must be ext2. Not ext3! 

Downgrade it to ext2 using tune2fs (delete the journal. see man tune2fs).

If you should have a journal (ext2 is ext3 - journal file) for more crash secuirty then you need to create a journal device on a normal hardisk (man tune2fs tells how to format a journal partition).

The reason is USB stick writes 6 times slower while it reads 200 times faster. With the actions above USB stick will not get write requests anymore and show its true performance. With necessary precautions the OS partion is totally readonly.

And it really gives better performance because there is no disk seek time, and it works in parallel with the internal HD. While an application is reading data from HD another binary will be launching without interrupting it. This means faster boot.

As for the wear out of the USB disks
a) OS is practically readonly. So it does not wear off. You won't make 1000000 OS upgrades.
b) The USB stick used for the SWAP wears off. Yes. Use different sticks for OS and SWAP. And change SWAP stick every 6 mounths.
If you insist on a totally USB stick system then that means you should carry 3 sticks for best life time
1. /
2. swap
3. /home

Still (/, /home) and a swap (2 sticks) would work out.

Because it's getting writes /home stick will die one day. But when the USB stick dies it becomes readonly. Data is not lost. So you'll have your chance to copy it to your new stick.

---

