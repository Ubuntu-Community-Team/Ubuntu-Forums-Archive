---
title: "Brand New Dell Inspiron 530"
date: 2008-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jadeuru on 2008-06-17
I just received my brand new desktop computer and would like to dual boot it with Ubuntu Hardy Heron 64bit.
I would like to dedicate 100gb.
-
Now, I am assuming that all I have to do is boot the computer with the disk in the drive and follow the instructions to partition it and choose dual boot.
Is this correct?


Specs-
	Microsoft Windows XP Home Edition

Inspiron 530,Intel Core2 Duo processor E4600 (2.4GHz 800FSB) w/Dual Core Technologyand 2MB cache
  
128MB ATI Radeon HD 2400 PRO
1GB DDR2 SDRAM at 667MHz
500GB Serial ATA II Hard Drive(7200RPM)

OH, and HOWDY from a new Linux convert :)

---

### Post by upwinger on 2008-06-20
I just got a Dell Ispiron i530 S and it has a 32 bit processor, not 64. I cant load Ubuntu into it, I keep getting DRDY errors, ata2.00...
 hmmmmm agrivating being so puter stupid:mad:

---

### Post by sbooder on 2008-06-21
I have an Inspiron 530 32bit and I have just spent the night trying to load Ubuntu to it.

And I am now typing this from inside Ubuntu.

To get Ubuntu to load you have to go into the BIOS and change the SATA setting from IDE to RAID.

[COLOR="Red"]WARNING[/COLOR]: This works but two things to keep in mind, 1. I loaded Ubuntu from Wubi, and 2, If you change your SATA settings it will stop you booting into Vista (but changing the settings back to IDE dose let you boot into vista.

I am still trying to find a way of getting Vista on my Dell to accept the RAID setting, but with no success.

If anyone has any info on this bit of the problem, it would most welcome.

Simon.

PS, Ubuntu found my ATI Radion 2400 Pro and my Vigor 2600we router without batting the Phoenix/odd desktop heron eyelid.

It is so good to be mucking about in Ubuntu again...and I have absolutely no idea what I am doing!

---

### Post by gbrainin on 2008-06-21
If you add the all_generic_ide parameter to your boot line, you can use Ubuntu (8.04) with your BIOS setting in IDE mode.  You'll need to edit your grub menu.lst file to make the change permanent.

---

### Post by markharding557 on 2008-06-21
> **jadeuru said:**
> I just received my brand new desktop computer and would like to dual boot it with Ubuntu Hardy Heron 64bit.
I would like to dedicate 100gb.
-
Now, I am assuming that all I have to do is boot the computer with the disk in the drive and follow the instructions to partition it and choose dual boot.
Is this correct?


Specs-
	Microsoft Windows XP Home Edition

Inspiron 530,Intel Core2 Duo processor E4600 (2.4GHz 800FSB) w/Dual Core Technologyand 2MB cache
  
128MB ATI Radeon HD 2400 PRO
1GB DDR2 SDRAM at 667MHz
500GB Serial ATA II Hard Drive(7200RPM)

OH, and HOWDY from a new Linux convert :)

welcome and i recommend using the 32bit to start because there can be more problems to overcome on 64bit

---

### Post by eruptionjoojo on 2008-06-21
I 'm Using DEll Inspiron 530 desktop with specification's:-
1gb ram(667 mhz)
160gb sata hdd(7,200 r.p.m.)
intel dual core e2160
intel g33/p35 chipset built motherboard
13 in 1 media card reader with bluetooth
media centre with remote control
i have been using ubuntu(32 bit) 7.10 gusty gibbon................. but,culdn't help it because i culdn't find d appropriate video driver's and also the dell-usb multimedia keyboard driver's............thus,ma multimedia keys don't wrk properly.............the media centre remote doesn't work as well..the media cards cn't be read.....
r u facing the same problem.........if not let me know...............i m having windows vista home premium................trio booted with windows xp n ubuntu 7.10(gusty gibbon)......

---

### Post by upwinger on 2008-06-21
where do you find the grub/menu.lst file?
And is the code: "all_generic_ide" complete? I've seen other posts suggesting code: "all_generic_ide floppy=off irqpoll" !!!
I want to try and get this working so I dont have to use Vista! Please help!!

I have another Dell Inspiron 6000 laptop that runs the live CD just fine, but as soon as I try to install a permanent onto the hd it locks up every time on the partition bar at 5%. I cant figure out what needs to be done to get it to load, but if I run the disc on "load without changing your computer" it boots up and works perfectly.

I have another Dell Inspiron laptop 600m and it loaded and runs perfect with no problems yet.

---

### Post by konungursvia on 2008-06-21
Ubuntu is so efficient you won't need 100 Gb on its side, more like 30 is plenty. I'd create a separate ntfs partition of 70 Gb as well, for your music and movies etc. That way both OS's can access those files.

---

### Post by gbrainin on 2008-06-22
> **upwinger said:**
> where do you find the grub/menu.lst file?

It's usually at /boot/grub/menu.lst but keep in mind that you'll have to sudo in order to edit it.

> And is the code: "all_generic_ide" complete? I've seen other posts suggesting code: "all_generic_ide floppy=off irqpoll" !!!

Well, on my 530, the all_generic_ide parameter is all I need, but it's always best to check.

Before you go changing your menu.lst file, why not experiment?  As your computer is booting into Ubuntu, you should have a boot menu (you may need to press Esc to make the menu visible).  From there, you can edit the boot parameters on a one-time basis.  Then after you find the set of commands that work on your machine, you can make it permanent by editing menu.lst.

Also, before you edit menu.lst (or any other configuration file), make a backup first!  If all else fails, you can always go back to the old version, in case things get too messed up (which occasionally happens to even the most experienced of us).

---

### Post by sbooder on 2008-06-22
I have just uninstalled Ubuntu from the Wubi instillation because I want it on my HDD in its own partition, I have sneaky feeling Vista slows it down ( I may be imagining it).

This is my problem though.  I have Vista and XP dual boot already, so I used the shrink tool in Vista disk manager and created another partition of 30GB for Ubuntu.  I put it the Ubuntu Live CD and chose the Install option (with F3 UK) and started the install.  

All is OK until I get to the Ubuntu Partitioner.  There is nothing wrong with the Install or the partitioner, it is me, because my HDD is 320GB, I can not use the largest continues free space option because the Vista partition still has 180GB of free space, so I have to use the manual option, and being a total Linux nonce; I do not know what all the options mean, like beginning and end, or Linux swap...and so forth.

So what I need to know is, is there a set of idiot instructions for manual partition, because I can not seem to find them anywhere?
Thanks for reading my ramble!

---

### Post by gbrainin on 2008-06-22
Ah, I missed the fact that you were using Ubuntu through Wubi.  If you want to set up the proper dual boot, I would start with these instructions: [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot").  If there are things there you don't understand, try searching on this forum or ask again, and someone will probably be able to help.

---

### Post by anibalrojas on 2008-06-22
Edit the kernel entry in the grub starup menu and add the pci=nomsi parameter to the end of it.

--
Aníbal Rojas
[http://laracaraoscura.com](http://laracaraoscura.com)
[http://anibal.rojas.com.ve](http://anibal.rojas.com.ve)

---

### Post by eruptionjoojo on 2008-06-22
Can anybody plzz.....provide me the dell inspiron 530 desktop usb-multimedia keyboard derivers of intel g33 motherboard...????

---

### Post by secdroid on 2008-06-23
I am considering the Inspiron 530n, but like to read the manual before buying.  Weird, I know!  :)

Need to know things like whether it will accept a PS/2 kbd connector (from my KVM switch).

It used to be easy to download manuals from the Dell support site, but I can't seem to find a downloadable 530 manual.  Can anyone point me to a link?

(The Dell sites really suck, compared to the old days.  No graphics with Firefox 1.5/Ubuntu 6.06 LTS - OK w/ Opera 9.27, excessive/slow flash, must jump through multiple hoops to do anything.  A shame.  They used to have excellent, fast sites.)

---

### Post by danbodoh on 2008-06-23
Sorry, no ps/2 keyboard connector.  When my 530 came, I had to give up my 22-year-old keyboard that I bought at a hamfest in college and then replaced one of the dead TTL chips.

Progress...

---

### Post by secdroid on 2008-06-23
> **danbodoh said:**
> Sorry, no ps/2 keyboard connector.
Thanks for the info.  Don't know if one of those PS/2->USB adapters would work to resolve this.  My other computers & KVM switch are PS/2.

I'd like to support Dell 'cause they support Ubuntu, but...  Everyone else (except Apple) seems to support PS/2 connectors.

BTW, Dell, have you considered the **disadvantages** of making your support forums unviewable by unregistered users?  (Not unpostable; completely unviewable.)  One more way your sites make users jump through hoops.  One of many ways!  Might that cost you sales?

FWIW, I looked at --
[LIST]
[*]HP/Compaq refurbs from Newegg.  Found tech info and manuals on HP site.  Even said **which** mobo each model used.  Could pick models using Asus and exclude ECS.  Ugly site, but very useful.  
[*]Gigabyte mobos.  Tons of info on their site.  Easy.
[*]Asus mobos.  Tons on info on their site.  Easy.
[*]Dell outlet.  No low priced 530s.  No site graphics with Firefox.  Dell sites are the **only** site to ever give graphics problem with Firefox 1.5/Ubuntu 6.06 LTS (patched to-date).
[*]Dell open store.  No graphics.  Hard to find.    
[*]Dell support.  Can't get manual.  Forums unviewable.  
[/LIST]

Sorry, Dell.  Your site used to be one of the very best for sales and technical info.  You just ain't what you used to be.  Hope you fix it.

---

### Post by gbrainin on 2008-06-23
> **secdroid said:**
> It used to be easy to download manuals from the Dell support site, but I can't seem to find a downloadable 530 manual.  Can anyone point me to a link?

[http://support.dell.com/support/edocs/systems/inspd530/]("http://support.dell.com/support/edocs/systems/inspd530/")

(No registration required.)

---

### Post by sbooder on 2008-06-27
As someone new to all this, where in the menu.lst do I enter the line: "all_generic_ide" complete? please.

I am no longer using Ubuntu through Wubi, I have it loaded on a partition.


Thanks.

---

### Post by gbrainin on 2008-06-27
Switches like all_generic_ide go on the end of the line that begins with "kernel."  There may be several of these.

---

### Post by secdroid on 2008-06-28
> **gbrainin said:**
> [http://support.dell.com/support/edocs/systems/inspd530/]("http://support.dell.com/support/edocs/systems/inspd530/")

(No registration required.)

Excellent manual.  Better than HP/Compaq (and most other brands.)  Thanks for the tip.

It turns out that you can enter "inspiron 530 manual" in the keyword search box at the top of the home page and then back up the URL (from the .html chapters) to find the download links.  It's a shame that it isn't easier to find.  

Tried the ordering process.  Unless I'm doing something wrong, the 530n only comes with the Pentium E2180.  If I want a Core 2 Duo, I have to buy Vista on a 530.  Only $10 over the price of Ubuntu (identically configured).

Gee, Dell, I want to love ya, but your heart doesn't seem to really be in this Ubuntu thing...  :confused:

---

### Post by gbrainin on 2008-06-28
The hardware options with Ubuntu do keep changing, and with no obvious (to this outsider) rhyme or reason.  I bought my 530n last year with a Core 2 Duo, Ubuntu preinstalled.

---

### Post by RedRat on 2008-06-29
> **gbrainin said:**
> The hardware options with Ubuntu do keep changing, and with no obvious (to this outsider) rhyme or reason.  I bought my 530n last year with a Core 2 Duo, Ubuntu preinstalled.

Same here. I got mine in January. came with 7.10 preinstalled.

---

### Post by bernardfrancois on 2008-07-13
I also have a dell inspiron 530. It came with windows vista pre-installed on a raid-1 configuration.

Some of my experiences with it:
[LIST]
[*]This thread helped me to install ubuntu next to the existing vista installation on the raid-1 configuration:
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)
This was quite tricky, so I strongly advise anyone trying this to take a full backup first.
[*]This thread helped me to get the bluetooth keyboard and mouse to work (I temporarily needed a usb mouse+keyboard to install it offcourse):
[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)
[*]I didn't get the sound blaster X-Fi sound card to work yet; at the time I installed linux on it there was only a beta driver for 64-bit linux. I just checked creative's site and now they also have it for 32-bit linux.
I will probably use the following thread to get it to work:
[http://ubuntuforums.org/showthread.php?t=571656&highlight=Xtreme+Gamer](http://ubuntuforums.org/showthread.php?t=571656&highlight=Xtreme+Gamer)
[*]I just tested if the memory card reader worked, and it did for a sony memory stick pro (I don't have any other memory sticks, so I couldn't test further).
[*]The remote that came with the computer doesn't work. It comes with a usb infra red receiver and seems to be designed for windows media center. **Anyone who got this to work?**
[/LIST]

---

### Post by bernardfrancois on 2009-04-13
Update:

[list]
[*] I still didn't get the Soundblaster X-Fi to work, but I'm getting close. Many people already got it to work in 8.10, but I'd like to stay with 8.04 (LTS) for the moment. This is the thread: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=870001](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=870001)
[*] For the bluetooth keyboard and mouse, you don't need to install anything any more. All I have to do is to unplug/plug the bluetooth stick when I'm at the log-in screen. I can live with that.
[*] The firewire connection works. I succesfully used it to capture video from a sony camera.
[*] I still don't have the remote working, but I didn't try to make it work...
[/list]

---

### Post by Student Driver on 2009-08-10
Anybody know how to get the built-in Bluetooth module to come up?  I have Bluetooth working in both my Dell Minis and other systems (usually using Blueman), but for some reason this module isn't coming up.  It's part of the media card reader (which is working fine).

---

