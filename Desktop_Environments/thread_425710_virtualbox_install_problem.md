---
title: "virtualbox install problem"
date: 2007-04-27
forum: Desktop Environments
---

### Post by merlinus on 2007-04-27
I tried installing virtualbox from the feisty deb, but it did not complete.  The installation dialogue box remained on the screen interminably, and then would not close.  So I restarted, logged back in and now synaptic will not run, claiming it has to be reinstalled but the archive cannot be found.

In a terminal, I get the following error message when running

sudo apt-get remove virtualbox

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

Help greatly appreciated!!!

-merlin

---

### Post by llamakc on 2007-04-27
If you install via dpkg you need to remove via dpkg.

---

### Post by merlinus on 2007-04-27
I tried this before posting my original message.

sudo dpkg -r virtualbox
dpkg: error processing virtualbox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox

When I try to reinstall it from the deb, it tells me I do not have the correct privileges.  This is untrue.

Thanks....

-merlin

---

### Post by llamakc on 2007-04-27
It is true if you forget to use sudo.

---

### Post by merlinus on 2007-04-27
OK, and many thanks!

I set up virtualbox using the gui, added myself to the vboxusers group, logged off and back in, and when trying to start the vm get this error msg:

VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups.

Help appreciated!

-merlin

---

### Post by kyphi on 2007-04-27
Type this in your terminal window:

sudo chmod 666 /dev/vboxdrv

then log out and back in.

---

### Post by merlinus on 2007-04-27
OK.  This got me to the point where I could start the vm, but then I got this error msg:

FATAL: No bootable medium found! System halted.

The hard disk I created is listed as Primary Master.

Here are the settings:

General
Name
Win2000
OS Type
Windows 2000
Base Memory
128 MB
Video Memory
8 MB
Boot Order
Hard Disk
ACPI
Enabled
IO APIC
Disabled
 
Hard Disks
Primary Master
Win2000.vdi [Normal, 3.91 GB]
 
Floppy
Not mounted

CD/DVD-ROM
Not mounted

Audio
Adapter
ALSA Audio Driver
 
Network
Adapter 0
NAT
 
USB Controller
Device Filters
0 (0 active)
 
Remote Display
Disabled
 

Enable ACPI is checked.

Thanks hugely for your assistance!

-m

---

### Post by kyphi on 2007-04-28
You will have to change your boot sequence.  The usual sequence is

Floppy
CD/DVD
Hard Drive
none

otherwise, virtualbox will not be able to read the installation CD.

All your other checks are OK.

---

### Post by kyphi on 2007-04-28
I forgot to add that to change the boot sequence in VB go to

Settings -> General -> Advanced

Click on none and on the resulting dropdown menu select floppy.  Change the others accordingly.

---

### Post by merlinus on 2007-04-28
I changed the boot order as you recommended.  Does that mean my win2000 installation disk has to be in the cd-rom drive before starting the vm?

I was hoping to use my existing win2000 installation, rather than starting over (I have a dual-boot setup).  And I seem to remember reading somewhere that this is possible....

Thanks again!

-m

---

### Post by kyphi on 2007-04-28
Yes, you need to install your chosen version of Windows on to the virtual disk.  Start VB, then go to "New" and follow the prompts.

I have been successful in using Windows programmes in Ubuntu that are essential to me via Crossover.  There was only one programme left (PhotoImpact) that I needed to run in VB and it works perfectly.

Windows now is only a bare bones installation used for gaming - no internet, no antivirus, no updates and no snooping from MS.

I am not aware of an answer to the question of whether or not an existing installation of Windows can be run in VB - I know that a lot of people are asking just that.

---

### Post by merlinus on 2007-04-28
I managed to load Win2000 and the one program I need that will only run under that OS.  Although it seemingly installed correctly, it would only work for a short time before crashing.  Shutting down and restarting windows did not help.

Also, I was unable to copy files from other partitions into the vm.  Perhaps this is a shortcoming of Virtualbox?

When VMWare updates its workstation for Feisty, I will give it a try.

But for now, at least, I will have to keep my dual-boot setup..... sigh.

Thanks very much for your assistance and expertise.

-merlin

---

### Post by kyphi on 2007-04-28
I am sorry to read that things did not work out.  Following are two URLs that may answer some questions:

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

[http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html](http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html)

Both links refer to managing VB in Feisty.

Which programme are you trying to run in VB?  Perhaps it would run via CrossOver.

Sharing files is definitely possible.

---

