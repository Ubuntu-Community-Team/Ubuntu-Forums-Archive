---
title: "New to Linux; Need help setting up wireless"
date: 2006-09-07
forum: Desktop Environments
---

### Post by bg1256 on 2006-09-07
I've read several guides, [such as this one]("http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#driver"), but I'm feeling a little lost and overwhelmed.

I'm completely new to Linux, and I'm running Ubuntu 6.06.

My computer is an HP DV 1000 notebook, if that's useful -- I'm not even sure.

If anyone is aware of any useful resources, I would greatly appreciate the help!

---

### Post by bg1256 on 2006-09-08
Well, I have successfullly done a few things.

I have identified my wireless card:
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation.

Does anyone know how I can get my card activated?  I'm still searching, but I can't seem to figure out how.

---

### Post by someguyouknow on 2006-09-08
I think you need to use ndiswrapper along with the driver for the card. I am not sure exactly how to do it but the guys on the link below know how to do it very well (one has a tutorial for broadcom cards).
[http://forums.pcpitstop.com/index.php?showforum=7](http://forums.pcpitstop.com/index.php?showforum=7)

p.s. for faster results, message bruce.

---

### Post by bg1256 on 2006-09-19
> Get the two files 

bcmwl5.inf

bcmwl5.sys

Install ndiswrapper

Then to install the drivers run the command

ndiswrapper -i /path_to_driver 

ndiswrapper -m
These are the commands I ran, with the advice of someone from a different forum.  It seemed to work correctly, but where do I go from here?

---

### Post by cemptor on 2006-09-20
ndiswrapper -l should say "driver installed, hardware present"

sudo depmod -a
sudo modprobe ndiswrapper

If no errors, check dmesg to make sure ndiswrapper loaded correctly.

Go ahead and activate your network interface, and you should be good to go (assuming you've set up the authentication WPA/WEP/none)

---

### Post by bg1256 on 2006-09-20
Hmmm... well ndiswrapper says the drivers are not installed.

Perhaps the commands I posted earlier were not the correct ones?

---

### Post by cemptor on 2006-10-01
> **bg1256 said:**
> Hmmm... well ndiswrapper says the drivers are not installed.

Perhaps the commands I posted earlier were not the correct ones?

The command is correct. After you install ndiswrapper,

sudo ndiswrapper -i <path_to_driver> 

MAke sure you point to the .inf file and not the .sys file, and both .inf and .sys files are located in the same folder

If the driver is the wrong one, ndiswrapper will warn you. That's the only thing that could be wrong

---

### Post by Crooksey on 2006-10-01
After you install the driver type "ndiswrapper -l" to see if the installed driver is valid and matches your hardware.

---

### Post by bg1256 on 2006-10-01
Thanks to all.  I finally did get it up and running :rolleyes: Couldn't have done it without help, though.

---

