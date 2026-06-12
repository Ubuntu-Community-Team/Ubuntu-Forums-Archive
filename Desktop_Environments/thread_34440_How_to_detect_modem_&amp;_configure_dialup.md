---
title: "How to detect modem &amp; configure dialup"
date: 2005-05-14
forum: Desktop Environments
---

### Post by davefr on 2005-05-14
I stumbled onto Kppp and configuring dialup doesn't seem too difficult but I can't find a way to make Kubuntu detect my generic modem. (PCI).

It's not shown under peripherals and I can't find anything such as an "add hardware" option.

The Ubuntu User's Gude seems to ignore modems.

I need both broadband and dialup.  The broadband/ethernet detection has been flawless but how the heck do I enable my modem and use dialup. 

There's also a utility on startup that seems to want to check the time  and it goes into an long "do loop" unless the internet connection is already active.  This means ultra long boot if an always on internet connection is not active.  How do I get rid of this time check until after boot up??

TIA

---

### Post by britbrian on 2005-05-15
davefr

I'm am possibly having the same problem. The kppp configure looked OK, but kppp initially connects then discconnects with unexpected kppp daemon death err 1. 'man pppd' doesn't explain err 1 any better.

However since I installed Kubuntu from an Ubuntu install, I had already used the Gnome 'networking' app ie:  'gksudo network-admin' to cfg the modem connection. Alas when I first hit activate, my connection speed was about a 1/4 of expected 48kbps. Another poster here suggested doing pppconfig in a root shell to properly cfg  '/etc/ppp/peers/provider' and that worked. I presume a Kubuntu install would have the 'networking' tool also.
Rather than put an icon for 'networking' in the panel to activate / deactive the connection (which also uses its icon for notification), I installed GNOME-ppp which is functionally more like kppp and similarly uses the tray for notification.

However, I'd still prefer to use kppp if anyone can help.

---

### Post by britbrian on 2005-05-15
Whoops I just re-read your post and I see your (PCI) refference to it being an internal winmodem.
For info & links for many winmodems you could check [www.linmodems.org](www.linmodems.org) or [http://start.at/modem](http://start.at/modem). For pctel, Conexant or Lucent based winmodems respectively, see - [http://pctelcompdb.sourceforge.net](http://pctelcompdb.sourceforge.net), [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) or [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem).
Last I checked linuxant drivers were about $15 or $0 for a qtr? speed version.  I bought an external analog modem (inc S&H) for $20 instead via a pricewatch.com listing.

---

### Post by mrshark on 2005-05-15
[QUOTE=britbrian]The kppp configure looked OK, but kppp initially connects then discconnects with unexpected kppp daemon death err 1. 'man pppd' doesn't explain err 1 any better. [...snip...]Alas when I first hit activate, my connection speed was about a 1/4 of expected 48kbps.[/QUOTE]
i've exactly the same behaviour... :-(

---

### Post by davefr on 2005-05-15
I found 3 modems in my "junk box".  All 3 are cheap winmodems.

One's based on Lucent, one's Conexant, and the other is Pctel.

Would the Lucent one give me the best chances of success?

Would any of these be possible to install with Synaptic or apt-get?

---

### Post by jodef on 2005-05-15
Please check my post in this link : [Kppp Error ](http://www.ubuntuforums.org/showthread.php?t=30808)

---

### Post by ludi on 2005-05-15
[QUOTE=davefr]I found 3 modems in my "junk box".  All 3 are cheap winmodems.

One's based on Lucent, one's Conexant, and the other is Pctel.

Would the Lucent one give me the best chances of success?

Would any of these be possible to install with Synaptic or apt-get?[/QUOTE]


Ok, lets go.
All should work on Linux but (there is always a "but") you should check the modem model.
I'm using a Lucent now, I got a little time to setup it, but works.
Whatever, check this links to more information:
General help and Lucent drives (check this first):
[http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html)
Rockwell/Conexant:
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)
PCTEL:
[http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)

There are already many threads and wikis about this three modems (and compiled drives in ubuntu/debian repositories).
If you couldn't setup the modem, just leave a comment here and we'll help you.

---

### Post by ludi on 2005-05-15
PPP problem:
Change the auth to noauth on /etc/ppp/options, should fix the problem of authentication.

---

### Post by britbrian on 2005-05-15
Thanks jodef & ludi for the noauth tip in /etc/ppp/options. Now connecting  happily with kppp.

---

### Post by davefr on 2005-05-15
I selected the Lucent Winmodem and installed all the drivers per this guide:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

When I do lspci -vv it's listed,

When I go to Kppp and select dev/ttyS0 it's there and seems to respond to modem query but it doesn't return any values.  It also doesn't make any sounds or complete a connection when I dial.

When I go to Kppp's mini terminal it initializes and resets but I can't enter anything in the window like an AT command.

It seems like I'm pretty close but for some reason it won't repond correctly.  I know the hardware works because I can switch to my Win XP hard drive and it works just fine.

Any tips would be appreciated.

---

### Post by ludi on 2005-05-15
[QUOTE=davefr]I selected the Lucent Winmodem and installed all the drivers per this guide:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

When I do lspci -vv it's listed,

When I go to Kppp and select dev/ttyS0 it's there and seems to respond to modem query but it doesn't return any values.  It also doesn't make any sounds or complete a connection when I dial.

When I go to Kppp's mini terminal it initializes and resets but I can't enter anything in the window like an AT command.

It seems like I'm pretty close but for some reason it won't repond correctly.  I know the hardware works because I can switch to my Win XP hard drive and it works just fine.

Any tips would be appreciated.[/QUOTE]
 Like I've said before, there is always a "but". You must know what model of modem you have. Lucent's V92 works just in Windows.
Use the ScanModem from ltmodem page to detect what kind of model you have.

---

### Post by davefr on 2005-05-15
This is what scanmodem is telling me:

Modem candidates are at PCI_buses:  0000:00:0c.0
    
Providing detail for device at PCI_bus 0000:00:0c.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:0440   Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
  SubSystem 11c1:0440   Lucent Microelectronics LT WinModem 56k Data+Fax+Voice+Dsvd
0000:00:0c.0 0780: 11c1:0440 (rev 01)
	Flags: bus master, medium devsel, latency 0, IRQ 255
	Memory at e5800000 (32-bit, non-prefetchable) [disabled] [size=256]
	I/O ports at 9400 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0440 11c1:0440 debian 2.6.10-5-386 3.3.5     i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:0440

---

### Post by ludi on 2005-05-15
[QUOTE=davefr]This is what scanmodem is telling me:

Modem candidates are at PCI_buses:  0000:00:0c.0
    
Providing detail for device at PCI_bus 0000:00:0c.0
  with vendor-ID:device-ID
     ----:----
Class 0780: 11c1:0440   Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
  SubSystem 11c1:0440   Lucent Microelectronics LT WinModem 56k Data+Fax+Voice+Dsvd
0000:00:0c.0 0780: 11c1:0440 (rev 01)
 Flags: bus master, medium devsel, latency 0, IRQ 255
 Memory at e5800000 (32-bit, non-prefetchable) [disabled] [size=256]
 I/O ports at 9400 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0440 11c1:0440 debian 2.6.10-5-386 3.3.5     i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:0440[/QUOTE]
Yes, I think that is supported, is the same version of my modem.
Try this thread form AZZ:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)
There are another threads about.
If didn't work, try to compile your own module.
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

I used the compiled drives, and create the devices by my self.
Give a try.

---

### Post by davefr on 2005-05-15
Thanks, I did exactly what the first link suggested.

As far as the second link it would be easier to design a rocket then figure out what he's saying.

I'm still a newbie that can't connect.

[QUOTE=ludi]Yes, I think that is supported, is the same version of my modem.
Try this thread form AZZ:
[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)
There are another threads about.
If didn't work, try to compile your own module.
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

I used the compiled drives, and create the devices by my self.
Give a try.[/QUOTE]

---

### Post by ludi on 2005-05-16
>  Thanks, I did exactly what the first link suggested.
 
 As far as the second link it would be easier to design a rocket then figure out what he's saying.
 
 I'm still a newbie that can't connect.
 

Lol, I didn't know that.
Well look this quote:
> 
[http://www.ubuntuforums.org/showthread.php?t=32183&highlight=lucent+modem](http://www.ubuntuforums.org/showthread.php?t=32183&highlight=lucent+modem)
\/ \\/ \\/ \\/ 
 DID IT! 
 
 I finally did it. Compiled the drivers (alk-7) and they really work fine, thanx to them I'm writing this from ubuntu. Hope this distro continues to evolve like it has been doing so fine so far. Congrats to the people responsible for this. For the first time I feel good looking forward to leave winblows behind.


This guy have compiled the drives by him self and could get the modem working.
To me was a little wired. I've boot up with pci=route (something like that) option and I started to make my own module but I didn't reach the compilation part, I got an error before it (but I just had created the modem devices, ttyLM0 etc...) then I restarted the pc and vualá the modem just
works.
This what I did, following the read me of Alk-7 source:
> 
You may need to create /dev/ttyLTM0 if you haven't used 2.4 version
of driver or if you don't use udev. Just do:
a. mknod --mode=0660 /dev/ttyLTM0 c 62 64
b. Change owner and group owner to match /dev/ttyS0
 (Debian users: set group to dialout) (so Ubuntu too)
c. Create symlink /dev/modem to it ('ln -s /dev/ttyLTM0 /dev/modem')
If you use udev, than read docs/udev-setup and skip this step.
OBS: I've had the binaries modules already installed :)
So a source compilation should work, but you may try this too.

Bu before he said:
> 
Anyway. I did got the default Hoary drivers properly loaded and "working", but looks like they have some bugs and they simply doesn't connect. The modem dials and everything, but I never get a real connection and the line hangs up about 20 seconds after the handshake and stuff. I hope this gets fixed in the next Ubuntu. \\/ 
 
 Then I got to read some chat about the "alk-7" drivers, downloaded them, but unfortunately I'm still a beginner with linux, and wasn't able to compile them properly. Is there a "step-by-step" tutorial on that? The README is obviously not for beginners.
 
So you can do it too :)

---

