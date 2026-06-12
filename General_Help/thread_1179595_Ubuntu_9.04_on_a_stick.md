---
title: "Ubuntu 9.04 on a stick"
date: 2009-06-05
forum: General Help
---

### Post by Prem Rajendran on 2009-06-05
Hey guys,

Can anyone tell me if running ubuntu on a usb stick will stuff up the usb because of the constant reading and writing

And how do i actually set this up. Not running live cd but actually installing and running entire os on a stick.

Thanks in advance :D

---

### Post by LMZKJ on 2009-06-05
I just set this up a couple of days ago.  Look for pendrive persistent USB on google.  There are pretty good tutorials to follow.  As for whether the OS will be slow because of the read/writes, I haven't noticed.  There is a Windows install on the hard drive, but I prefer to boot and run from the USB.

---

### Post by Prem Rajendran on 2009-06-05
just to clarify 

I didnt mean to ask if it will run slow on a usb 

but if it will cause damage to the usb

---

### Post by LMZKJ on 2009-06-05
USB thumb drives do have a limit on the number of read/writes that they can do.  That said, the number is very high and the USB keys are around $10 for 4 GB in the states. It should work well for a rather long period of time.

---

### Post by Prem Rajendran on 2009-06-05
ahh k 

thanks for clarifying

now just need to find a tutorial on how to install

---

### Post by Meow27 on 2009-06-05
download the latest ubuntu iso

make sure your usb is formatted fat32 not fat16 

make sure you add a memory file (casper-rw) make it as much as you need (maximum 4 gb)

remember this is a live cd, so it should do TOO many writes.

use the usb cd install tool 

system->administration->usb startup disk creator tool

---

### Post by anjilslaire on 2009-06-05
Easy to do from within Ubuntu itself:
From Ubuntu 8.10 or newer:
System >Administration>Create A USB Startup Disk
1. plug in your usb stick
2. run the tool
3. point it to your 9.04 ISO as the source, and your usb as the destination.
4. When finished, you're all set.

---

### Post by Meow27 on 2009-06-05
if you are using the memory file, booting is going to take considerably longer, also depending on the size of the memory file

also i recommend you getting a high speed usb for these kinds of things, (somthing like 200x so it can transfer ~27 megabytes/sec)

edit- when you turn on your computer, press the boot manager button, usually f12. keep pressing whatever the key is so you can boot from your usb, not from the harddisk

---

### Post by blueridgedog on 2009-06-05
> **anjilslaire said:**
> Easy to do from within Ubuntu itself:
From Ubuntu 8.10 or newer:
System >Administration>Create A USB Startup Disk
1. plug in your usb stick
2. run the tool
3. point it to your 9.04 ISO as the source, and your usb as the destination.
4. When finished, you're all set.

Does this result in a persistent setup?  I assumed (bad idea I know) that it was an install method not a persistent "use it and save files" type of thing.

---

### Post by anjilslaire on 2009-06-05
Yes, it is persistent. During the process, it will let you designate how much space you want to allow on the usb for persistent settings.

It allows a persistent environment, as well as an installer.

---

### Post by Prem Rajendran on 2009-06-06
Thanks for all the help guys 

If there isnt already one maybe you guys 

could use this thread to post all your problems 

that need solving with regards to ubuntu on a stick

---

### Post by colau on 2009-06-06
> **anjilslaire said:**
> Easy to do from within Ubuntu itself:
From Ubuntu 8.10 or newer:
System >Administration>Create A USB Startup Disk
1. plug in your usb stick
2. run the tool
3. point it to your 9.04 ISO as the source, and your usb as the destination.
4. When finished, you're all set.
Does unetbootin work similarly like USB Startup Disk?:)

---

### Post by anjilslaire on 2009-06-08
Yes, I believe it does. Not sure if it's persistent, but it does allow for installing/booting from a usb.
If you're running 8.04 or earlier that doesn't include this, you can install it by
```

sudo apt-get intstall usb-creator

```

---

### Post by Krupski on 2009-06-08
> **Prem Rajendran said:**
> Hey guys,

Can anyone tell me if running ubuntu on a usb stick will stuff up the usb because of the constant reading and writing

And how do i actually set this up. Not running live cd but actually installing and running entire os on a stick.

Thanks in advance :D

Ubuntu runs very nicely from a USB stick. And, since it caches what it does in ram, you won't be CONSTANTLY reading and writing the USB drive (i.e. the USB ports won't get saturated).

As far as "how to install"... just boot up the install disk, insert your USB drive and use manual partitioning to select and partition the USB drive.

As far as Ubuntu is concerned, the USB stick is just "another drive". Install to it and you're all set.

---

### Post by Duckslammer on 2009-06-08
> **anjilslaire said:**
> Yes, it is persistent. During the process, it will let you designate how much space you want to allow on the usb for persistent settings.

It allows a persistent environment, as well as an installer.

I have tried every method I can find on the net to make a persistent thumbdrive system, and none of them save the files back to the thumbdrive.  In other words, they aren't persistent.

I have just reloaded xubuntu 9.04 for the umpteenth time and the menu option for loading the usb drive no longer exists.  Where did it go, how do I get it back?  (I have noticed this about xubuntu - different things load and/or work at different installs, and never everything works all the time.)

Currently I'm playing with unetbootin - makes a fine Live thumbdrive, but like every other method, files updated are not saved back to the thumbdrive - it's not persistent.  

I was wondering if maybe it was how I was rebooting: reboot, init 6, shutdown -r now, holding the power button - none make any diff.

Reading that everyone else in the world can make this work except me is extremely frustrating.

---

### Post by salvachn on 2009-06-08
An easier way is here:
[http://tinyurl.com/pendriveubuntu](http://tinyurl.com/pendriveubuntu)
And it is persistent, yes.

---

### Post by Duckslammer on 2009-06-08
I made another install using usb-creator.  When I boot it, I get the "boot:" prompt, hit enter, screen goes grey, the r/w access light on the stick flashes for a few secs and nothing happens.  if I press any key, I see an ansi graphics box quickly scrolling up the screen as if the enter key were jammed.  But no boot.  I have reloaded twice and double checked the md5sum of the iso.

---

### Post by Duckslammer on 2009-06-08
> **salvachn said:**
> An easier way is here:
[http://tinyurl.com/pendriveubuntu](http://tinyurl.com/pendriveubuntu)
And it is persistent, yes.
I tried this, it is not persistent.

---

### Post by Prem Rajendran on 2009-06-09
Persistant?

What does that mean?

---

### Post by GeorgeVita on 2009-06-09
Hi, I am using only Live/Persistent/Installed 9.04 (and puppy 4.2) into USB sticks and SDHC cards with my EeePC1000H (Hard Disk removed!). Two days ago I made some speed tests on various formats on HardDisk (installed), SD, SDHC and USB flash concluding to faster results with **ext2**.

Speed Check: [http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt)
Graph: [http://acomelectronics.com/GeorgeVita/extPoll.jpg](http://acomelectronics.com/GeorgeVita/extPoll.jpg)

Notes: all tests done on the 1000H, big files=25pcs total=1.2GB, small files=28723pcs total=1.2GB, HardDisk=Toshiba MK6037GSX 60GB sata II 2.5", SDHC=SanDisk Extreme III 20MB/s

As I had to try it 10-15 times (format/install/change media) the only sure procedure was:
- If your system has a CD-drive: Boot a live CD, install to the USB/SDHC media setting manually the partition to ext2. The swap file is about 380MB (I don't know if you can remove it).
- If you are using a LiveUSB stick (ex. a netbook with no CD-drive): _burn it again_ using the original .iso because some files/parameters remain there from previous tries, resulting to a BAD install. That means that the Live USB is persistent or semi-persistent...

If your system has an SDHC reader, you may _try_ if this reader is fast enough to use it (my reader has a maximum of 15-17MB/s so I do not need a more expensive 30MB/s card). Most times a USB flash drive is faster but it can be removed accidentally. SDHC cards most times are "into" reader. "Life expectancy" of the media could be some years so you have to backup your data. Do a real "benchmark" by timing a large copy (ex. a very big directory) from/to the same formated ext2/fat32 media:

**time sudo cp -r /media/mySDHC/G_various/* /media/mySDHC/G_var** (destination directory must exist)

Regards,
George

---

### Post by GeorgeVita on 2009-06-09
Hi again,

I just finished an application note (plain text):
**HowTo install Ubuntu 9.04 to a USB or SDHC disk (flash memory) on an Asus EeePC 1000H**
[http://acomelectronics.com/GeorgeVita/G904_USB_sdhc.txt](http://acomelectronics.com/GeorgeVita/G904_USB_sdhc.txt)

I am trying to cover 3 subjects (as there is no CD drive to EeePC):

1. Check the speed of the USB/SDHC disk that will be used for the installation
2. Make an Ubuntu 9.04 LiveUSB
3. Install 9.04 desktop on USB or SDHC disk

The speed-check only: [http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt)
The speed results graph: [http://acomelectronics.com/GeorgeVita/extPoll.jpg](http://acomelectronics.com/GeorgeVita/extPoll.jpg)

Regards,
George

>>> **Prem Rajendran**
(**Persistent**: In computing, a persistent data structure is a data structure which always preserves the previous version of itself when it is modified, [http://en.wikipedia.org/wiki/Persistent_data_structure](http://en.wikipedia.org/wiki/Persistent_data_structure))

---

### Post by sendblink23 on 2009-06-09
"GeorgeVita"
Sorry but your instructions.. actually *does not work* (tested it exactly the same way yesterday 4 times *Ubuntu 8.10 / Ubuntu 9.04*) it will not boot from the USB alone from F12 or ESC, it will always need to read the Internal Hard Drive for it to boot

Why... simple Grub will always be installed in the Primary Hard Drive

The ONLY way to install Ubuntu OS (not as a live cd) forcely only at a USB Drive, is by Removing or Disconnecting the internal Hard Drive... 

That way you can install it as normally by simply selecting the only the HD that would be visible.. which will be the USB Flash Drive

Trust me I've done it so many times.. and It Ruins the Installed OS in your Primary Hard Drive .. all because of Grub

There should be a way of simply being able to custom adding the Grub(where you want), during the installation Process of the Live CD, and this issue should be resolved

*All the People that Mentioned This*
 Originally Posted by anjilslaire  View Post
Easy to do from within Ubuntu itself:
From Ubuntu 8.10 or newer:
System >Administration>Create A USB Startup Disk
1. plug in your usb stick
2. run the tool
3. point it to your 9.04 ISO as the source, and your usb as the destination.
4. When finished, you're all set.


It will not install Ubuntu as a OS, just as a LIVE CD .. with a partition to save Data... you will always boot as a Live CD.. and when Doing Updates ... when it comes to Linux Headers.. they will always give Error.. simply because its a LIVE CD install on a USB  ..  But yes everything else is Updated as normal and it works as a full Ubuntu OS.. just new Linux Header will not update

In other words.. it will install the OS & Boot Only from a USB.. but it will always still be simply a Live CD version

---

### Post by dcstar on 2009-06-09
> **Duckslammer said:**
> I tried this, it is not persistent.

When I create a "Live" USB drive in 9.04 using the USB Startup Disk Creator, I couldn't get the persistence working, so I did this workaround:

[LIST=1]
[*]Use the Partition Editor to wipe your USB drive and then create a FAT32 partition  on it (I used 3GB so I can store stuff on it, 700MB minimum if you don't need to do that).
[*]Use the Partition Editor to create an EXT2 partition on the USB labelled "casper-rw" (it is vital that this name is exactly used) to store updates/persistent data (1GB minimum recommended)
[*]Use the USB Startup Disk Creator to make the drive using the FAT32 partition you created previously
[*]Once created, replace the default FAT32 partition syslinux/text.cfg file with the following:
[/LIST]
```
default live
label live
  menu label ^Run Ubuntu from USB drive in Persistent Mode
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
label check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  noprompt boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80
```

Now I have a USB that boots 9.04 and stores my settings and software updates.

---

### Post by sendblink23 on 2009-06-09
Guys here is the easiest method to install Fully Ubuntu OS on a USB Hard Drive or Flash Drive

Super Simple - *THIS IS THE CORRECT WAY* Using the Normal GUI Installation

Boot with Live CD

Connect USB Device (Once detected right-click "unmount")

Choose Install from Desktop

After the language, keyboard etc.. and enter the choose where to install Ubuntu area, Choose use Guided Entirely and select the USB Device HD

Do all the normal filling username, password... and when you get to the final Page Where you choose to begin the Process *Click the Button Advanced*

In there choose where to install the Boot Grub - Just select the USB Device HD and Ok

And confirm the Instalation Process


THERE YOU GO DONE! Full Ubuntu Install on a USB Device Hard Drive / Flash Drive

*no coding, or partitioning.. or casper thingy .. Just Regular Install GUI of Ubuntu Live CD

---

### Post by dcstar on 2009-06-09
> **sendblink23 said:**
> 
.........
THERE YOU GO DONE! Full Ubuntu Install on a USB Device Hard Drive / Flash Drive

*no coding, or partitioning.. or casper thingy .. Just Regular Install GUI of Ubuntu Live CD

And you end up with an OS **that will kill your USB device prematurely** because it assumes it can do as many Write cycles as it likes.

As the OP pointed out, he wants an install that **does not** kill his hardware.

The UNR install is tailored to SSD devices by minimising writes and using RAM, the USB persistent Live install is also suitable because of the use of RAM for temp storage.

---

### Post by mcretzu on 2009-06-09
Thanks, it works!

---

### Post by blueridgedog on 2009-06-10
> **dcstar said:**
> 
The UNR install is tailored to SSD devices by minimising writes and using RAM, the USB persistent Live install is also suitable because of the use of RAM for temp storage.

Where did you get that information?  I have been digging to find out what the difference is in the UNR.  See:  [http://ubuntuforums.org/showthread.php?t=1180373](http://ubuntuforums.org/showthread.php?t=1180373) 

I was ultimately told that the only difference was the launcher and the full screen windows.

The UNR needs a special kernel and write avoidance techniques, but I think it lacks them.

---

### Post by Mighty_Joe on 2009-06-10
> **dcstar said:**
> And you end up with an OS **that will kill your USB device prematurely** because it assumes it can do as many Write cycles as it likes.


If wear and tear are a worry for you, there are steps you can take to lighten the load: like forgo the swap partition and move logging and caching to tmpfs.  I use the instructions [here]("http://beastie.cs.ua.edu/cs150/configuration.html") to configure a flash drive install and it works great.

---

### Post by GeorgeVita on 2009-06-10
Hi,
**sendblink23** was right!
I had formated my H.D. so it was easier to make the installation to the SDHC. Today I installed 9.04 UNR on my hard Disk and later managed to install another copy to a USB disk. Now I can boot one from three, sorry **one from five** drives alternatively.
[img]http://acomelectronics.com/GeorgeVita/multiBoot.jpg[/img]
Above shown ability to boot from: HD 9.04 UNR installation, 9.04 LiveUSB, my recent try (USB), my 1st one (USB), my fully updated working 9.04 (SDHC). Believe me they are all working. I agree this is useless as most are the same version. Also I did not calculate the "life expectancy" of the media but other posts on this thread have some ideas to try.

Today I faced many problems till success, so debugging must be done.

One issue was a new SanDisk cruzer which stucked during formatting (let's assume it was a random reason). Another weird state was at "prepare partitions". It automatically points to the first line (sda Hard Disk) after every partitioning job. An unwanted task to repartition sda appeared at the resume so I revised my selections (GParted). Also there is an "Advanced" selection where you can confirm that the Boot Loader must go to sdb/sdc.

>>> Is GParted well debugged?

About Grub: In my 2nd USB installation (cruzer) Grub has extra options to "boot from another O.S. on sda (Hard Disk)"! This must be what **sendblink23** mentioned. The other Grub on the Hard Disk did not changed. Is the selection into "Advanced" option that worked? Another option can skip the Grub installation (I did not check it).

Concluding these are just some ideas to try. I do not fear about breaking the SDHC as it is more importand to have there a "stable" condition and try Alpha 2 on my hardisk (tomorrow!).

Regards,
George

---

### Post by Handssolow on 2009-06-10
I've installed Ubuntu persistent on both USB sticks and SD memory in a USB adaptor. I've used both the pendrivelinux and Ubuntu's own methods. I've not researched this widely but isn't there an issue over time about using the update manager on this type of USB persistent booting?

For example, Ubuntu 9.04 on my 8G usb stick is showing vfat 22% used but squashfs is full at 100%. I've another install on a 2G SD chip and effectively it's not usable until I start afresh, I can no longer fully update the OS.

My 8G stick still works but for how much longer with squashfs at 100%?

---

### Post by salvachn on 2009-06-10
Do you mean your squashfs file is 100% full, i.e 8GB large??

---

### Post by Handssolow on 2009-06-11
Booting from my 8G stick, System Monitor reports 

Device /dev/sdb1 Directory cdrom Type vfat Total 7.5 GiB Free 5.8GiB Available 5.8 GiB Used 1.7 GiB
Device /dev/loop0 Directory /rofs Type squashfs Total 675.1MiB Free 0 bytes Available 0 bytes Used 675.1 MiB

It appears that with time repeated use of Update Manager adds to squashfs but older stuff isn't removed so it fills up. It was a few weeks back I last looked into this but I haven't yet seen an answer. Rather than being able to run Ubuntu from a USB stick with a username and password, currently it seems that main purpose of the USB stick is help install Ubuntu to a sytem which doesn't have a CD drive.

---

### Post by GeorgeVita on 2009-06-11
Hi **Handssolow**,
trying a boot from my all media, **/dev/loop0 Directory** exists only to LiveUSB and it is Full (100%).
I have not update this USB LiveUSB stick.

**Below shown**: the LiveUSB running now (Kingston 8GB), 2x full 9.04 installations on USB stick (SanDisk 4GB and Transcend 8GB), my main 9.04 installation on SDHC (SanDisk 8GB 20MB/s) and my testing install on HardDisk.
[IMG]http://acomelectronics.com/GeorgeVita/multiBootLiveUSB.jpg[/IMG]

This /dev/loop0 may be a RAMDRIVE? It exists also when running from a LiveCD.
Regards,
George

P.S. I will not bother you with other photos! The last one here shows all tested/bootable drives attached to my 1000H.

---

### Post by Mighty_Joe on 2009-06-11
> **Handssolow said:**
> I've not researched this widely but isn't there an issue over time about using the update manager on this type of USB persistent booting?


I can't find a reference, but I remember seeing that one cannot update the kernel on the Live USB because the "regular" kernel (as opposed to the Live CD kernel) doesn't have squashfs.  

> **Handssolow said:**
> 
It appears that with time repeated use of Update Manager adds to squashfs but older stuff isn't removed so it fills up.

That is how I understand it.  Rather than replacing updated packages (like in the regular install), new packages have to occupy the casper-rw partition, so there's a net increase in disk use.

---

### Post by thinkcow on 2009-06-11
> **GeorgeVita said:**
> 
This /dev/loop0 may be a RAMDRIVE? It exists also when running from a LiveCD.


/dev/loop0 is the original .iso file of the Live-CD, mounted as a read-only device {That is also why it shows as being mounted in /rofs [/ReadOnlyFileSystem] by default} ;)

In Linux you can always mount an .iso cd-image as a directory, which makes it easy to {for example} replace config files on the CD you later burn from the .iso. 
Just "mount -o loop nameofisofile.iso /mnt/nameofdirectory", replace the files you need adjusted then "umount /mnt/nameofdirectory".
This way you can customize a live-cd so that even though your machine has hardware that is not supported by the standard Ubuntu-Live/Install CD, you can use the Live-CD with a fully-working system. :KS

[edit/addition: My advise is to boot with a live-usb-stick, then install to another USB-stick/SD/SDHC Card [Don't forget to tell the installer to install GRUB to the USB/SD you install to, or do not install GRUB at all!] That way you will not have the loopdevice {So it saves space} and you will have no troubles updating/upgrading.  :twisted:]

---

### Post by GeorgeVita on 2009-06-11
Many thanks **thinkcow**!

This is '**learning through a post!**'

Regards,
George

---

### Post by Handssolow on 2009-06-11
Run this past me again please.
So I'm booting from a stick with persistent Ubuntu 9.04 which I've customised and updated, then using Administration>USB Startup Disc Creator I'm hoping to create my customised OS on another USB (or SD) memory stick/device to refresh my system files.

Only it's asking me where the iso is which it needs. I could download one but then it would be a completely new install without any of my personal files, wifi or bluetooth settings.

At we say, have I missed something?

---

### Post by thinkcow on 2009-06-12
> **Handssolow said:**
> Run this past me again please.
So I'm booting from a stick with persistent Ubuntu 9.04 which I've customised and updated, then using Administration>USB Startup Disc Creator I'm hoping to create my customised OS on another USB (or SD) memory stick/device to refresh my system files.

Only it's asking me where the iso is which it needs. I could download one but then it would be a completely new install without any of my personal files, wifi or bluetooth settings.

At we say, have I missed something?

Unfortunately you did not miss something. Most recipes out there that help you create a "persistent stick", do still work with the full-live-cd in the background. What they do is that they save the changes you make {settings/config} into run-scripts that get run after booting the Live-cd {So first they start as if you were running from the Live-cd and after that they do the adjustments giving you the impression that it adjusted the Live-CD}. In my opinion the best way to go is to make a "normal full install", using an USB-stick/SD-card instead of the harddisk/builtin SSD that you would use if you wanted to replace the OS of your machine.

The USB Startup Disc Creator only makes an USB-stick into a bootable CD which then can be used as an install medium. It is mostly meant for people wanting to upgrade to a newer/different version which do not have a CD-burner or do not want to waste a CD-R {As mostly the CD is only used for the installation and the next time you are going to install you will probably want the newest version anyway which means that you then create a CD-R with the newest version and often never use that CD again}. 
The tool {as I understand it} has been integrated to save you the hassle you would have if you did the same process yourself [You then have to format the stick, make it bootable, install the correct bootstrap on it, create a loop-device to be able to copy all the files within the .iso file to the stick etc].

In the past the Live-CD and the install CD were two different CD's which made it clearer that if you run off the Live-CD you can not adjust it. The modern methods of making the Live-CD persistent on a stick/SD give you the idea of having done a real install, but in most cases you will eventually run into problems if there are major changes. 

An example of this is if there is a new version of Ubuntu: If you have made a persistent stick with the Ubuntu 8.10 Live-CD as the base and want to upgrade it to 9.04 in the normal way, the persistent stick would then first boot the 8.10 Live-CD, remove everything from memory that has been removed in the new version and add everything to memory that is new in 9.04 ... this because it can not change the Live-CD image of 8.10 which is only mounted as read only.

So if you plan to use your USB-stick/SD card for a longer time or even permanently, my advise is to take the time once to make a full install which you then can normally upgrade/update/adjust [I know it takes longer to do this than to make a Live-version persistent, but in the long run it will save you hassle as the persisten Live-version will "break" at major updates].

:oops: Please excuse the lengthy answer. I hope it clarifies things and saves you time [In the past it has cost me many a day to try to "fix" broken persistent-Live-versions, which in most cases I ended up having to reinstall to get working again ](*,) ]

---

### Post by Handssolow on 2009-06-15
Thanks thinkcow great help, I'm not sure why your advice isn't more widespread for those who want to just boot from a memory stick.

I did a normal install of 9.04 on my 8GiB memory stick. To avoid any mistakes I first disconnected my hard drive and booted from the Ubuntu iso setup CD then instead of choosing the option of USB Startup Creator simply installed from the desktop's shorcut. As there was no HD connected only my memory stick, I could relax. I've got Bluetooth and wifi back and configured but not yet 3G mobile broadband.

---

### Post by olliraa on 2009-06-18
I (also) have a problem with the persistency of a live version installed on a usb-stick. In practice nothing is persistent :( What I need this for is the following:

An arcade-cabinet running Xubuntu 9.04. I'd prefer a usb-stick, because only thing I have to install is Nvidia restricted drivers and Mame and the roms. So I'd basically never want to update the software. But unfortunately I cannot even make a simple launcher on the desktop persistent :( I followed [this]("http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/") guide at pendrivelinux.com. I also checked th text.cfg (that was mentioned a few posts ago), but I already have the "persistent" there.

Now that you know the reason for my "desire", are there any more reasonable options available? As I said, Id rather not use a real harddrive.

---

### Post by mixmaster on 2009-06-18
> **olliraa said:**
> I (also) have a problem with the persistency of a live version installed on a usb-stick. In practice nothing is persistent :( What I need this for is the following:

An arcade-cabinet running Xubuntu 9.04. I'd prefer a usb-stick, because only thing I have to install is Nvidia restricted drivers and Mame and the roms. So I'd basically never want to update the software. But unfortunately I cannot even make a simple launcher on the desktop persistent :( I followed [this]("http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/") guide at pendrivelinux.com. I also checked th text.cfg (that was mentioned a few posts ago), but I already have the "persistent" there.

Now that you know the reason for my "desire", are there any more reasonable options available? As I said, Id rather not use a real harddrive.

Forget all the old guides.  Just use the tool under 
system->admin->create USB startup disk

Just make sure you allocate some space to save files!

As a tip, use remastersys to create a backup iso and use that instead of the livecd iso.  That way you will get a clone of your normal desktop setup rather than having to recustomise your desktop on the usb stick.

---

### Post by olliraa on 2009-06-19
Ok, thanks :) I tried that, but when I boot from usb I get thown to the unfortunately infamous "busybox" :( So, there's something weird goin on...

Could it be a possibility to install Ubuntu as a standard install to the stick and then set all logging and swappiness to 0 (I really don't need swap at all with my setup). This should reduce the writing to the stick dramatically, right?

---

### Post by Mighty_Joe on 2009-06-19
> **olliraa said:**
> Could it be a possibility to install Ubuntu as a standard install to the stick and then set all logging and swappiness to 0 (I really don't need swap at all with my setup). This should reduce the writing to the stick dramatically, right?

There's some other things you can do, like moving logging to tmpfs.  I used this [install]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configure]("http://beastie.cs.ua.edu/cs150/configuration.html") guide to set my flash drive up.  Works great.
His guide doesn't mention the swappiness switch, but I use that too.
Given that flash may wear out, store your important files elsewhere!

---

### Post by Knacker_Ned on 2009-06-24
> **dcstar said:**
> 

[LIST=1]
[*]Use the Partition Editor to wipe your USB drive and then create a FAT32 partition  on it (I used 3GB so I can store stuff on it, 700MB minimum if you don't need to do that).
[*]Use the Partition Editor to create an EXT2 partition on the USB labelled "casper-rw" (it is vital that this name is exactly used) to store updates/persistent data (1GB minimum recommended)
[*]Use the USB Startup Disk Creator to make the drive using the FAT32 partition you created previously
[/LIST]


Apologies for coming to this thread late, but I too have been having problems saving files persistently from a usb stick (live cd running Ubuntu) when using the USB Startup Disk Creator. However, other than the OS is slighly slower to load, all seems fine now after following dcstar's advice. Thanks for great tip. 

The only part which wasn't clear to me personally concerned the USB Startup Disk Creator and whether I should have chosen to save docs and settings in the "reserved extra space" or to select the "discard on shutdown unless saved elsewhere" option? I chose the latter, which appears to work okay, but did I guess right?

---

### Post by Handssolow on 2009-07-14
I've successfully created working live persistent installs of Ubuntu on usb sticks following methods on pendrivelinux and UNetbootin.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

For a time they seemed to work great but after using update manager over a prolonged period, shortcomings became apparent. I reached a point when I was unable to update or add further applications. Following thinkcow's advice I created a full install on a 8Gb USB memory stick and for the past few weeks I've had an Ubuntu install giving me a normal login with username and password booting it on my Acer AAO netbook.

Booting Ubuntu this USB stick way is certainly usable but things happen rather slowly. Big updates take ages and Google Earth isn't workable, on the other hand booting with XP from the hard drive Google Earth is fast enough.

Is it all about the slow speed of data transfer with a USB stick? Is this the reason for Ubuntu's slow OS speed. Now that external USB hard drives are both small and relatively cheap, would it make better sense to install Ubuntu to one of these instead of a USB stick?

---

### Post by GeorgeVita on 2009-07-15
Hi **Handssolow**, I am still working (from June 9) with the 9.04 installed on the 8GB SDHC updated 2-3 times per week, 3-6 hours daily use on EeePC 1000H (internet, **maps.google.com**, photo xfer/crop/resize, html web page creation/edit, self-education in python, kids are playing playmobil/lego games via internet 3 hours/week). It has slower but usable speed (comparing with the HD). BUT this SDHC is a fast and more expensive memory than USB sticks.
> **Handssolow said:**
> ...Following thinkcow's advice I created a full install on a 8Gb USB memory stick and for the past few weeks I've had an Ubuntu install giving me a normal login with username and password booting it on my Acer AAO netbook.
Booting Ubuntu this USB stick way is certainly usable but **things happen rather slowly. Big updates take ages and Google Earth isn't workable**, on the other hand booting with XP from the hard drive Google Earth is fast enough.
**Is it all about the slow speed of data transfer with a USB stick?** Is this the reason for Ubuntu's slow OS speed.

It is probably the speed of the USB stick and possibly the file system. Use **ext2** for faster response. I 'created' a benchmark before my installation:

> **GeorgeVita said:**
> Hi, I am using only Live/Persistent/Installed 9.04 (and puppy 4.2) into USB sticks and SDHC cards with my EeePC1000H (Hard Disk removed!). Two days ago I made some speed tests on various formats on HardDisk (installed), SD, SDHC and USB flash concluding to faster results with **ext2**.

Speed Check: [http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt)
Graph: [http://acomelectronics.com/GeorgeVita/extPoll.jpg](http://acomelectronics.com/GeorgeVita/extPoll.jpg)

Regards,
George

---

### Post by DavidFourer on 2009-07-15
Recently I read the difference between a Live CD on a USB and an "Install" on a USB.  Install tries to mimic a hard-drive install, but their are some problems.  For one thing, when you carry the USB stick to another computer, it will probably need to be configured for the different hardware.  You can't do this on the fly with a real install.  

The Live CD goes through hardware configuration every time you boot.  System > Admin > USB Startup Disk Creator can make a version of the live CD for USB sticks.  It sets aside a partition for permanent files.  Files with permenant configuration changes go here.  It also saves data files here.  Basically it's like your home directory goes here.  It also allocates swap to ram to avoid wearing out flash memory.  It should behave like an installed OS. 

I tried this and it worked well until I ran System > Admin > Update Manager on the USB stick.  The updates of 100+ files (Jaunty) went fine, but then it wouldn't boot.  I gave up at that point.

You will be asked to allocate some space to the "persistant partition".  Don't use all the space.  Leave a few hundred M or so for Update processes. Also there seems to be a bug limiting the persistant partition to under 2 GB.

This is a hot topic and lots of threads are going.  I think problems will be ironed out in time.

---

### Post by Mighty_Joe on 2009-07-16
> **DavidFourer said:**
> For one thing, when you carry the USB stick to another computer, it will probably need to be configured for the different hardware.  You can't do this on the fly with a real install.  

I haven't run into this problem (if it indeed exists). I've only tested on an HP laptop and HP desktop.

> **DavidFourer said:**
> It also allocates swap to ram to avoid wearing out flash memory. 

It's pretty easy to configure Linux to do this yourself.  See the links in my last post.  

> **DavidFourer said:**
> 
Also there seems to be a bug limiting the persistant partition to under 2 GB.

I found [Bug 321544]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") when I last tried to use the USB creator.  
IMHO, using the Live CD-on-USB is fine for test driving Ubuntu or installing to devices that don't have CD drives.  If one wants to use Ubuntu, he is better off with a full install.

---

### Post by DavidFourer on 2009-07-16
> **Mighty_Joe said:**
> ...IMHO, using the Live CD-on-USB is fine for test driving Ubuntu or installing...If one wants to use Ubuntu, he is better off with a full install.
This is good to know.  Maybe Karmic Koala will have an option to install on a USB stick.  What is the reason it was not offered that way in the first place?

---

### Post by Mighty_Joe on 2009-07-16
> **DavidFourer said:**
> This is good to know.  Maybe Karmic Koala will have an option to install on a USB stick.  

Well, it does.  To Linux, a Flash USB drive is just another hard drive, and installation is the same as with a regular rotating hard drive.  There are a few tweaks to make a USB drive install faster and to save wear and tear on the drive, hardly even worth writing a script to automate (at least the ones I know about).

> **DavidFourer said:**
> What is the reason it was not offered that way in the first place?

My guess: the vast majority of Ubuntu users will install it on their hard drive as a primary OS or dual-boot with Windows. It makes sense for Canonical and the community to concentrate on those users, rather than the few hundred of us who use a USB flash drive.

---

### Post by mctimoth on 2009-07-16
I am trying to get the persistent switch to work with the live CD and USB.  I've followed the LiveCDPersistence documentation.  I cannot get it to work with Jaunty.  Any help here?

Tim:confused:

---

### Post by Mighty_Joe on 2009-07-16
> **mctimoth said:**
> I've followed the LiveCDPersistence documentation.  

Exactly what did you do?  There's no fewer than 5 different procedures on that page.  
What problem are you having?  Does the drive fail to boot?  Does the drive not preserve your settings?

---

### Post by mctimoth on 2009-07-17
Settings are not kept.  I think there is actually suppose to be a file on the thumb drive called casper-rw, correct?  The thumb drive is only labeled casper-rw; no file resident.

I partitioned and formatted the drive.  That is all that needs to be done right?  Then I booted the Live CD with the persistent switch.  The OS came up.  I made some changes; different theme and desktop.  I was keeping and eye on the drive space used and it did not change as I made the OS changes.  The only dir on the drive is Lost+Found.  The drive shows up as casper-rw in File Browser.

Tim

---

### Post by Mighty_Joe on 2009-07-17
> **mctimoth said:**
> I partitioned and formatted the drive.  That is all that needs to be done right?  Then I booted the Live CD with the persistent switch.  

Are you talking about two different devices?  A Live CD and a separate USB flash drive? You boot the CD and hope that changes are saved to the USB drive? That won't work.
The Live CD has a tool on it to install the Live CD image to a USB drive.  That tool has a setting to create a persistent partition. Have a look [here for pictures]("http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/"). Once the Live CD image is on the USB drive, you can boot the USB drive (not the CD) and save your settings.

---

### Post by mctimoth on 2009-07-17
So if I wanted to boot the LiveCD with the persistent switch I would have to fall back to Hardy or Intrepid?

---

### Post by Mighty_Joe on 2009-07-17
> **mctimoth said:**
> So if I wanted to boot the LiveCD with the persistent switch I would have to fall back to Hardy or Intrepid?

I'm sorry. I'm unfamiliar with this "persistent switch".  Can you point me to a link so I can give it a try?  All of the methods for a persistent install that I'm aware of are in [this post]("http://ubuntuforums.org/showthread.php?t=1193680").

---

### Post by mctimoth on 2009-07-17
[This]("https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence") documentation page has the write up.  It was pre-Jaunty and looks like specifically for Dapper but was updated for Hardy and Intrepid.

---

### Post by ujodarko on 2009-09-03
> **mctimoth said:**
> [This]("https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence") documentation page has the write up.  It was pre-Jaunty and looks like specifically for Dapper but was updated for Hardy and Intrepid.

I've looked to that tutorial and gave up immediately.

I can not belive how much energy have been wasted to Ubuntu on USB stick!

Belive me, I came to idea by my self and tryed to install Ubuntu on 4GB flash USB in a normal way. So again, as in post before, I disconnected internal HDD drive, and after booting from Live CD > plug in USB flash memory stick and went through complete instalation (took some time) and after it was finished that USB flash was able to boot! Everything works just fine, I can not belive how everything is operating as from HDD!

**Every file and installed program (aplication) is there after reboot!!! So forget programs Unetbootin like, just go and install Ubuntu on stick as it is one of HDD drives.**

Oh, I tried to install 9.04 on 250 external HDD powered only by USB current, and again with success! 

Linux is simply GREAT!

---

### Post by Krupski on 2009-09-03
> **ujodarko said:**
> I've looked to that tutorial and gave up immediately.

I can not belive how much energy have been wasted to Ubuntu on USB stick!

Belive me, I came to idea by my self and tryed to install Ubuntu on 4GB flash USB in a normal way. So again, as in post before, I disconnected internal HDD drive, and after booting from Live CD > plug in USB flash memory stick and went through complete instalation (took some time) and after it was finished that USB flash was able to boot! Everything works just fine, I can not belive how everything is operating as from HDD!

**Every file and installed program (aplication) is there after reboot!!! So forget programs Unetbootin like, just go and install Ubuntu on stick as it is one of HDD drives.**

Oh, I tried to install 9.04 on 250 external HDD powered only by USB current, and again with success! 

Linux is simply GREAT!

[http://ubuntuforums.org/showpost.php?p=7419118&postcount=14](http://ubuntuforums.org/showpost.php?p=7419118&postcount=14)

---

### Post by carloslosgrande on 2009-09-05
[FONT="Comic Sans MS"]DCStar, I followed your instructions and that fixed it perfectly for me.
Thanks mate.

I do have another query, the system has no password so root is open to the net? Like running as admin on windows?

I was wondering whether I should try and put a password on root or create a new user?

Ta.[/FONT]

---

### Post by map7 on 2009-10-28
Portable Linux seems to be the best current solution for create a persistant bootable usb.  This works for multiple distros not just ubuntu and includes grub and other nice features.

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

---

### Post by pricinosus on 2009-11-21
[**[COLOR="Red"]here[/COLOR]**]("http://www.storagesearch.com/ssdmyths-endurance.html") is a article about write endurance on ssd

---

### Post by Mighty_Joe on 2009-11-23
> **pricinosus said:**
> [**[COLOR="Red"]here[/COLOR]**]("http://www.storagesearch.com/ssdmyths-endurance.html") is a article about write endurance on ssd

To be clear, USB flash drives are not the same thing as an SSD.  SSD's are designed to be used exactly like hard drives, with data intensive operations taking place 24/7.  USB flash drives are designed to hold fairly static data and hang off a key chain.  I would not use that article to draw conclusions about the endurance of a USB flash drive.  
Personally, when I boot up my laptop with a USB flash drive, I save anything I want to keep on a NAS.

---

