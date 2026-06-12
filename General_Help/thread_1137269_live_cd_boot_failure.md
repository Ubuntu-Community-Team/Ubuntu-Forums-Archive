---
title: "live cd boot failure"
date: 2009-04-25
forum: General Help
---

### Post by 123456789123456789123456 on 2009-04-25
Hi, I have just built a computer with a PC Chips A15G motherboard.  I started up with the 9.04 ubuntu live cd.  It started up the menu, I went to try ubuntu part.  It started like it was going to load.  Came up with that it expected something, 0 detected, then went to the built in shell.

I was able to use xubuntu 8.10 live cd, it booted into the live desktop, but gave an incorrect video resolution, of only 800x something.  Is Ubuntu not comapatable with the motherboard video card?  Why did 9.04 fail to boot?
but 8.10 did?

---

### Post by overdrank on 2009-04-25
> **123456789123456789123456 said:**
> Hi, I have just built a computer with a PC Chips A15G motherboard.  I started up with the 9.04 ubuntu live cd.  It started up the menu, I went to try ubuntu part.  It started like it was going to load.  Came up with that it expected something, 0 detected, then went to the built in shell.

I was able to use xubuntu 8.10 live cd, it booted into the live desktop, but gave an incorrect video resolution, of only 800x something.  Is Ubuntu not comapatable with the motherboard video card?  Why did 9.04 fail to boot?
but 8.10 did?

Hi and have you checked the cd for errors and also check the iso with [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by 123456789123456789123456 on 2009-04-25
it's something I don't understand.  You see I used the same cd to install on a dell machine, a dimention 2400 desktop, it booted and installed without a hitch.  I don't understand what is happening now.  I also don't understand why a earlier copy of 8.10 xubuntu actually boots.  When I downloaded 9.04 I downloaded it the day it came out, when I got home, I found that the download stalled, and I had to tell firefox to pause and resume download, it resumed at last point and finished.  I don't know if that could have had a problem or not.
I am willing to try and download another iso, now since the downloading of 9.04 has libale to have slowed down by now.

---

### Post by overdrank on 2009-04-25
Hi and I am not saying you need another download. I am just giving some options to try. If you can give some more info on the specs of your system may help also. 
It could be the cd drive or many other things as I just suggested to start with the checksum. :)

---

### Post by 123456789123456789123456 on 2009-04-25
well, I know that xubuntu 8.10 live cd boots the system, but does not give correct video resolution.

the system is motherboard PcChips A15G Am2+/AM2
Chipset NVIDIA MCP61P/MCP61S
mem 2gb

I don't know what other information to provide.

---

### Post by 123456789123456789123456 on 2009-04-25
would the error message give more help?  I can try booting again and copy that down.

---

### Post by 123456789123456789123456 on 2009-04-25
This is the error message I get, when attempting any loading of the os, to check the cd, to load live, or anything

[1.086412] ACPI: Expecting a [Reference] package element, found type 0
loading please wait. . . . 

BusyBox v1.102 (Ubuntu 1:1.10.2-2 ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

---

### Post by 123456789123456789123456 on 2009-04-25
this us an update, I downloaded another copy, tested checksums, which checksums matched, same error attempting boot.  I am unsure what the problem is.  I have found an alternate install cd, and will attempt a direct install onto the system.  I hope that the boot problem is something interfering with the live boot, that would not accure with a full install on the system.

If not, I will have to chuck this one up to defective motherboard, and replace it.

---

### Post by 123456789123456789123456 on 2009-04-26
well, seems no one knows.
I have now downloading a new copy of 8.10, since for some reason it boots and runs the live cd, but with incorrect drivers for video.

I also assuming that for some reason completely unknown to me, that the cd will not work because it is attempting to boot on a 64bit machine, which makes no since since the 32bit 8.10 boots.
I am downloading 9.04 64bit
if not, I will probably have to get a more compatable motherboard.

---

### Post by 123456789123456789123456 on 2009-04-26
I appolagize about last post.  No one wrote back, and I was getting upset.  however weird thing happened.  I did get it to install 8.10 with incorrect drivers, under oem install.  It updated itself to 9.04.  Which after words, configured the video correctly, and booted the machine correctly, however it went up and asked for user name and password
don't know exactly why it did that.  Still no sound, testing the sound card through other means, to see if it is just a driver issue.  The cd's however still never boot, I can't explain why that is.

---

### Post by 73ckn797 on 2009-05-22
> **123456789123456789123456 said:**
> This is the error message I get, when attempting any loading of the os, to check the cd, to load live, or anything

[1.086412] ACPI: Expecting a [Reference] package element, found type 0
loading please wait. . . . 



I get the same message but everything is working normally. I was searching for the meaning of this message and found this thread.

---

