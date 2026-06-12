---
title: "Old PC"
date: 2008-12-15
forum: General Help
---

### Post by Powerman2442 on 2008-12-15
I have an old PC that I got free from my grilfriend's grandma, after she decided to buy a new one. It is extremely old but I would like to fix it up and make it decent for browseing, e-mailing, and watching videos online (Youtube, etc.).

Here are the specifications.

- Pentium 2 350 Mhz
- 2x64 MB RAM (128 MB) PC-100 (Note: Have 2x256 MB coming, so I plan to use 2x256 MB + 1x64 MB = 576 MB RAM)
- ATI Rage 2 8 MB AGP GPU (Might consider upgrading if anyone has a list of good older AGP cads that work well under Linux)
- 8 GB 5400 RPM ATA-33 HDD (Want to upgrade, but the max ATA-33 I can find is 10 GB, might buy an external or a PCI IDE or SATA controller)

Currently Running Windows XP Pro, halfway decent.

My main concern is I need to find a distro that will not bog down this old system. I've considered Damn Small Linux, but I really enjoyed working with Ubuntu on my laptop (once I got the wireless NIC working). Which brings me to my next concern. I connect this computer to the internet via wireless NIC PCI card. I don't think the one I have is going to work.

It is a LinksKey (NOT Linksys) LKW-G553. It does not come with Linux  drivers (no suprise) and I've read on some other forums that it may not be supported based on the fact that it has a Mervell chipset. Does anyone have any more info on it or a list of compatible PCI wireless NICs?

Thanks ahead of time,
Powerman2442

---

### Post by abn91c on 2008-12-15
im on a 400mhz celeron with 448mg pc100 ram, if you can find a 40 gig IDE HDD you may be in business, my has a similar video card, i my case an SIS 8mb AGP, ubuntu 8.10 runs in low graphics mode, which means no compiz or fancy eye candy like cairo-docks, but the colors and every thing else works fine, I'm using a belkin usb adapter since i get some sort of confict if i use a PCI NIC. Wait for you ram then you will probably do OK with 8.10, I never used an ATI card but f your monitor supports 1028 x768 or higher you will be able to work around any video issues that may surface. follow the ubuntu sound guide if you have any problems with your sound card, it revived my old yamaha isa card.

---

### Post by samden on 2008-12-15
With enough RAM you will be able to run Ubuntu with Gnome (the default environment), but it will be slow.

I'd consider using fluxbox if I were you. Damn Small Linux uses fluxbox. That way you can have an efficient system just like DSL, but still be using Ubuntu. Install Ubuntu, then do "sudo apt-get update" and "sudo apt-get install fluxbox", and you'll have an alternative environment that will be a bit quicker, while still having your familiar Ubuntu desktop available to you. I've only been using fluxbox for a week (on a PIII) and am hooked! More info here:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

An 8GB hard drive will be manageable although not ideal, there are ways to trim down the installation. I'm using a 10GB HD with no worries. Make sure you delete all the .deb files after installing software, that will free up a lot of space - use "sudo apt-get clean".

---

### Post by EngDrewman on 2008-12-15
> **samden said:**
> With enough RAM you will be able to run Ubuntu with Gnome (the default environment), but it will be slow.

I'd consider using fluxbox if I were you. Damn Small Linux uses fluxbox. That way you can have an efficient system just like DSL, but still be using Ubuntu. Install Ubuntu, then do "sudo apt-get update" and "sudo apt-get install fluxbox", and you'll have an alternative environment that will be a bit quicker, while still having your familiar Ubuntu desktop available to you. I've only been using fluxbox for a week (on a PIII) and am hooked! More info here:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

An 8GB hard drive will be manageable although not ideal, there are ways to trim down the installation. I'm using a 10GB HD with no worries. Make sure you delete all the .deb files after installing software, that will free up a lot of space - use "sudo apt-get clean".

The only thing is that fluxbox is incredibly non-user friendly/ for power users. I would strongly recommend xubuntu instead and use fluxbox only as a last resort.

---

### Post by Powerman2442 on 2008-12-16
> **samden said:**
> With enough RAM you will be able to run Ubuntu with Gnome (the default environment), but it will be slow.

I'd consider using fluxbox if I were you. Damn Small Linux uses fluxbox. That way you can have an efficient system just like DSL, but still be using Ubuntu. Install Ubuntu, then do "sudo apt-get update" and "sudo apt-get install fluxbox", and you'll have an alternative environment that will be a bit quicker, while still having your familiar Ubuntu desktop available to you. I've only been using fluxbox for a week (on a PIII) and am hooked! More info here:
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

An 8GB hard drive will be manageable although not ideal, there are ways to trim down the installation. I'm using a 10GB HD with no worries. Make sure you delete all the .deb files after installing software, that will free up a lot of space - use "sudo apt-get clean".

I'll have to see what's the max hard drive this motherboard can handle. I wouldn't doubt 40 GB is the max. Maybe you can help me. It is a Superpower SP-P2BXA. I'll keep looking around.

So far I have found this. [http://www.elhvb.com/mboards/superpower/manuals/SP-P2BXA.html](http://www.elhvb.com/mboards/superpower/manuals/SP-P2BXA.html) and everything else is a dead link. :(

TigerDirect.com sells ATA-100 40 GB and 80 GB modles for 39.99 each. But I wouldn't want to buy the 80 GB if the BIOS won't detect it. Newegg also has an 80 GB for 35.99. I've looked for the older ATA-33 like I have and they are around 10 GBs and used. If anyone figures out anything let me know.

Thanks

---

### Post by spcwingo on 2008-12-16
Puppy would be great on that box.  I'm running it (a derivative called Macpup) on an ancient Compaq Armada 1592dmt laptop with a Pentium I @ 233Mhz, 98MB RAM, and a 3GB HDD.  It would blow XP out of the water on that machine.

---

### Post by Powerman2442 on 2008-12-16
> **spcwingo said:**
> Puppy would be great on that box.  I'm running it (a derivative called Macpup) on an ancient Compaq Armada 1592dmt laptop with a Pentium I @ 233Mhz, 98MB RAM, and a 3GB HDD.  It would blow XP out of the water on that machine.

Hmm, got any links? I'll look around. I'm guessing I will have a harder time finding a wireless NIC that works with at distro, correct?

Edit: I found the site and I'm reading up on it now. Do you mean Macpup Dingo? Thanks.

---

### Post by TeXtonyx on 2008-12-16
I doubt if that motherboard will support more than 384mb of ram.
Look up in your bios when you boot up, it will likely identify
your motherboard. Then go to the manufacturer's website and dl
the mobo manual. Sometimes you can find the manual using Google.

I wouldn't open the second stick of 256mb ram until you find out
how much will work. There should be a bios update that will let
you use at least 32GB of a 40GB (a standard size) hard drive.

---

### Post by spcwingo on 2008-12-16
> **Powerman2442 said:**
> Hmm, got any links? I'll look around. I'm guessing I will have a harder time finding a wireless NIC that works with at distro, correct?

Edit: I found the site and I'm reading up on it now. Do you mean Macpup Dingo? Thanks.

Yes, that's the one.  All versions of Puppy are very simple and easily customized.  I have only been using linux in general for about 6 months and I have already made my own Puppy derivative...this coming from a long time windows user.  Here's a link to Puppy/derivatives downloads:

[http://www.puppylinux.org/downloads]("http://www.puppylinux.org/downloads")

It shouldn't be that hard to find a wireless card for it.  Try going to:

[http://www.geeks.com]("http://www.geeks.com")

and looking for wireless USB cards with Realtek rtl8187 chipsets.  Not only are they cheap, but they also work pretty good too.

---

### Post by theultimate on 2008-12-16
Try Puppy linux. It is very light, and it has very much software for everyday work.

---

### Post by Powerman2442 on 2008-12-16
> **TeXtonyx said:**
> I doubt if that motherboard will support more than 384mb of ram.
Look up in your bios when you boot up, it will likely identify
your motherboard. Then go to the manufacturer's website and dl
the mobo manual. Sometimes you can find the manual using Google.

I wouldn't open the second stick of 256mb ram until you find out
how much will work. There should be a bios update that will let
you use at least 32GB of a 40GB (a standard size) hard drive.

The only site I've found information on about this board says it can have 768 MB of RAM max. (3x256 MB) If there are any BIOS updates for this board I would like to know. The company that made it no longer exists and every link I find that "should" have information about it is dead.

---

### Post by Powerman2442 on 2008-12-16
> **spcwingo said:**
> Yes, that's the one.  All versions of Puppy are very simple and easily customized.  I have only been using linux in general for about 6 months and I have already made my own Puppy derivative...this coming from a long time windows user.  Here's a link to Puppy/derivatives downloads:

[http://www.puppylinux.org/downloads]("http://www.puppylinux.org/downloads")

It shouldn't be that hard to find a wireless card for it.  Try going to:

[http://www.geeks.com]("http://www.geeks.com")

and looking for wireless USB cards with Realtek rtl8187 chipsets.  Not only are they cheap, but they also work pretty good too.

Well I downloaded both Xubuntu, Puppy, and MacPup Dingo. To bad I can't boot up into any of them. Been having problems with my CD-Rom drive. When  I got this thing I installed a few programs from a disk onto the drive. Then, the next day I tried to install an old game and the drive told me that there was no disk in the drive. I've tried every CD with no luck. Can't even boot up a Live CD. I'm think it might have somthing to do with an IDE controller.

---

### Post by TeXtonyx on 2008-12-16
> **Powerman2442 said:**
> The only site I've found information on about this board says it can have 768 MB of RAM max. (3x256 MB) If there are any BIOS updates for this board I would like to know. The company that made it no longer exists and every link I find that "should" have information about it is dead.

Good, the old max ram limits are sometimes 128mb, 256mb, 384mb, 768mb or 1GB

Check in your bios, see if enabling LBA support is an option. That is good
for trying a larger drive, 20 or 40 GB, used, and they are hard to find new.

---

### Post by Powerman2442 on 2008-12-16
> **TeXtonyx said:**
> Good, the old max ram limits are sometimes 128mb, 256mb, 384mb, 768mb or 1GB

Check in your bios, see if enabling LBA support is an option. That is good
for trying a larger drive, 20 or 40 GB, used, and they are hard to find new.

I will check it out. Yeah the smallest internal drive NewEgg and tiger Direct sells are I think  40 GB. Anythign smaller then that is going to be used and bought off ebay for example. the drive size isn't bothering me so much as you can get a flash memory stick with 16 GB for $16.

---

### Post by louieb on 2008-12-16
P2-400mHz maxed out at 384 MB ram. Had to do a BIOS upgrade to it before it would handle larger that a 30GB drive. Some drives have a CLJ (capacity  limiting jumper) when set make the drive look like its a 30GB drive to BIOS.  

Its got an nVidia FX5200 AGP card in it. Works pretty decent. and cheep. 

I just use it as a play and test machine. Kinda nice to have a PC that will run most anything even if its slow.

---

### Post by samden on 2008-12-16
> **EngDrewman said:**
> The only thing is that fluxbox is incredibly non-user friendly/ for power users. I would strongly recommend xubuntu instead and use fluxbox only as a last resort. It is somewhat non-user-friendly, which is why I recommended installing ubuntu or xubuntu (both are much larger than a small distro like DSL or Puppy), then installing fluxbox as an alternative graphical environment. You can always drop back into Gnome or XFCE if something is playing up. If you use DSL or Puppy you're stuck only with fluxbox or another similar system, and don't have an alternative if you find it too difficult to do something in.

---

### Post by mpsii on 2008-12-16
Sticking to the idea that someone on the Ubuntu Forums is looking to use Ubuntu with their old hardware, I suggest the following:

Fluxbuntu
[http://fluxbuntu.org/]("http://fluxbuntu.org/")

Screenshots:
[IMG]http://fluxbuntu.org/fluxbuntu-intrepid.png[/IMG]

Or try the following
Install Ubuntu for low memory systems:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
Note that there is a section at the bottom for suggested low memory combinations of GUI environments, include XFCE. Remember you can install XFCE without having to get the full on Xubuntu-desktop package.

Then, install IceWM (can have a windows xp look, if desired... or not):
[https://help.ubuntu.com/community/IceWM]("https://help.ubuntu.com/community/IceWM")

Screenshots:
[IMG]https://help.ubuntu.com/community/IceWM?action=AttachFile&do=get&target=2007-12-07-222200_1024x768_scrot.jpg[/IMG]

---

### Post by Powerman2442 on 2008-12-16
Heh, nice. Well thanks for the help guys. I've figured out that my CD-ROM drive is shot. Need to buy a new one, but they are fairly cheap so it shouldn't be a problem. Once I get that up and running I am going to try a few different things and figure out what one I like. Ahh, the beauty of Linux. Speaking of which I just got my head chewed off at Windrivers.com for asking them about the who IDe contoller issue. Then, mentioning the fact I am going to be installing Linux on it. Or as they refered to it, Linshit. :P I love it.

Thanks again,

---

### Post by Powerman2442 on 2008-12-18
Ordered a new CD-Rom drive and found out today that my wireless NIC has a Realtek 8185L chipset and there are Linux drivers included on the driver disc (didn't know that). Might be easier to get my wireless NIC up and running than I thought. Although if I have problems they told me that the y don't provide support under Linux (big suprise).

---

### Post by nolanjurgens on 2008-12-18
I just switched an old (AMD K6 333/160 MB of RAM) laptop over from Xubuntu to U-lite. I believe U-lite uses Light X Desktop Environment (LXDE) which in turn uses Openbox, instead of XFCE. Anyways it does seem to be running a little smoother than Xubuntu did on that hardware, but looks/is laid out very similar. I actually thought it was XFCE at first. Anyways, if your gonna try out some different distros I'd say that's another one to take a look at, at least if Xubuntu happens to run slower than you would like.

[http://u-lite.org/](http://u-lite.org/)

---

