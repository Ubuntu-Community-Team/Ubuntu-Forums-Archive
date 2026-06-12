---
title: "Time for some ranting"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sn0m on 2008-07-09
My beloved compaq pressario v5000 screen packed up(wired as it would work flowlessly with hardy and has got broadcom of some sort and ati graphics) so bought what i thought would work out of a box with linux, ie a Dell Inspiron 1525. bump........ 
First of all it wont let me install WinXP as I normally use it for wired microsoft file formats that some people continue to use. I had to use dells media centre cd that does some sort of wired partition thing, after that I can only install the bloated vista. Even after installling vista, wont let me install xp, bastards.
Anyway, after that I installed hardy which went fine, graphic card works great, credit to intel x3100. However the broadcom crap dosen't won a do a thing.
This is the lspci

sn0m@sn0m-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
sn0m@sn0m-laptop:~$ 

and this is the lshw

sn0m@sn0m-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:4e:75:f0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.15.133 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
sn0m@sn0m-laptop:~$ 



Tried propritary hardware drivers, apparently it is installed but not in use. It is some sort of wl    -enabled -not in use.
I tried disabling and re-enabling it, restarting hardy but no luck, comes back as not in use again.
Has anybody had any experince with it and how to get it to work again....
Kind regards
Sokol

P.S 
did some research in here, some guides are too technical for a newbe like me.

---

### Post by sn0m on 2008-07-10
oups, silence ](*,)](*,)](*,)

---

### Post by sn0m on 2008-07-10
Ping, ping
no one's feeling my pain......

---

### Post by nikgare on 2008-07-10
WHat happens when you click in the Hardware Drivers Dialogue to turn on the driver?

---

### Post by sn0m on 2008-07-10
Thanks mate, for a moment I felt lonely.......
Device is already enabled but not in use, however disabling then enabling it asks for system restarts, which dosen't do a thing, comes back to the same point, ie enabled but not in use.
Ta
Sokol

---

### Post by nikgare on 2008-07-10
Maybe this will help:

[http://ubuntuforums.org/showthread.php?t=850675](http://ubuntuforums.org/showthread.php?t=850675)

---

### Post by sn0m on 2008-07-11
Thanks nikgare
it worked :)
I advice people to use ndiswrapper plain on their windows xp driver as bcxx fcutter can sometimes mess it up.
Maybe ubuntu guys should look at it.
Anyway thanks for all your help.
You guys rock
Sokol

---

### Post by rickyjones on 2008-07-11
> **sn0m said:**
> 
First of all it wont let me install WinXP as I normally use it for wired microsoft file formats that some people continue to use. I had to use dells media centre cd that does some sort of wired partition thing, after that I can only install the bloated vista. Even after installling vista, wont let me install xp, bastards.


Your laptop uses a SATA drive, according to the lspci command output that you posted. Windows XP does not support the majority of SATA controllers without integrating the driver. I have a Latitude D630 with the intel sata controller. I had to integrate the driver into my Windows XP CD.

Vista installed because it has the correct SATA driver.

So, who are the bastards then?

-Richard

---

### Post by timcredible on 2008-07-11
maybe it would be easier to try to find linux apps that will open the files you mentioned rather than trying to install xp?  what are you having trouble opening?

---

### Post by sn0m on 2008-07-11
Richard, this is my ranting post, if you want to do a bit of ranting yourself feel free to open a new thread. 
However since you asked an 80% self explanatory question, my answer is that any company that tries to push whatever operating system by inventing new drivers to make the old operating system incompatible with new hardware is a *******. My xp is ok with SATA, however i had to disable the AHCI in bios and revert to pure ATA hdi control to install it. So that's one for microsoft, the other is for Dell, as the inspiron 1525 was supposed to be linux friendly, however i spent 2hrs trying to find an xp driver for BCM4310 till i realised that it was renamed by dell as some dell minipci wireless card.
Ok, so when the expectations of a human being who is not a software expert by trade are crushed, one would naturally be frustrated and use the word B..... However thanks for your help...

---

### Post by sn0m on 2008-07-11
Hi Tim
sometime i get files like xml documents that are difficult to work with linux yet and I also quite like adobe premier for video editing, so till something like that becomes available, I will continue to keep an xp partitition in my computer.

Kind regards
Sokol

---

### Post by Lumpy da Moose on 2008-07-17
[FONT="Comic Sans MS"][SIZE="3"]
Hi Sokol--

Couple things got my attention.  You CAN use XP on your laptop, but it is tricky to get the AHCI drivers to load.  You do not have to slipstream them into the XP install, you can just set the BIOS to do ATA for hd control as you've done and it works fine.  You can scratch around on the Dell forums and find out where to get the AHCI drivers and how to do the install in XP-- very easy, but it is tricky to find them.  Even the forum moderators in the Dell forums seem to be reluctant to give away much info on supporting XP; I'm sure someone is pressuring them to not do it "officially."  I had Vista on here half a day and wiped the drive.  Piece of excrement I hope to never be forced to use or support at work.

I've found everything I need to get my XPS M1530 to work well in Hardy on here.  I wish I had documented everything better-- where to find, what links, etc., so if I have to do this again, I'll know where everything is.  

I too use an XP partition for much the same reason-- no one has put together a good open source timeline video editor for Linux yet.  It's in the works, from what I hear, but will be a little while yet.  I use two Windows editors, depending on the machinery.  On my desktop at home I use Liquid 7.  On the laptop, I use Pinnacle 10; works fine for one-camera stuff.  I'm assuming you're using Premier with an external drive (or 2).  

I'm assuming of course that you got your wireless working.  There's lots of help for that on the forums here-- the fwcutter thing did not work at all for me.

Good luck and happy editing

L[/FONT][/SIZE]

---

### Post by zedcar on 2008-09-24
sn0m I just wanted to say I share your pain. I've done the same as you - bought a 1525 preloaded with Vista, trashed it, installed 8.04.1 in the expectation it would work - and now I'm stuffed. No wired or wireless connectivity. I've been trying all sorts of things for five hours and so far no good. 

What's worse is that I bought it for my daughter and in about 4 more hours she is going to be real pissed when I tell her I've broken her shiny new machine.

---

### Post by lumos_aeternum on 2008-09-24
Yeah, ndiswrapper is certainly the way to go. If it weren't for that, I wouldn't have net now... It is a little tricky to work out if you don't know how to use it, and I wish there were easy to follow directions out there. I don't think I'm savvy enough yet to explain it...

---

### Post by zedcar on 2008-09-24
Thanks lumos

Thankfully, I managed to install the Dell image and somehow wired connectivity came to life. This sounds bizarre but true... wired was dead, so I was cruising through the logs to see if I could diagnose the problem, I had a play with my webcam (after I saw the message that it was working) and when I got to the end I saw a message that said ethernet had started... 

Once I was connected I was able to download nearly 400megs of updates, and somewhere in there after a reboot, the wireless drivers installed themselves.

I've now also isntalled wicd to make it all work properly. Phew. I live to play another day.

---

### Post by lumos_aeternum on 2008-09-24
Lucky! Glad it worked out. I tried to get my wired to work and had the same problems...

---

### Post by adult swim on 2008-09-25
zedcar, do you know what driver is being used with the dell image?  i am curious to know.

---

### Post by zedcar on 2008-09-25
adult_swim - Sorry I've handed the machine to it's new owner and it might take me a few days to answer your question. I think it was just the standard 'wl' driver - does that make sense?

FWIW - She (the new owner) is mightily impressed, so I should say thanks to all the nice Ubuntu people who made it work.

---

### Post by zedcar on 2008-09-25
adult_swim - Sorry I've handed the machine to it's new owner and it might take me a few days to answer your question. I think it was just the standard 'wl' driver - does that make sense?

FWIW - She (the new owner) is mightily impressed, so I should say thanks to all the nice Ubuntu people who made it work.

---

### Post by sn0m on 2008-09-28
Good on you mate, glad you got it sorted out. I've physically removed broadcom wireless and replaced it with intel wireless pro and it works like a charm. Maybe next time I'll buy a linux machine from dell and spare the headaches.
Regards
Sokol

---

