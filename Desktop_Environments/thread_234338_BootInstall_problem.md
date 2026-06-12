---
title: "Boot/Install problem"
date: 2006-08-11
forum: Desktop Environments
---

### Post by jkerr on 2006-08-11
Hi all, I'm having problems installing Ubuntu 6.06 i386 from the live/install CD.  It won't get very far at all in the boot process.

I have an eMachines T6212 system: (this info from SiSoftware Sandra app)
AMD Athlon 64 3200+, 1.99 GHz
1.5 GB Ram
2 Hard drives
video card - NVIDIA GeForce 6600 GT
network card - Realtek RTL8139 Family PCI Fast Ethernet NIC (onboard)
audio - Realtek AC'97 Audio
I believe it has on-board video too, but I didn't jumper anything to disable it, winXP just picked up the new one...
Mainboard info:
MP APIC: yes
System BIOS: Phoenix Technologies, LTD 255.255
Mainboard: MS-7093 (pretty sure it's this one: [http://www.msicomputer.com/product/p_spec.asp?model=RS480M2-IL]("http://www.msicomputer.com/product/p_spec.asp?model=RS480M2-IL") )

Here's what happens when I boot from the CD:

I get the menu, and choose the first option, to boot or install.
I get the popup "Ok booting the kernel" message
I see some text flash on a black screen, I believe these are the first PCI errors, below...
The splash screen shows, and at the bottom it reads "Loading essential drivers... OK", "Mounting root file system..." and it sits there for several minutes.
It comes back to text on a black screen with:[COLOR="Blue"][FONT="Courier New"]
PCI: cannot allocate resource region 3 of device 0000:00:00:0
PCI: cannot allocate resource region 3 of device 0000:00:00:1[/FONT][/COLOR]
then after a bit:[COLOR="Blue"][FONT="Courier New"]
hdc: ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hdc, logical block 357296[/FONT][/COLOR]

After scanning the forums I also tried the [COLOR="Blue"]irqpoll [/COLOR]boot parameter, same thing.  Also tried [COLOR="Blue"]nolapic[/COLOR], but that just gave several other messages first, then the above...

I've also tried the amd 64 install/boot CD without luck...

Any ideas?  Thanks!
Jeff

---

### Post by SEMW on 2006-08-11
When I installed Ubuntu, I also got a "Buffer I/O error on device xxx, logical block xxxxx" error message, except it cycled every second or so with a new logical block number.  I found when I left it for about 3/4 of an hour, it resumed booting, and never did it again.  See [http://www.ubuntuforums.org/showthread.php?t=208342](http://www.ubuntuforums.org/showthread.php?t=208342).  Hope this helps...

---

### Post by chedabob on 2006-08-11
friend of mine had a similar problem. he ran it in safe graphics mode and it worked fine.

---

### Post by jkerr on 2006-08-11
Thanks for the ideas,

Tried letting it sit for a while, and the buffer I/O problem happens for about a half-hour but then my monitor lost sync, so I don't know what happened after that point... didn't look good...

Tried safe graphics mode as well (tried it before but wanted to make sure the errors were the same) - same errors...

---

### Post by jkerr on 2006-08-12
Not sure if this helps or not, but at a friend's suggestion I tried a SUSE 10 live CD and that booted fine...

---

### Post by jkerr on 2006-08-14
Well, looks like both suggestions actually worked :) 

First time I let it sit, I left the room and returned later to a monitor out of sync, so didn't know what happened.  I decided to try it again to see if there was anything else before that happened, and the boot process continued after about 10 minutes, then gave me some weird graphics glitches.  So I tried booting in safe graphics mode AND waiting the 10 minutes until the errors passed, and voila, it booted!

So thanks for the replies!

---

