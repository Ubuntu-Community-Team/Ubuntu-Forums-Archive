---
title: "Access denied to scanner"
date: 2009-03-15
forum: General Help
---

### Post by MadMax2 on 2009-03-15
I wasn't sure which section this goes in.

I'm using 8.10
I tried to use XSane Image Scanner and when I tried to select the scanner Microtect Scanmaker 3840 I got this message:
Failed to open device:SM3840:libusb:002:002: Access to resource has been denied.
Thanks
Max

---

### Post by MadMax2 on 2009-03-15
3.4.&#8195;Manually installing a scanner

There are some scanners that have less than complete drivers from the SANE project. They can sometimes be used, but not all the features may work.

   1.

      Make sure the Universe repository is enabled. The easiest way to do this is probably through Synaptic.
   2.

      Get the drivers by searching Synaptic for libsane-extras or at a terminal type:

      							


      sudo apt-get install libsane-extras


      							
   3.

      Edit the /etc/sane.d/dll.conf and enable the right driver for your scanner. Look for the lines that say:

      							


      # The following backends are not part of the SANE distribution
      # but are provided by the libsane-extras Debian package


      							

      						

      Below it are several commented out lines. Uncomment (delete the #) the right one for your scanner.
=================
I don't understand how to do step 3. I typed /etc/sane.d/dll.conf in terminal it said Permission denied.

---

### Post by MadMax2 on 2009-03-15
"Unsuported"? [Microtek Scanmaker 3840]

---

### Post by oldos2er on 2009-03-15
Check System, Administration, Users and Groups, User Privileges, and make sure 'Use scanners' is checked.

---

### Post by MadMax2 on 2009-03-15
I did that and I was the only one without (several) privileges, but I am still getting the same message.
Thanks Ie I'm the only one who has used the system but I have added 2 other users. All the boxes in "user Privileges" are checked for me.

---

### Post by oldos2er on 2009-03-16
"I don't understand how to do step 3. I typed /etc/sane.d/dll.conf in terminal it said Permission denied."

 It's a text file you need to edit:
```
gksu gedit /etc/sane.d/dll.conf
```

---

### Post by MadMax2 on 2009-03-16
Thanks for that but there was no # in front of microtek or microtek2

[# Edit the /etc/sane.d/dll.conf and enable the right driver for your scanner. Look for the lines that say:

# The following backends are not part of the SANE distribution
# but are provided by the libsane-extras Debian package
Below it are several commented out lines. Uncomment (delete the #) the right one for your scanner.]


Max

---

### Post by DoctorMO on 2009-04-26
Max it's because the scanner is owned by root and your not allowed to use it.

You have to make sure that the scanner has the required udev rules in /etc/udev/rules.d/ this tells the computer to treat the scanner like a scanner and add it to the scanenrs group (which you should be a part of to use the scanenr)

Make sense?

---

### Post by alonbr on 2009-10-06
I did something to workaround this problem (a known bug):
first I:
```
Myname@Myname-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 00X Device 002: ID 04f9:0182 Brother Industries, Ltd Composite Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Than I:
```
$ mk bin
$ nano FixBrother
[INDENT]gksudo chmod a+w /dev/bus/usb/00X/*
xsane
```
[/INDENT]Than: Ctrl+x
Y
And now for the Grad finnale:
(under GNOM GUI)I went to: System -> Prefrences -> Main Menu
on Graphics I double clicked on XSane Image scanning program and changed command to:
/home/*Myname*/bin/FixBrother
Now everytime I open: Applications ->Graphics -> Xsane... it asks for root password and open xsane as user.
Obviously not good enough if you don't want to give your user the root password, but a workaround alright.
Good luck

---

### Post by DoctorMO on 2009-10-06
AlonBr, that is not the right way to do it. For a few reasons.

When you change the permissions in the first command, that will be lost when you reset the machine or cycle the power on the scanner (or unplug it and replug it). What you want is to have the machine issue the correct permissions when plugged in, this is what udev security groups are for.

The second thing as you point out, is that you should never have to use your root password (which doesn't exist) or your password to become root in order to use devices. Escalation of privileges is a security risk every time you do it.

Without the proper security group in place, you'd never be able to fix the problem properly for everyone. Push at the bug reports to get the problem concluded so the next version of Ubuntu this problem goes away.

---

### Post by hyperhelium on 2010-06-26
> **DoctorMO said:**
> Max it's because the scanner is owned by root and your not allowed to use it.

You have to make sure that the scanner has the required udev rules in /etc/udev/rules.d/ this tells the computer to treat the scanner like a scanner and add it to the scanenrs group (which you should be a part of to use the scanenr)

Make sense?

Actually that should be the right way to do it. I had the same problem in Jaunty and now in Lucid. I had to modify the udev rules in order to be able to access the scanner without root privileges. I wrote a new file in the /etc/udev/rules.d/ named "70-basic-permission.rules" with the following content:

# This file is made for the SCANNER
#
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"


You do this in gedit and save the file with the .rules extension. Of course it'll work if you have a printer that is plugged via usb.

I must make the observation that the number you start the file name with is important, since I first named it "40-basic-permission.rules" and it didn't work. After I read the "READ ME" file within the folder I noticed that it said:

1) Write your own rules in this directory that assign the name,
    symlinks, permissions, etc. that you want.  [B]Pick a number higher
    than the rules you want to override, and yours will be used.[/B]

I renamed the file with "70" and it worked well.

Anyway I'm not a senior Linux user, but this worked pretty well. I hope this helps somebody. ):P

---

### Post by DoctorMO on 2010-06-26
Your solution will work, but it does break the security on the scanners. Technical we should be setting the group of the device and then making sure users are in that group.

You are in the scanners/sane group right?

---

