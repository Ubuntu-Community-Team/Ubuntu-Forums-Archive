---
title: "[SOLVED] Ubuntu no longer loads"
date: 2008-01-12
forum: Desktop Environments
---

### Post by Travis Bickle on 2008-01-12
Hello everyone, I am fairly new to Ubuntu and  tried to find a solution to my problem before creating this post. I had feisty fawn 32bit edition installed on my previous system which worked great, dual booting between windows media center edition and Ubuntu. I built a new rig about 4 weeks ago, formatted my hard drives and first installed Windows XP 64bit edition then proceeded to install Ubuntu 7.10 64bit edition. I didn't need to partition my hard drive, I simply formatted the existing partitions and was successful. Everything was fine with dual booting until yesterday. I booted into Ubuntu, simply tried to set up a different screen saver then my computer just rebooted into the bios. I tried to go back into ubuntu but it just simply hangs and then restarts.  Ubuntu recovery mode works, memtest works and windows works. I even tried to boot into Ubuntu by booting from cd and got the same result, computer restarts itself. I even created a new disk with no luck. Here is my system specs.

AMD Athlon 5200+ 2.6 Gig Processor 65Watt 2x1MB Level 2 cache, Mushkin 2GB (2 x 1GB) 240-Pin 
DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory 4-4-4-12 Timings, Gigabyte 
GA-M57SLI-S4 AM2 Nvidia nForce 570 SLI MCP ATX AMD Mobo, Asus GeForce 8500GT 256MB 128-bit 
GDDR3 PCI-E x16 GPU, Zalman CNPS 7900 HSF, NEC DVD RW optical, BENQ DVD RW w/lightscribe 
optical, WD 160Gig Sata HD, WD 250 Gig Sata HD,500Watt Antec Smartpower PSU, Cooler Master 
Centaurion5 CAC-TO5 black/silver aluminum Bezel Chassis, Windows XP Professional 64bit 
Edition OS & Ubuntu Linux 7.10 64bit version in dualboot mode. 

I really want to fix this, I love Ubuntu and have found myself using it more then windows. The only time I was using windows was to play games, everything else I was using Ubuntu. Thanks for listening.

---

### Post by erginemr on 2008-01-12
Hello,

Can you please find out what is causing the system to crash (the error message I mean)? You can see behind the scene (i.e. orange progress bar) by pressing Alt+F3.

---

### Post by Travis Bickle on 2008-01-12
For some reason ever since I installed 64bit edition, I never saw the "orange bar". My monitor would go into standby mode, lost signal if you will. After a few seconds of loading, it would come out of standby (amber light turns green) and my login screen would appear. Now it isn't even restarting back to bios. My monitor just hangs in standby mode forcing me to press the reset button on my computer. So basically I can't see anything, I just tried to hit alt+f3 like you suggested with no luck. Is there something I can do in recovery mode?

---

### Post by erginemr on 2008-01-12
The standby phenomenon is due to the fact that default Ubuntu boot splash resolution has been selected too high. You can read the following thread on this issue:
[http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216)

There, you should boot into recovery mode and try this to redeem the orange progress bar again:

> Originally Posted by Tony3286  View Post
I FINALLY GOT IT !!!!!

eye208 WAS RIGHT !! I was at the end of my rope so figured, what the heck, lets try it!
I didn't change any of the Horizontal or vertical setting in Xorg
BUT you do have to use sudo dpkg-reconfigure -phigh usplash
AFTER you change your settings in gksu gedit /etc/usplash.conf.

So for anyone that is having this "OUT OF RANGE" problem:

First thing to do is backup before editing you usplash.conf by using
sudo cp /etc/usplash.conf /etc/usplash.bak
then edit your usplash.config by typing gksu gedit /etc/usplash.conf and making sure
the values are
xres=1024
yres=768
Or what your monitor resolution is - mine, the only resolution that worked was 800x600
Save it, THEN use eye208's tip type sudo dpkg-reconfigure -phigh usplash

Reboot and see if the out of range disappears - if not go back to the link
Namanbagga has posted - you will be brought to a page titled 'Ubuntu 7.10 Bootup Resolution Problem"

Hopefully, you will be able to boot into Ubuntu after this change. If not, pressing Alt+F3 to see the boot/kernel messages will then work.

---

### Post by Travis Bickle on 2008-01-12
Ok, I just tried editing usplash.conf in recovery mode and I got this error: (gksu:4820): Gtk-Warning **: Cannot open display:

---

### Post by jnylen on 2008-01-13
> **Travis Bickle said:**
> Ok, I just tried editing usplash.conf in recovery mode and I got this error: (gksu:4820): Gtk-Warning **: Cannot open display:

I assume you're in a console-only environment during recovery mode?  Gksu[do] and gedit require an X server to be running, so you'll probably want to use 'sudo nano' instead of 'gksudo gedit' or whatever else.

---

### Post by Travis Bickle on 2008-01-13
First I just want to thank for your help. I successfully edited usplash.conf but to no avail. Ubuntu still doesn't load and my monitor shuts off after a few seconds, and still instead of going back to bios splash, system just hangs. I set the resolution to 800x600. If I could I would just reinstall Ubuntu, I saved all my work on a shared partition with the fat32 file system but like I said, ubuntu will not even load from cd. This is frustrating.

---

### Post by sandysandy on 2008-01-13
> **Travis Bickle said:**
> First I just want to thank for your help. I successfully edited usplash.conf but to no avail. Ubuntu still doesn't load and my monitor shuts off after a few seconds, and still instead of going back to bios splash, system just hangs. I set the resolution to 800x600. If I could I would just reinstall Ubuntu, I saved all my work on a shared partition with the fat32 file system but like I said, ubuntu will not even load from cd. This is frustrating.

Have u tried Super Grub Disk to boot your ubuntu partition.

regards

---

### Post by Travis Bickle on 2008-01-13
I download and burned an image of Super Grub Boot disk, read the documentation and tried both to fix MBR and boot into Ubuntu with no luck. Screen still flickers off and system just hangs with no activity. I'm beginning to lose hope & curious if it is my hard drive or some other hardware conflict. Is there a tool that I can use in windows environment to look for problems in Ubuntu such as resource conflicts or driver issues? Thanks again for the continued support.

---

### Post by erginemr on 2008-01-13
> **Travis Bickle said:**
> First I just want to thank for your help. I successfully edited usplash.conf but to no avail. Ubuntu still doesn't load and my monitor shuts off after a few seconds, and still instead of going back to bios splash, system just hangs. I set the resolution to 800x600. If I could I would just reinstall Ubuntu, I saved all my work on a shared partition with the fat32 file system but like I said, ubuntu will not even load from cd. This is frustrating.

Sorry to hear this. I assume you have also issued:
```
sudo dpkg-reconfigure -phigh usplash
```
after editing the usplash.conf file to put the changes into effect...

---

### Post by Travis Bickle on 2008-01-13
Ok, now I'm getting somewhere. Here is the error I get on the top of the screen..

[ 20.956131] kernel Panic -not syncing: UFS: unable to mount root fs on unknown-block (0,0)

On the bottom it says "kernel alive"

After doing some searching, it seems like a grub issue. Still searching for a fix with Ubuntu.

---

### Post by erginemr on 2008-01-14
That is some good news. Now, can you boot up from a Live CD, and try to mount your hard drive from Nautilus? If yes, then please post the contents of your /etc/fstab and /boot/grub/menu.lst files (but the ones inside your hard drive, not those from the Live CD).

---

### Post by Travis Bickle on 2008-01-14
I tried to boot from my Live CD and still the same thing happens, screen goes into standby mode. I can hear my optical drive working, loading up files then 1 beep and back to bios. I don't understand why this happens when using a live CD.
Maybe I can just open those files up in recovery mode?

---

### Post by erginemr on 2008-01-15
You initial post contains such a remark:
```
Ubuntu recovery mode works, memtest works and windows works.
```
Is this still the case, because I began to suspect the RAM slots:
[http://www.amptron.com/html/bios.beepcodes.html](http://www.amptron.com/html/bios.beepcodes.html)

Otherwise, I am out of my wits...:confused:

---

### Post by erginemr on 2008-01-15
Given the facts that:
* You used the Ubuntu Live CD to install Linux,
* You were able to use Ubuntu 64 bit for a while.

And after a trivial change in screensaver settings:
* You can no longer boot either from your hard drive or from the Live CD...

Logic tells me that there is definitely something recently broken in your hardware.:confused:

Possible candidates are:
1) BIOS Settings (loading to defaults might work)
2) Hard Drive (unlikely, Live CD would work)
3) CD Drive (unlikely, hard drive installation would work)
4) Memory (maybe)
5) Graphics Card (my best bet, since you can run Ubuntu in text-only recovery mode but not from a graphical environment)

focusing on 5th component:
- Assuming that it is not an onboard card, is its fan working?
- If you also have an onboard card, does Live CD load when you remove it and enable onboard graphics functionality from BIOS?
- Can you check its properties and benckmark it under Windows with a diagnostics tool, say using Sisoft Sandra or AIDA 32?

If I were you, I would also download and burn the Live CD of another Linux distro, say PC Linux OS:
[http://www.pclinuxos.com/](http://www.pclinuxos.com/)
and check whether it loads into the graphical environment.

---

### Post by Travis Bickle on 2008-01-15
I ran memtest all night with zero errors. It's not my graphics card, GPU runs great in windows. Hard drive and optical drives all work under my windows 64bit install. I did manually ajust my memory's timings to acheive 4-4-4-12 as advertised but like I just said, ram memtest with zero errors (memtest as an image on a cd). I will run memtest again and also try another linux distro. Thanks again for all your help, I really want my pc freedom back.

---

### Post by adrian15 on 2008-01-16
> **Travis Bickle said:**
> I tried to boot from my Live CD and still the same thing happens, screen goes into standby mode. I can hear my optical drive working, loading up files then 1 beep and back to bios. I don't understand why this happens when using a live CD.
Maybe I can just open those files up in recovery mode?

If I were you when booting from the live cd I will try to check the FX options to see if there is an option that disables the usplash option or to reduce the resolution settings.

Once the live cd works you can continue your quest.

adrian15

---

### Post by Travis Bickle on 2008-01-16
Last night I tried to boot from my live cd, 32bit. For some reason my screen doesn't go into standby mode using 32bit, I made it as far as a cursor then my pc just restarted once again. I now think this has something to do with a piece of hardware, it's just hard to narrow it down. I logged all my tweaks in bios so I will start reverting certain configurations back to auto or normal. I will start with my HT. When I initially installed Ubuntu, for some reason my bios had this setting at x1 giving my 200mhgz of HT when default is x5 (which is the setting auto gives) to give me a HT of 1000mhgz. Tonight I will try and bring it back down to x1 and see if I can boot back into Ubuntu. It's just strange that I can still go into recovery mode and just not GUI, be it HD install, or live cd both 32bit and 64bit.

---

### Post by Travis Bickle on 2008-01-17
I tried setting my bios settings all to default and I still cannot load Ubuntu, either by live cd or my hard drive installation. The only thing that works is Ubuntu recovery mode, windows xp professional and memtest. All my hardware checks out fine in windows, this is a real mystery.

---

### Post by Travis Bickle on 2008-01-18
I have a little more information, I can not longer boot into recovery mode and here is the errors I get:
VFS: Cannot open root device "VVID=8528f4da-0715-4f94-9869-c01463eb9773" or unknown block (0,0)
Please append a correct "root=" boot option: here are the available partitions:
[   24.393058] kernel panic-not syncing: VFS: Unable to mount root fs on unknown -block (0,0)

---

### Post by adrian15 on 2008-01-19
> **Travis Bickle said:**
> I have a little more information, I can not longer boot into recovery mode and here is the errors I get:
VFS: Cannot open root device "VVID=8528f4da-0715-4f94-9869-c01463eb9773" or unknown block (0,0)
Please append a correct "root=" boot option: here are the available partitions:
[   24.393058] kernel panic-not syncing: VFS: Unable to mount root fs on unknown -block (0,0)

This is so boring! :( 

From your live cd do a fdisk -l to know which it is your root partition.

Then edit your systems's /boot/grub/menu.lst so that the strings like:

root=UUID:8528f4da-0715-4f94-9869-c01463eb9773

read as:

root=/dev/sda3

where /dev/sda3 is your Linux root partition that you did find with the fdisk -l command.

If when you reboot Ubuntu is not able to boot then you will need to do a fsck to your Linux partition to fix it. (Ask other forum users for more details.)

adrian15

---

### Post by erginemr on 2008-01-19
It turns out that there is something wrong with your partition where Ubuntu has been installed for some unknown reason. This may also have affected how the Live CD works, that is to say, during the boot up process it may be scanning your hard drives and stalls when it encounters this error.

Anyway, in addition to adrian15's suggestion above, you may try to diganose (and fix if necessary) your Ubuntu installed partition by using a tool called "testdisk":
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is known to be very powerful in identifying and repairing hard disks and is OS independent, so you can install and run it from under Windows.

---

### Post by Travis Bickle on 2008-06-14
After months of just giving up, I re-traced my steps and found a solution. The problem was staring directly in my face all along. I received for christmas last a year a wireless optical mouse (microsoft 5000). I never enabled usb mouse support in the bios. It was during this time I built my new system & I never had to mess with the bios upnp for the mouse for my windows installation, it just worked with windows. I went into the bios and found the options to enable usb support for the mouse and keyboard. I enabled usb mouse support, rebooted into my Ubuntu 7.10 installation and everything worked again. I can't tell you how relieved I am that I finally got it working again and how I have to just laugh that it was such a simple solution. Yesterday I upgraded to 8.04 and just finished installing some new x64 applications and working on my new prefrences. Thanks to everyone who pitched in a helping hand.

---

