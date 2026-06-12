---
title: "plugged in a Microsoft wireless mouse, and lost my USB ports."
date: 2009-01-07
forum: General Help
---

### Post by klunk2009 on 2009-01-07
I have 6 usb ports on my computer. I got a wireless mouse for Christmas. I plugged it into a usb port and it worked right away. The problem is that the mouse is now the ONLY thing that any usb port will recognize. Does not recognize flash drives or my wireless internet receiver. Have tried to fix this own my own for a week, this morning I tried 

dmesg | tail:

[ 2563.034640] usb 4-7: new high speed USB device using ehci_hcd and address 2
[ 2563.146465] usb 4-7: device descriptor read/64, error -32
[ 2563.362099] usb 4-7: device descriptor read/64, error -32
[ 2563.577733] usb 4-7: new high speed USB device using ehci_hcd and address 3
[ 2563.689542] usb 4-7: device descriptor read/64, error -32
[ 2563.905174] usb 4-7: device descriptor read/64, error -32
[ 2564.120790] usb 4-7: new high speed USB device using ehci_hcd and address 4
[ 2564.528104] usb 4-7: device not accepting address 4, error -32
[ 2564.639917] usb 4-7: new high speed USB device using ehci_hcd and address 5
[ 2565.047224] usb 4-7: device not accepting address 5, error -32


lsub gives me this:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

and sudo fdisk -l only displays the partitions in my hard drive, not the flash drive that I plugged into a usb port.

right now I'm using a corded mouse plugged into the PS/2 port and still no usb recognition. As I said I've tried fixing this on my own for a week now, and or course searched the forums for help.

I have several partitions on my drive, Ubuntu is in one, and winXP is in another. Of course, in WinXP I can use the wireless mouse and at the same time access my flash drives and other things plugged into other usb ports.

Please help, and if you need more info I will provide. Thank you so much!

---

### Post by hangfire on 2009-01-07
> **klunk2009 said:**
> I have 6 usb ports on my computer. I got a wireless mouse for Christmas. I plugged it into a usb port and it worked right away. The problem is that the mouse is now the ONLY thing that any usb port will recognize. Does not recognize flash drives or my wireless internet receiver.

See if some ports are burned out. Try the other devices in the USB port that the mouse worked in. Try all the devices on other computers.

If you have an old i865 chipset motherboard, you may be suffering from the dreaded USB static related burnout.

-HF

---

### Post by klunk2009 on 2009-01-07
The wireless mouse receiver works in each of the 6 usb ports, so I don't think anything is burned out.
Other usb devices do not work in any of the ports - eg flash drive doesn't even light up.
The other devices work on my other computer, as well as this computer when I boot into WinXP.
I will not try the wireless mouse on my other computer because I'm sure this is what started the problem.

The people at Future Shop told me I needed a USB hub because the wireless mouse is sucking all the power from all USB ports, but I don't beleive that, because everything runs smooth in WinXP. It's just Ubuntu.

I also fired up Puppy Linux from a CD to troubleshoot:
-when the wireless mouse is plugged in, no other usb ports/devices are recognized
-when I use a corded mouse, all usb ports are recognized and useable.

The problem is that even if I throw the wireless mouse away, my USB ports would still be unusable in Ubuntu. Any ideas?

---

### Post by Loosewheel on 2009-01-07
I remember quite some time ago, Vista updated my network controller driver and I no longer had any network at all with Linux. Seems the driver turned the card off.....I rolled back the driver in Device Manager and all was well. Maybe take a look at this:

[http://ubuntuforums.org/archive/index.php/t-797789.html](http://ubuntuforums.org/archive/index.php/t-797789.html)

---

### Post by klunk2009 on 2009-01-07
Thank you for the lead! I booted into XP and no drivers have been installed or updated. I looked at the device manager, specifically usb controllers. I think there may be a few tweaks I can try there.

In the Ubuntu terminal I typed

sudo echo -1 >/sys/module/usbcore/parameters/autosuspend

but I got "permission denied".

---

### Post by The Cog on 2009-01-07
You have problems with pipes there. Sudo is doing the echo but the piping to the system is being done in your ID. Try this:
> sudo -i
echo -1 >/sys/module/usbcore/parameters/autosuspend
exit

---

### Post by klunk2009 on 2009-01-07
oh, thanks! Well, I typed that in, rebooted with the flash drive already in a port, and the flash drive still doesn't light up and won't let me mount it.

dmesg | tail shows:

[   45.929660] usb 4-7: device descriptor read/64, error -32
[   46.145309] usb 4-7: device descriptor read/64, error -32
[   46.360937] usb 4-7: new high speed USB device using ehci_hcd and address 7
[   46.472753] usb 4-7: device descriptor read/64, error -32
[   46.688403] usb 4-7: device descriptor read/64, error -32
[   46.904009] usb 4-7: new high speed USB device using ehci_hcd and address 8
[   47.311371] usb 4-7: device not accepting address 8, error -32
[   47.423144] usb 4-7: new high speed USB device using ehci_hcd and address 9
[   47.830471] usb 4-7: device not accepting address 9, error -32
[   50.050691] eth0: no IPv6 routers present


Another clue is that I used to pop a flash drive into my cold computer, turn it on, and on the startup screen it would say "boot sequence has been changed, press DEL to enter setup"...now when I start the computer with a flash drive plugged in, I do not get that message.

I've already looked hi and lo in the bios to find some magical setting that this stupid microsoft mouse could have changed.

I really appreciate all the help on this- I have lurked for a long time here and have been helped vicariously many times, but this is the first time I've hit such a hard wall that I was driven to post. Thank you.

---

### Post by klunk2009 on 2009-01-08
Still can't get my USB ports recognized in Ubuntu. Do you think the guys at Future shop were right and I need a USB hub? (but I already have 6 usb ports, why would I need more? and, the mouse has batteries in it, so it really shouldn't be hoarding all the USB power).

---

### Post by The Cog on 2009-01-08
I have no idea if the solution you are trying will work, but I am sure that changing configuration by writing to /sys is temporary. If you did manage to fix the problem, rebooting will have restored the original configuration. Just write the configuration and test to see if it worked. If it did, you will have to rustle up a way to make the change every time the machine reboots.

---

### Post by klunk2009 on 2009-01-23
Hi everybody,

well I still have not resolved this problem. As I said, I have 3 operating systems on my computer. In XP, the wireless mouse and flash drives can be used at the same time. In puppy linux, the flash drives are recognized if the wireless mouse is not plugged in. And in Ubuntu, my USB ports do not exist at all whether the wireless mouse is plugged in or not. In Ubuntu, the wireless mouse does work, but nothing else plugged in to any USB port is recognized.

This is really a hassle now because all my work is on my flash drives, obviously so I can wipe my computer without losing my files. I have to boot into XP, copy the files off the flash drive onto the hard drive, boot into Ubuntu, work with the files, save them on the hard drive, then boot into XP to copy the files back onto the flash drive. 

Has no one else encountered this type of problem with a wireless mouse?

---

### Post by DeMus on 2009-01-23
Sorry for this terrible answer, but Microsoft and Linux just don't work together. :p

---

### Post by klunk2009 on 2009-01-27
I don't know what I did, I don't think I did anything, but suddenly Ubuntu recognizes the flash drives.

However, I have to click 3 times on my wireless mouse to do anything.

and the wireless modem still isnt' working.

---

