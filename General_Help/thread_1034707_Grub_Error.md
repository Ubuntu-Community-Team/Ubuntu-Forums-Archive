---
title: "Grub Error"
date: 2009-01-08
forum: General Help
---

### Post by johnmarkbuchanan on 2009-01-08
I have two hard drives, one with xp and another that i recently formatted and have a four gig "swap" partition and a 160 gig partition dedicated to ubuntu 8.10. However during my "text only" install it, said that it recognized windows on my computer and mentioned installing grub, I said yes and went on with the install. The first time I booted ubuntu after the install I recived the following error 

Grub Loading stage 1.5.
Grub loading, please wait...
Error 17

So I reinstalled 8.10 but this time when asked about Grub i said no, and the installation said it was necessary to start my OS, so i tried putting it on the hard drive that only had ubuntu on it and i recived the same error the first time i booted. 

Now I have read a how-to on restoring Grub, only I don't know what exactly was wrong in the first place and what I need to do differently. Any thoughts?

---

### Post by nimbus9 on 2009-01-09
I had this error, too. I had grub on one drive and ubuntu on another. When my computer tried to boot off the drive with grub on it, I got an error 17. I had to unplug the second drive to sort it all out but I am sure there is a less drastic solution.

---

### Post by logos34 on 2009-01-09
sounds like you're still booting from the windows disk...go into the Bios at startup and make the ubuntu drive the boot disk

---

### Post by johnmarkbuchanan on 2009-01-09
I might have to give unplugging the one hard drive a try, but I am deffintly booting to the second hard drive with ubuntu installed. When I boot to the first drive it proceeds to boot up windows.

---

### Post by caljohnsmith on 2009-01-09
> **johnmarkbuchanan said:**
> I might have to give unplugging the one hard drive a try, but I am deffintly booting to the second hard drive with ubuntu installed. When I boot to the first drive it proceeds to boot up windows.
In my "vicarious" experience of helping in the forums, getting a Grub stage1.5 error 17 is sometimes caused by how the drive is set up in BIOS, and in more rare cases, how the HDD is jumpered if it is an IDE drive. But to get a clearer picture of your setup in order to make sure it isn't due to some other obvious reason, from the Live CD how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by Herman on 2009-01-09
> I have two hard drives, one with xp and another that i recently formatted and have a four gig "swap" partition and a 160 gig partition dedicated to ubuntu 8.10. However during my "text only" install it, said that it recognized windows on my computer and mentioned installing grub, I said yes and went on with the install. The first time I booted ubuntu after the install I recived the following error 

Grub Loading stage 1.5.
Grub loading, please wait...
Error 17

So I reinstalled 8.10 but this time when asked about Grub i said no, and the installation said it was necessary to start my OS, so i tried putting it on the hard drive that only had ubuntu on it and i recived the same error the first time i booted. 

Now I have read a how-to on restoring Grub, only I don't know what exactly was wrong in the first place and what I need to do differently. Any thoughts?:D That problem is very simple to solve. 

All you need to do is go into your BIOS and change the hard disk order so the hard drive with GRUB installed to it will be the first hard drive.
Ubuntu 8.10 and later features UUID booting, which is very good, as long as you can point your BIOS at the right MBR to begin with. 

The problem comes about most often when there is one or more SATA drives and one or more IDE hard drives in the same computer. Some people may have a USB hard drive or a USB flash memory as well. Different BIOSes have different numbering priorities for the different kinds of drives if it's just left up to the defaults. 

There is no reason why you have to keep to the BIOSes default numbering scheme, and it's a lot easier to switch hard drives than go re-installing GRUB and manually editing operating system files. It only takes about a minute or less. [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").

Intrepid Ibex's implementation of UUID numbers for booting is so good, that yesterday I had a daisy chain of USB hubs with flash memory sticks attached to them and Intrepid Ibex's GRUB in my EeePC was able to find the right USB flash memory stick install and boot it without any problems at all. I had three USB hubs with four ports each, with three memory sticks each and one port for the next hub. I plugged the memory stick into the third hub in the daisy chain. Some memory sticks had operating systems in them and some didn't. 
The correct Ubuntu memory stick booted the first time.

This is why I say you should not need to edit files or re-install GRUB if you have Intrepid Ibex 8.10 or later. 

Regards, Herman :D

---

### Post by chdieawoy on 2009-01-09
Hi, I am new here. I viewed all posts. ----------------------------------------------------------------------------------------------[Nature inspired jewelry](http://www.towholesalejewelry.com/to/33.html), [Wholesale Fashion Magnetic Jewelry](http://www.towholesalejewelry.com/to/34.html), [Dragon is a mystery in China](http://www.towholesalejewelry.com/to/35.html), [Red Gold Fashion Jewelry](http://www.towholesalejewelry.com/to/36.html), [What Is New For Fashion In Jewelry](http://www.towholesalejewelry.com/to/37.html)

---

### Post by meierfra. on 2009-01-09
> This is why I say you should not need to edit files or re-install GRUB if you have Intrepid Ibex 8.10 or later. 

There are still cases  where Grub needs to be reinstalled: 

Say you have two hard drives, sda and sdb, with Ubuntu   and XP on /dev/sda,  and say /dev/sda has a regular Windows MBR. During installation you choose Grub to be installed to /dev/sdb.   The installer will run "grub-install /dev/sdb".  grub-install will use 

(hd0) /dev/sda
(hd1) /dev/sdb

as device map. Since  Ubuntu is install on /dev/sda=(hd0), the first track  of /dev/sdb will contain instructions to look on (hd0) for stage2.

This makes it impossible to boot into Ubuntu:

If you set the bios to boot from sda, you will  boot into Windows.
If you set the bios to boot from sdb, Grub will look on (hd0) for stage2.  But (hd0) is now /dev/sdb, and you will get some kind grub error (probably 15,17 or 22) 
The fact that Intprepid uses UUID does not help in this case. The UUID's are only used by stage2, not by stage1/stage1.5

---

### Post by Herman on 2009-01-10
Yes, you are right, but in that case the user has voluntarily chosen where to install GRUB, so therefore they should be aware of what they are doing. :)

---

