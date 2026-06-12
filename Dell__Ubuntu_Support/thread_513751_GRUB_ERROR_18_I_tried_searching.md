---
title: "GRUB ERROR 18 I tried searching"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by gatdammit on 2007-07-30
Hi,
  I tried searching but I can't find it. I found some threads aboiut how to fix ERROR 18 in GRUB, but those all had to do with first installs and such.  I actually had my system up and running.  I have a Dimension 5150 and was running a 160GB HD with Feisty.  Now all of a sudden I booted up the other day and I'm getting a Error 18 message.  I can't seem to figure out how to resolve this.  If I repartition my drives won't i lose data? Right now I"m locked out of my system.  I need assistance! THanks.

---

### Post by logos34 on 2007-07-30
how about this link:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by gatdammit on 2007-07-31
So say I can't get past this GRUB error is there a way to access my HD then? from say a Windows system?  I need to get files off there.

---

### Post by gatdammit on 2007-07-31
I have my Linux HD plugged in and tried booting from the CD... how come it doesn't recognize the drive?

---

### Post by logos34 on 2007-07-31
> **gatdammit said:**
> I have my Linux HD plugged in and tried booting from the CD... how come it doesn't recognize the drive?

You can't boot the cd or you can't mount the linux partition because it doesn't recognize the hard drive?  Clarify.

Check that your Bios is seeing the drive correctly.  Verify it's set to 'auto'[detect].

---

### Post by gatdammit on 2007-08-01
No I can boot from the CD... but I have my drive also connected to one of my SATA ports.  So when I get into the system using the Live CD I can't seem to navigate to my SATA drive.  If I have to mount it manually... how do I do that?

---

### Post by logos34 on 2007-08-01
check that linux can 'see' the sata:

**sudo fdisk -l**

If so, then try to mount it manually:

[B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu[/B]   (*replace sda1 with your root partition)
**cd /mnt/ubuntu**

---

### Post by gatdammit on 2007-08-01
this is what i get when i hit sudo fdisk -l

Disk /dev/sda 163.9GB 16392804672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device          Boot     Start      End        Block                Id     System
/dev/sda1       *        1            19553    157059441      83    Linux
/dev/sda2                 19554    19929    3020220                 Extended
/dev/sda5                 19554    19929    3020188+               Linux Swap


i made the /mnt/ubuntu dir already... and when i try

sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

it returns some error... "wrong fs type, bad... check syslog - demsg | tail or so "  something like that... sorry i have to switch back and forth between systems... i don't have internet when i boot to the Live CD... thanks for your help though...

---

### Post by logos34 on 2007-08-01
you might try running a filesystem check:
[B]
sudo fsck /dev/sda1[/B]

---

### Post by gatdammit on 2007-08-01
Thanks I'll try that when I get home... does it matter that I was Dual booting to XP also?  I had my old XP system on an 80GB and then I got another 160GB to run Ubuntu off of.  I did some GRUB editing and made the Linux drive the 'master' so that it would boot GRUB... 

I just can't seem to anything on this error where someone actually had the system up and running.  I was using my Feisty since May of this year then all of a sudden a week ago I get the error while GRUB was trying to load.  Have you ever heard of this happening?  

Can I reinstall GRUB or something or am I just gonna get the same error?

---

