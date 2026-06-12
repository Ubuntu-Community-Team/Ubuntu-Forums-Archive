---
title: "Wireless network on a laptop"
date: 2006-01-31
forum: Desktop Environments
---

### Post by BlackJack on 2006-01-31
I am new to Linux in general and am trying to setup and run Breezy Badger (5.10) on a Dell Latitude D610 with the Dell 1350 802.11b/g WLAN mini PCI card. This card has a Broadcom chipset and is the only piece of hardware, that I can tell, that Ubuntu was not able to automatically recognize and configure. Can anybody help me out with support for this card? I have heard that Broadcom is not supported under Linux in general because Broadcom will not release thier driver code, but the hard-wired network card on the mother board is also a Broadcom chipset and it was recognized and works just fine.

If this card cannot be supported how about the IntelPro Wireless 2200 802.11b/g card with the intel chip set, I can get that for about $25.00 if it will solve my problem.

Thanks.........

---

### Post by mjunior on 2006-01-31
Have u tried to install the libiw and wireless-tools packages?

I'm running a much worst pc then yours, a A900 PC-Chips desknote with Dlink Wlan USB card on it..
Can't see why those libraries won't recognize your card as well..

Regards.

---

### Post by BlackJack on 2006-01-31
Yes, it's already installed.

Thanks for trying..........

---

### Post by icarius on 2006-01-31
Hola fellow Dell user. The fix is quite easy, I have recently done it myself. Use synapti c to download ndiswrapper including the graphicaly interface, which is a seperate package. You will then need the windows driver files, bcmwl5.ini , .sys, and .inf , three seperate files. Put all of these files into a folder somewhere on your box. Go to System, Admin.., and Windows Wireless Drivers, install the driver, then configure it with underneath networking, and poof!!!! you are jacked in. 
Icarius

PS let me know if you have a hard time finding the files, I can get them to you

---

### Post by dsierpin on 2006-01-31
icarius-

I have bcmwl5.sys in WINDOWS/system32/drivers, but I can't find the other two files (bcmwl5.inf, bcmwl5.ini).  I downloaded the GUI ndiswrapper, and it wants the .inf file.  Another post used netbc564.inf, but I don't have that file either.  Can you tell me where I can download bcmwl5.inf and bcmwl5.ini?  Thanks a lot in advance!

---

### Post by icarius on 2006-01-31
Are you searching for the driver files in windows or nx?

---

### Post by BlackJack on 2006-01-31
icarus,
Glad there is somebody else out there who has Dell....

I only have the .sys and .inf files, no .ini file. I went ahead and put these two files on my system and when I tried to "install new driver" it allowed me to select the apropriate .inf file but it never showed up in the list of "Currently installed Windows Drivers". 

My assumption is that I either grabbed the wrong version (yes, I also have them on there for the older 1150 card) or it is not working because of the lack of an .ini file.

If you could e-mail me (tcotariu@ix.netcom.com) the files you got to work I'll try them.

Thanks........

---

### Post by icarius on 2006-01-31
Enroute Senior BlackJack. :~)

---

### Post by BlackJack on 2006-01-31
Thanks, got the file but still the same result, it doesn't show up in the list of installed drivers. I went to the terminal and ran ndiswrapper -l but it shows that there are no drivers installed. i have thought about trying to install it manually with ndiswrapper rather than using the gui, but I am afraid i'll mess it up without an example.

Any other ideas?

---

### Post by icarius on 2006-01-31
Did you put them all into one folder and them install the .ini file using the GUI and then configure your network with the configure network from the ndiswrapper?

---

### Post by BlackJack on 2006-01-31
The problem seems to be with the GUI. when I went to the terminal and ran "ndiswrapper -i bcmwl5.inf" it did install teh driver and it now shows up in the list of installed drivers adn indicates that the hardware is there. unfortunately, when i go to "Configure Network" it is not listed in the network configuration tool. My guess is that I now have to use the other command line options to assign a deivice id and MAYBE write config for modprobe (no idea what this is) and MAYBE generate the hotplug information (again not sure what this is).

Anyplace I can get more information on ndiswrapper or get an example of how to configure it?

Thanks.........

---

### Post by dsierpin on 2006-02-01
icarius-

Thanks anyway, I got it working.  

Just pulled bmcwl5.inf off of the emergency backup driver DVD that came with Windows, put it into the same folder as bmcwl5.sys (/home/dsierpin/WindowsDrivers) and ran "sudo ndisgtk" after setting up the ndiswrapper GUI with automatix.  My wireless card shows up in the list of network adapters and works splendidly now. \\:D/   

Thanks again for the response.

---

### Post by BlackJack on 2006-02-01
I removed the partial install of the driver and then tried what dsierpin did and received the following error:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Anybody have any ideas?

---

