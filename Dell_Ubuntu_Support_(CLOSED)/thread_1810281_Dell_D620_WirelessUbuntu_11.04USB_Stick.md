---
title: "Dell D620 Wireless/Ubuntu 11.04/USB Stick"
date: 2011-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bayouoldguy on 2011-07-22
Copied from other post....G
Re: Wireless from USB /Ubuntu 

--------------------------------------------------------------------------------

Update 07/22/11 after some attempts to get a wireless working.
On page 3 , Step 3 Referenced Help page: "Instead of a computer restart, in a terminal
issue the following commands:
~$ sudo modprobe -r b43 ssb wl
~$ sudo modprobe wl
I could not get the terminal to accept an "Enter" command,
therefore the "restart" type of function could not be performed.
Any suggestions Ubuntu community ?....G

[I found the Help page : [https://help.ubuntu.com/community/Wi...river/bcm43xx?]](https://help.ubuntu.com/community/Wi...river/bcm43xx?])
( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys E2000 & can "hardwire" to the internet on the USB/Ubuntu load).
__________________

---

### Post by gordintoronto on 2011-07-23
I think that help page has been removed because it was obsolete. When you are hard wired, run Additional Drivers. It should fix you right up.

I can't figure out what this means:
"I could not get the terminal to accept an "Enter" command,"
"Enter" means, press the Enter key.

---

### Post by bayouoldguy on 2011-07-23
Would not accept "Enter" when key pressed !. No action.....


> **gordintoronto said:**
> I think that help page has been removed because it was obsolete. When you are hard wired, run Additional Drivers. It should fix you right up.

I can't figure out what this means:
"I could not get the terminal to accept an "Enter" command,"
"Enter" means, press the Enter key.

---

### Post by bayouoldguy on 2011-07-27
Heres what I did..........

( Running a Dell D620 w/Windows Vista Business , works fine thru Windows/Linksys E2000 & can "hardwire" to the internet on a USB/Ubuntu stick load).

i tried to access & set up Ubuntu 11.04 & my wireless net. was not able to "enter" any terminal commands changing the wireless setups. If I re-booted, I lost the settings in the USB stick.
Saw all the problems of others trying to get Wireless up & came to this conclusion:
I stopped trying to use the USB/Ubuntu 11.04 stick & went back and reloaded Ubuntu 10.04LTS. Was able to get up & running on Wireless after uninstalling "bcmwl-kernel-source" & "bcmwl-modaliases", then installing "b43-fwcutter", re-booting, configuring my Wireless SSID, Security as: WPA & WPA2 Personal & putting in the passcode. A re-boot started up the Wireless & showing ALL neighborhood nets !.
Therefore: I installed Ubuntu 10.04LTS on my Dell D620 until
the Ubuntu Team/users correct the Driver situation !..."G"

---

