---
title: "I need a dual boot, to install windows xp"
date: 2009-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yoshiki2 on 2009-07-29
I own a mini9 with ubuntu, but there are some programs that I need to run, so I need to install Windows xp. My mini is with 4 gig sd, so what do I need to install windows xp.. Can i use memory sdhc, or a flash drive? or do i need to change my 4 gigabytes sd, and how do i make it dual boot. thanks

---

### Post by cosine352 on 2009-07-29
I will say 4G is too small for two operating systems. If you can boot from USB then an external hard drive may be a good option. The problem is you need to bring the external drive with you all the time !!!!!

Another option will be to find alternative to those applications. There is a good chance that you will find a good alternative.

---

### Post by yoshiki2 on 2009-07-29
It's a program that requires windows office 2007.. so I'll have to use it I want it or not... so I can change my 4 gigabytes sd, and add a 16 sd? and make it dual boot? or can I install windows xp on the memory sdhc?

---

### Post by theGlitch on 2009-07-29
This is completely a theory as I am at work and unable to test it:

I recently killed my XP partition of my dual boot to go full Ubuntu. But in order to use my iPod Touch, I needed a newer version of iTunes (thus couldn't use WINE). So I download the newest version of VirutalBox and created a virtual XP machine in my Ubuntu partition. 

I gave it a dynamic virtual drive so I can change its size as needed. I know you can give the virtual machine a physical chunk of your HDD. So my theory is installing XP to an external HDD through VirtualBox; and when setting up the virtual machine map the HDD to your external instead of virtual (this can all be done in the GUI).

Again this is just a theory...

---

### Post by yoshiki2 on 2009-08-06
I got the windows xp disks.. and am replacing the ssd from 4 to 32 gb. How can I install ubuntu now? and how can i make partitions on windows xp?
thx
Or should I install ubuntu first with the Iso posted on the sticky, make the partitions and install windows xp after that? (how to make partitions) thx

---

### Post by vikhram on 2009-08-09
HI 

   First install XP and then install ubuntu bcoz installing windows after installing Ubuntu will overwrite your Grub and then u hv to go thro the hassle of rebuilding the GRUB from the cd.:KS

---

### Post by ugm6hr on 2009-08-09
Boot Ubuntu from USB/CD first.

Use "Partition Editor" (System menu) to create appropriate partitions (NTFS for XP at start of SD card).

Reboot. Then install XP.

Then install Ubuntu.

---

