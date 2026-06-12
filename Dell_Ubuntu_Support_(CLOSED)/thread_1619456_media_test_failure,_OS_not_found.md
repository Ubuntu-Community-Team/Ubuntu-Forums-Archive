---
title: "media test failure, OS not found"
date: 2010-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inspiron910 on 2010-11-11
Couldn't start my linux netbook, so at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) I downloaded netbook version and followed mac USB startup disk creation instructions.

Changed setup in my Inspiron 910 to boot from USB; I get:

Intel UNDI, PXE-2.1 (build 082)

For Realtek RTL8101E/8102E PCI-E Ethernet Controller v1.08 (080408)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Operating system not found

Hitting enter repeats this; flash drive light flashes


Do I need a different version of Ubuntu? If so, what, and where can I get it?

Do I need to find a Windows friend to create a working USB startup?

Do I have a hardware issue?

Is there a way to at least save the other files?

Sorry if I didn't search the abundant material diligently enough before posting. Any help would be greatly appreciated. Thanks!

---

### Post by PRC09 on 2010-11-11
Are you sure it is set to boot from usb.I think the error you see about PXE is its trying to boot from your nic card as a network install.Your machine is not seeing the usb as a bootable device so moves to the next device set to boot which is your nic....Are you creating this usb boot from a mac???

---

### Post by inspiron910 on 2010-11-11
I created the boot from a mac because that's my other computer. I'd read elsewhere, in contradiction to the instructions, that this wouldn't work. The flash drive has a new name and its window's files look the way Windows files normally look on my mac.

---

### Post by PRC09 on 2010-11-11
Sorry I dont have any experience with Mac but what exactly are you trying to do.Is it just that you cant boot the Inspiron or are you trying to install or ???

---

### Post by inspiron910 on 2010-11-11
I was unable to boot my existing linux and didn't have any CD so I sought a version to download. But I have no idea if the Inspiron 910 is limited to any given version (it's become unstable recently after I auto-updated it).

---

### Post by Jim198865 on 2010-11-11
[LEFT][COLOR=#444444][FONT=Verdana]Years ago, Microsoft had stopped the upgrade on [/FONT][/COLOR][FONT=Calibri][SIZE=3][**Windows Media Player for Mac**]("http://www.umacos.com/windowsonmac/run-windows-media-player-on-mac-os-x.html") [/SIZE][/FONT][COLOR=#444444][FONT=Verdana]and promote QuickTime component Filp4Mac. So chances are you need to run [/FONT][/COLOR][FONT=Calibri][SIZE=3][**Windows Media Player for Mac OS**]("http://www.umacos.com/windowsonmac/run-windows-media-player-on-mac-os-x.html")[/SIZE][/FONT][COLOR=#444444][FONT=Verdana] and you don’t want to shift to other media player. What are you left with?[/FONT][/COLOR][/LEFT]
 
 
 
[LEFT][FONT=Calibri][SIZE=3]In addition to being a media player, Windows Media Player includes the ability to rip music from and copy music to compact discs, burn recordable discs in Audio CD format or as data discs with playlists such as an MP3 CD, synchronize content with a digital audio player or other mobile devices, and enable users to purchase or rent music from a number of online music stores.[/SIZE][/FONT][/LEFT]
 
 
**[COLOR=#444444][FONT=Verdana][B]Install Windows Media Player for Mac OS X** [/FONT][/COLOR][/B]
[COLOR=#444444][FONT=Verdana]Windows Desktop for Mac lets you install Windows system on Mac so you can easily run any Windows application on Mac, like Windows Media Player 12, at native speed. You can install it on your Mac and run it directly from Mac application dock. Like the idea? Read on. [/FONT][/COLOR]

 
**[COLOR=#444444][FONT=Verdana][B]Step by step guide to install Windows Media Player on Mac OS X**[/FONT][/COLOR][/B]

 
 
[LEFT]**[COLOR=#444444][FONT=Verdana]Step 1:[/FONT][/COLOR]**[COLOR=#444444][FONT=Verdana] Download and install the Windows Desktop for Mac.[/FONT][/COLOR][/LEFT]
 

[LEFT][FONT=Verdana][COLOR=#444444]**[FONT=Verdana]Step 2:[/FONT]** Read and follow the instructions for installing Windows on your Mac computer[/COLOR][/FONT][/LEFT]

 

[FONT=Verdana][LEFT][COLOR=#444444]**[FONT=Verdana]Step 3: [/FONT]**The Windows Media Player is built-in application of Windows system. So when you finished, you will find the Windows Media Player in Windows system. Otherwise, you can [/COLOR][/FONT][/LEFT]
[FONT=Verdana]
 
[LEFT][/FONT][FONT=Calibri][SIZE=3]download Windows Media Player for Mac[/SIZE][/FONT][COLOR=#444444][FONT=Verdana] from Microsoft’s official site and install it.[/FONT][/COLOR][/LEFT]
 
 
[LEFT][FONT=Verdana][COLOR=#444444]**[FONT=Verdana]Step 4:[/FONT]** Double click the icon of Windows Media Player to run it on Mac.[/COLOR][/FONT][/LEFT]
 
 
 
 
[LEFT][FONT=Calibri][SIZE=3][IMG]http://www.umacos.com/images/windowsonmac/windows-media-player-10.jpg[/IMG][/SIZE][/FONT][/LEFT]

---

### Post by inspiron910 on 2010-11-11
Did you mean to post this somewhere else, or will this help with this issue?

P.S. My mac is not Intel-based.

---

### Post by PRC09 on 2010-11-11
Hmmm, that above post was different!!!!

Dont know if this will help, maybe with your original problems.....


[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by PRC09 on 2010-11-11
Just found this,I have no way of knowing if it works but....


[http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/](http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/)

---

### Post by inspiron910 on 2010-11-11
The makeuseof link seems to have an identical procedure, EXCEPT that it says to obtain the file in IMG format rather than convert it from ISO, which I did. Could this be the problem?

Anyone know where I can get the IMG format he says is available? Thanks.

---

### Post by PRC09 on 2010-11-11
Sorry for the delay but the last .img file I could find was for 9.04 so dont know if that will serve your purpose but here is the 
link,doesnt look like that format is used from then on....


[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by inspiron910 on 2010-11-12
I reformatted the flash drive with this 9.04 download using the Mac's sudo terminal command, just as I had with the other version, but although it seems to have loaded the correct files and has a new size that seems right, the disk was named Untitled instead of being given a specific Ubuntu name, and the terminal showed no activity after the command (never went back to the prompt) unlike with the first formatting. When I tried to boot from it, I just got MBR on the netbook. So I sense I was closer the first time. Maybe I'll try the first procedure but with a 9.04 ISO until I can get to Windows. Thanks.

---

### Post by inspiron910 on 2010-11-12
IT WORKS!

Even though it seemed to transfer about enough megabytes in a short time, doing it for 20 minutes brought the terminal prompt back and a working flash. Now I just have to deal with the netbook's SSD:

Cannot mount volume

mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error

I'll try syslog -try, dmesg | tail or so like it suggests, once I figure those out, to recover docs--of course I welcome any suggestions.

---

### Post by skubo on 2011-01-01
i has the same netbook,mine had the crash after login problem.
mine can run from text mode.and copy files from the ssd to sd.

i gets a file type error when i mounts a usb with the wrong partition number.
/dev/sda2 is ubuntu
/dev/sda1 is dell utils.


in moblin usb i has to mount the ssd on the command line first,
or the file broswer crashes.

the meego.img worked, i used
dd bs=4096 if=filepath of=/dev/sdc

the first time i used sdc1, and it didn't work.


i tried on my slackware 9.1 desktop

dd bs=4096 if=/pathto/ubuntunetbook-10.10.iso of=/dev/sda

i also tried to copy the bootable dell restore dvd to usb with

dd bs=4096 if=/dev/sr0 of=/dev/sda

the dvd wasn't mounted first, i gets the os not found
the usb can be mounted and the files seen.
should .iso be copied to sda1
what file type does dd make on the usb.
does ubuntu use a file name or location that the dell +usb boot
 menu cant see.
the ubuntu download page didn't have command line instructions
for ubuntu ,can usbcreator be used from the command line without
the missing libgconf-2.so.4 file.
what does usbcreater do that dd doesn't

is ubuntu's iso different from the other iso's
the help.ubuntu.com page was long with alot of links,not sure
whitch ones need to be followed.looked like syslinux was on the
usb.


meego wants a user and password ,when using devices open ssd
not sure what the right answers are.
i can list the files, but cant open or copy them.
does ubuntu write protect the ssd in some way.
or would the update change permissions
is this normal or the reason ubuntu cant find some files

would it be bad to copy a lib file from the dvd usb copy to the
ssd using ubuntu's text mode cp copy.

---

