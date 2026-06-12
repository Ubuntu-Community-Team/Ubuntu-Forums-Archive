---
title: "Ubuntu Freezes after ~30 min"
date: 2006-08-16
forum: Desktop Environments
---

### Post by buddy_krish on 2006-08-16
I prefer downloading large files at nights.....I just keep the file for download and ignore the comp for 8 to 9 hrs..I used to do that in Windows...But in Ubuntu after 30 min or so....The system just hangs up and I have no other option but to restart the system again. 

This is bothering me because Im not able to downmload larg files when Im away... :-(

Please help me.

~Krish

---

### Post by Valacosa on 2006-08-16
I used to have the same problem on my Thinkpad. Try this fix:
[LIST]
[*]Open up /etc/X11/xorg.conf
[*]Find the bit in xorg.conf that says
[INDENT]Section "Device"[INDENT]
	Identifier	"ATI Technologies (blah blah blah...this is probably hardware specific)"
	Driver		"ati"
	BusID		"PCI:1:0:0"[/INDENT]
EndSection
[/INDENT]
[*] change **driver "ati"** to be **driver "vesa"** and you should be all set. That's the fix that worked for me in Ubuntu 6.06 at least. 
[/LIST]

---

### Post by buddy_krish on 2006-08-17
I'm not on ATI.... :-(

Here is how it is........

=======================

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"

=======================

---

### Post by buddy_krish on 2006-08-17
No Update yet.... :-(

I dont think thats ant Video drivers problem...

---

### Post by lagagnon on 2006-08-17
Is your machine dual boot? Have you recently tried doing the same thing in Windows on the SAME machine? The reason I ask is that I bet you have a HARDWARE problem, not a software/OS problem.

If I were you I would load a Live CD (Knoppix, Slax, Ubuntu) onto your computer and try a large overnight download - after mounting a  partition on which to save the file. If you still get crashes you definetely have a hardware problem - probably in this order:

1) DIMM memory modules faling
2) hard drive failure
3) overheating (remove all dust from inside and heat sinks, renew CPU heat sink compound)
4) power supply failing.

Larry, A+ certified tech.

---

### Post by buddy_krish on 2006-08-17
My System is pretty new and is a Dual boot...

I have Xp and recently installed Ubuntu.....ive stopped using Windows Completly after having Ubuntu....Its just there on ma sys.....

I doubt if there would be any damage to the Hard drive or any other hardware component as it is pretty new....Hardly 3 months since I brought the system....

How do I go about "Load the CD and try an overnight download"...U want me to boot over the CD and then Try download?????

---

### Post by cptnapalm on 2006-08-17
Is the system set to hibernate or sleep after that period of time?

---

### Post by buddy_krish on 2006-08-19
Nope....Nothing.....

---

