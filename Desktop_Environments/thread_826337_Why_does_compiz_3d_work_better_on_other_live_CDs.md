---
title: "Why does compiz 3d work better on other live CDs"
date: 2008-06-11
forum: Desktop Environments
---

### Post by tunznath on 2008-06-11
Hi
Just wondering why compiz 3D works better on other distros live CDs than my dual boot ubuntu setup - I am talking about Mandriva Live CD and the Dream Linux live CD - everything is smoother and I dont get left with little blocks on the screen sometimes and also I dont have lines on the screen where the drop shadows were, as I do in my ubuntu HH instal - any Ideas anyone - 

Also off topic when I use my windows boot to access the net I can have my wireless router in another room with the door closed and it works yet using Ubuntu I have to have my wireless router in a direct line of sight with the wireless stick. WEIRD 

You are probably wondering why I still have to use windows - well till I get the DVB-t stick, scanner, wacom tablet working I still have to use windows - so any ideas on that appreciated

---

### Post by pytheas22 on 2008-06-11
Compiz performance differences could be the product of different graphics drivers.  What kind of card do you have and which driver are you using?  As long as you have a decent graphics card, you shouldn't be seeing unsmooth behavior or blotches on the screen using compiz (it works smoothly for me on a six-year-old onboard Intel i810 chip), so there's probably something that you can fix in Ubuntu if you're seeing problems like that.

Poor wifi signal strength could also be a driver issue.  Some Atheros cards especially are known to have markedly weaker signal strength when using the Linux driver than they do in Windows.  Again, what kind of wireless card do you have and which driver are you using?  If you used ndiswrapper and the Windows driver then you should get the same performance that you would with Windows.

I've never had a scanner or wacom, so I can't help there.

---

### Post by tunznath on 2008-06-12
the graphics card is a ATI mobility radeon 7000IGP
the wireless is a buffalo airstation wireless G

---

### Post by pytheas22 on 2008-06-12
Are you using the open-source or proprietary driver for your ATI card?  By default it uses the open-source driver.  The distributions that work better are probably using the proprietary one.  Try downloading envy:
```

sudo apt-get install envyng envyng-gtk
```

and then run it with:
```

sudo envyng-gtk
```

and use it to install the closed-source ATI driver.  Log out of your session and back in and see if the desktop effects are smoother.

For the wireless, please post the output of these commands:
```

lsusb
lspci
```

The name of the wireless adapter as it appears on the shelf isn't enough, because it's the wireless chipset inside that matters, and hardware vendors rarely make it clear which chipset their cards use.  The lspci/lsusb commands will tell us.

---

### Post by tunznath on 2008-06-12
Hi pytheas22
Thanks for all of that -  If I do the envy way  - is there a way I could get back to what I have setup at the moment - I have jumped thru hoops and fire to get it to where it is.

here is lsusb
nath@nath-laptop:~$ lsusb
Bus 003 Device 014: ID 0a5c:2100 Broadcom Corp. 
Bus 003 Device 013: ID 0d7d:1600 Phison Electronics Corp. 
Bus 003 Device 012: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 011: ID 08ec:0008 M-Systems Flash Disk Pioneers 
Bus 003 Device 010: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 003 Device 009: ID 0409:005a NEC Corp. 
Bus 003 Device 008: ID 0d49:7450 Maxtor 
Bus 003 Device 007: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 003 Device 006: ID 0411:0066 MelCo., Inc. 
Bus 003 Device 005: ID 0409:005a NEC Corp. 
Bus 003 Device 004: ID 04cf:8819 Myson Century, Inc. 
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1111 Belkin Mouse
Bus 001 Device 001: ID 0000:0000  
nath@nath-laptop:~$ 
--------------------------------------------------------
and lspci

nath@nath-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)


MANY THANKS
Nathan

---

### Post by AdamWill on 2008-06-12
pytheas: nah, it's not open vs. proprietary driver. That chip is too old to work with the proprietary driver, it's only supported by the open source driver. Mandriva will be using the same driver as Ubuntu.

Given that I'm not sure why performance would be better in MDV than Ubuntu...

---

### Post by pytheas22 on 2008-06-12
> Thanks for all of that - If I do the envy way - is there a way I could get back to what I have setup at the moment - I have jumped thru hoops and fire to get it to where it is.

Envy itself doesn't provide any "go-back" feature, but if for some reason you want to undo the changes that envy makes, you should need merely to uninstall the proprietary ATI driver by using Synaptic.  That said, I can't guarantee 100% that envy isn't going to do something weird and cause irreparable problems, so if you're happy enough with the way compiz works now, you could wait and save the envy thing for the next time you have to reinstall Ubuntu.  It's up to you.

As for the wireless stuff, it looks like you have a USB wireless adapter with a Broadcom chipset.  If you want to try using the Windows wireless driver instead of the native Linux one to see if you can get a better signal (you should), you would want to do this:

1. blacklist native driver:

```
sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
```

2. install ndiswrapper and a graphical interface for it:
```

sudo apt-get install ndiswrapper ndisgtk
```

3. start the ndiswrapper GUI by selecting it from System>Administration>Windows Wireless Drivers

4. click the button to install a new driver and browse to the location of the .inf file associated with the Windows driver for your device.  Since you have a dual-boot system, you should be able to just browse to wherever in Windows the driver is kept.  Otherwise you can download the driver and save it somewhere on your Ubuntu system.

5. if everything works as it should, you'll get a message to the effect of "driver installed, device present."  Then reboot your computer and your card should be working using the Windows driver.

6. if for some reason you want to revert to the native Linux wireless driver, you need simply to type:
```

sudo gedit /etc/modprobe.d/blacklist
```

and add to the file that pops up the line:
```

blacklist ndiswrapper
```

and remove the lines that say:
```

blacklist b43
blacklist ssb
blacklist b43legacy
blacklist b43 ssb
```

---

### Post by tunznath on 2008-06-12
Thanks for the info on the wireless - will see what I can do with it - nice that you gave me a way to get back to my current setup - compiz right now is almost unusable - weird because I have enough RAM, and also weird that Mandriva works and that DreamLinux works excellently - you should see it - the live CD even has a dock and everything works great - maybe ??? nah stick with what I got.
I must say that Linux is a bit of a mission to get working - so until I can get the scanner and wacom working I will need a windows partition to do stuff.

Thanks again

---

### Post by tunznath on 2008-06-12
Hi
OK i found the driver for the USB wirelss stick - its a rt2500usb.sys file - cant find the .inf do I need that? - I also looked on the disk that came with the adapter, and couldnt find any rt2500.inf there. Maybe will search again.

---

### Post by tunznath on 2008-06-12
as for the bad 3D performance is there a way that you could manually adjust the ram or cache or something for the video card?

---

### Post by pytheas22 on 2008-06-12
> as for the bad 3D performance is there a way that you could manually adjust the ram or cache or something for the video card?

Yes, you can specify values for different things and put them in /etc/X11/xorg.conf, but it's not a fun time figuring out what you need to put in, and for different drivers you might need different values.  Take a look at the [xorg man page]("http://linux.die.net/man/5/xorg.conf") if you really want to try, though.  If you're not happy with the performance of your card, you should install the proprietary driver, however, instead of trying to play with xorg.conf.  Lacking the proprietary driver is what's slowing the card down.  The ATI open-source driver is only really supposed to provide 2d effects; with some cards it's capable of providing 3d acceleration more or less, but results vary.  ATI/AMD won't release many specifications on its hardware so there's only so much that the open-source developers can do with it.
> 
OK i found the driver for the USB wirelss stick - its a rt2500usb.sys file - cant find the .inf do I need that? - I also looked on the disk that came with the adapter, and couldnt find any rt2500.inf there. Maybe will search again.

When you select which driver to use, you're looking for the one with the .inf extension.  The .sys and .cat files need to be present in the same directory as well, but ndiswrapper will detect them automatically once you point it to the .inf file.  Also I'm confused; the rt2500 drivers are for cards with Ralink chipsets, not Broadcoms like yours.  Are you positive you're looking at the right drivers?  The lsusb that you provided earlier definitely didn't mention any Ralink chipsets.  Actually things would be a lot easier if it turns out that your chipset is made by Ralink.  But make sure there aren't any files with names that look like they might be Broadcom's--usually they look like "bcmXXXX.inf" or sometimes just "bXXXX.inf."

---

### Post by pytheas22 on 2008-06-12
Also to help make sure that you definitely have a Broadcom card, can you plesae post the output of:

```
sudo lshw -C Network
```

I'm getting a little confused about this the more I read on the Internet.

---

### Post by blazercist on 2008-06-12
thats an rt2x00 wifi card, he shouldn't need to use ndiswrapper it should just work...  if not there is an opensource RT driver, google serialmonkey.

---

### Post by tunznath on 2008-06-12
Hi Pytheus
I booted into windows and went to the device properties of the wireless adapter, and it said the driver was a ralink rt2500usb - then i went to win32 drivers and searched for the driver and copied it  - also i checked on the CD that came with the stick and it had the driver there - do you know how I can double check it in windows.

BTW i cant find the .inf file I cant take booting to windows it takes like 5 mins to get in and another 5 to shut down!?!?!?

I will try a little later - also I did the compiz check script thing and got this
-----------------------------------------------------
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility 7000 IGP
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) y
nath@nath-laptop:~$ 

NOW--------------------------------------
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility 7000 IGP
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

nath@nath-laptop:~$

---

### Post by tunznath on 2008-06-12
googled serialmonkey and got this no 2500 usb there?
t2400 (PCI/PCMCIA)

Last beta release: v1.2.2-b3
CVS hourly tarball: rt2400-CVS
[edit]
rt2500 (PCI/PCMCIA)

Last beta release: v1.1.0-b4
CVS hourly tarball: rt2500-CVS
[edit]
rt2570 (USB)

Last beta release: v1.1.0-b2
CVS hourly tarball: rt2570-CVS
[edit]
rt61 (PCI/PCMCIA)

Last beta release: v1.1.0-b2
CVS hourly tarball: rt61-CVS
[edit]
rt73 (USB)

CVS hourly tarball: rt73-CVS

---

### Post by tunznath on 2008-06-12
Hi
would direct rendering being off have anything to do with compiz not playing ball???
see this
nath@nath-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


and how do I set it to verbose???

thanks

---

### Post by blazercist on 2008-06-12
> **tunznath said:**
> googled serialmonkey and got this no 2500 usb there?
t2400 (PCI/PCMCIA)

Last beta release: v1.2.2-b3
CVS hourly tarball: rt2400-CVS
[edit]
rt2500 (PCI/PCMCIA)

Last beta release: v1.1.0-b4
CVS hourly tarball: rt2500-CVS
[edit]
rt2570 (USB)

Last beta release: v1.1.0-b2
CVS hourly tarball: rt2570-CVS
[edit]
rt61 (PCI/PCMCIA)

Last beta release: v1.1.0-b2
CVS hourly tarball: rt61-CVS
[edit]
rt73 (USB)

CVS hourly tarball: rt73-CVS

lol im pretty sure 2570usb will cover it :)

---

### Post by pytheas22 on 2008-06-12
Yeah, it definitely looks like an rt2500 chipset.  I don't know lspci and lsusb didn't mention it.  Fortunately RaLink cards do have good Linux support.  The default drivers that come with Ubuntu have some issues, but you can blacklist them and use serialmonkey and that may improve your signal strength.  The ndiswrapper method could work too, but I'd try serialmonkey.  Run this to install:
```

sudo apt-get install build-essential rutilt
sudo echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
sudo echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
sudo echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
sudo echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
sudo echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
sudo echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
sudo echo 'ndiswrapper' >> /etc/modprobe.d/blacklist
```

If your wireless card is an external USB stick:
```
wget http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz
```

If your wireless card is internal:
```
wget http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz
```

```
tar -xzvf rt*
cd rt*/Module
make
sudo make install
```

Reboot and see how the new connection works.  Note that you won't be able to use Network Manager with this driver; you have to use a utilty called "Rutilt" built especially for serialmonkey drivers.  You can launch it from System>Administration.

I'm sorry for leading you down the wrong path before...I didn't see any mention of anything besides Broadcom chipsets...but it's clear now that serialmonkey should be the answer.  Let me know how this goes.

Also I'll look into the compiz stuff too as soon as I get a chance (if I don't, remind me).  The information you gave above for that is very useful.

---

### Post by RAOF on 2008-06-12
> **pytheas22 said:**
> ...
If you're not happy with the performance of your card, you should install the proprietary driver, however, instead of trying to play with xorg.conf.  Lacking the proprietary driver is what's slowing the card down.  The ATI open-source driver is only really supposed to provide 2d effects; with some cards it's capable of providing 3d acceleration more or less, but results vary.  ATI/AMD won't release many specifications on its hardware so there's only so much that the open-source developers can do with it.
...

1) The proprietary driver no longer supports his card, so that's not going to work :).

2) The open-source 'radeon' driver certainly *is* designed to provide full 3D support, and there have been times when the 3D performance of the open-source drivers have exceeded that of the proprietary drivers, on certain cards at least.

3) ATI released full specs for his card (a radeon 7000 is an r100 or r200 chip, IIRC) ages ago.  ATI/AMD fairly recently (in the last year or so) released full specs for all their cards up to the r500 chips, which covers everything but the newer Radeon X3xxx's, or whatever stupid numbering scheme the latest cards are following.  ATI/AMD are also working with X hackers to improve the existing open-source drivers, and are either releasing soon, or have already released, the specifications for their r600 chips.

Open source support for ATI/AMD cards is improving quite rapidly because of this.

You might have been thinking of nVidia, who certainly aren't doing anything open-source friendly :(.

While this isn't very helpful for the original poster, I feel it's worth pointing out that ATI/AMD are actually working with the open-source community.  They're not quite as good as Intel at it yet, but they're much, much better than nvidia, and this should be recognised.

---

### Post by tunznath on 2008-06-13
Hi Pytheus
I ran all that code about blacklisting and got this output
----------------------------------------------------------
nath@nath-laptop:~$ sudo echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ sudo echo 'ndiswrapper' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
nath@nath-laptop:~$ 
--------------------------------------------------------------
Do I then run this command for the usb version - 
wget [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
even though i got all those permission denieds?

---

### Post by pytheas22 on 2008-06-13
> I ran all that code about blacklisting and got this output
----------------------------------------------------------
nath@nath-laptop:~$ sudo echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied

I don't know why that's happening, but if you run the command:
```

sudo -s
```

before running that code, it will work.

---

### Post by tunznath on 2008-06-13
Ok I did all that rebooted, and got 2 wireless things in the top bar - a new one that looks like an antenna, and after doing a scan can see my wireless network along with a lot of others - but whatever i enter in the ssid and the key I cant get it to connect - then there is the other one that was there before - the one with the blue balls that change to green when a connection is made  - the blue ball one scans and pops up a connect thing with the ssid and the wep wap hex key thing again - am I supposed to have both of these,
I cannot connect using either of these.
If this doesnt work How do i go back to what i had - is this going to work?

Thanks 
Nathan

---

### Post by tunznath on 2008-06-13
If I cant get this to work and cant go back to what I had how do I reinstall ubuntu, I am using my windows partition at the moment to access the net

---

### Post by blazercist on 2008-06-13
ok the reason for this is that you have two network managers running, namely nm-applet(blue orbs) which is built in and probably rtutil (antenna thing) you need to remove network-manager package and try again.

---

### Post by tunznath on 2008-06-13
OK I shut down went to the shop came back and now it works Many thanks to pytheas22 and all who helped- the network manager with the blue balls that change to green is still there, but it has a orange triangle in it with a exclamation mark - so do i still need to remove it

---

### Post by pytheas22 on 2008-06-13
> OK I shut down went to the shop came back and now it works Many thanks to all who helped- the network manager with the blue balls that change to green is still there, but it has a orange triangle in it with a exclamation mark - so do i still need to remove it

No, Rutilt and NM should be able to coexist--they do for me--you just can't use NM for the wireless card that you have.

I'm glad you got this working finally and sorry for all of the confusion.  Is your wireless signal stronger now (that was the whole point of going through this originally, I think)?

---

### Post by tunznath on 2008-06-13
This driver works much better - 88% signal from the wireless box in the other room - before it was about 5m away in direct site of the computer and it was only getting about 30 -40% signal and kept dropping out - thanks again

---

### Post by tunznath on 2008-06-13
much better signal now thank you and no need to apologise about the confusion - the computer was confused saying it was a broadcom card

---

### Post by tunznath on 2008-06-13
does it need to be setup each time or will it connect automatically

---

### Post by pytheas22 on 2008-06-13
> does it need to be setup each time or will it connect automatically

Unfortunately Rutilt won't connect automatically, but you can work around this problem by running a command to connect every time you log into Gnome (or every time the computer boots if you want, but Gnome is easier).  The script could look something like this:
```

gksudo rutilt wlan0 -p PROFILE-NAME -d
```

where PROFILE-NAME is the name of a profile that you configured and saved in Rutilt to connect to your home network.

Then add that command to the list of things to be run when you log in to Gnome using the utility at System>Preferences>Sessions.

You can add some more arguments to the command to make Rutilt behave the way you want; take a look at its man page if you're interested.

---

### Post by tunznath on 2008-06-13
Great I will try that - main thing is its great to have wifi working right - thanks

---

