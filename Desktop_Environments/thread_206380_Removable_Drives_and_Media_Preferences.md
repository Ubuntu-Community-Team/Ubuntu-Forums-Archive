---
title: "Removable Drives and Media Preferences"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Grundlebug on 2006-06-30
Hello,

I've changed my preferences for audio cd, blank cd, and ipod a number of different times as I've tried various jukebox type programs.  I've had a little trouble going back and forth.

What do the %h, %m, and %d placeholders stand for?  I seem to be having some trouble with configuration because of these.

Sometimes my Audio CD will show up on the desktop when I insert it, but then it quickly disappears.  If I have sound-juicer set as my default audio cd program, the cd info will flash into the program and then disappear, but if I just click "rescan disk" it all comes right back.

Thanks in advance for the tips.

---

### Post by Grundlebug on 2006-06-30
Okay, I've narrowed down part of my problem.

If I already have banshee open when I insert a CD, the CD automounts, shows up on my desktop and in banshee, and then disappears!

If banshee is closed when I insert a CD, banshee opens up, the Cd automounts, and shows up on my desktop and in banshee and doesn't disappear.

Anyway to solve this?

---

### Post by quill3033 on 2008-04-30
Did anyone ever answer this question? Was there somewhere else that it needed to be posted? 
I hope so for your sake and also I'm interested in the answer. :-)

---

### Post by bilal.17 on 2008-04-30
Yeah i am interested in the answer to this as well, more information is needed!

---

### Post by keenboy on 2008-05-22
Auto-open files on new drives and media

    Enable this option to make of auto-open capabilities of certain removable drives and media. See the Desktop Application Autostart Specification for details about the auto-open mechanism. To enhance security, you will always be prompted to confirm the auto-open. 

The remaining options allow you to specify a command to run when a certain kind of media is inserted into a drive or a certain kind of external device is connected. The command can use three special variables, that will be substituted when the command is run:

%d

    Each appearance of %d in the command will be substituted with the device file path of the newly added device. For example, if you have plugged in an USB stick, the device file path will be /dev/da0s1 or /dev/sda1.

    If no device file is associated with the device or the device file could not be found for some reason, the variable %d will be substituted with the empty string. 
%h

    Each appearance of %h in the command will be substituted with the HAL UDI of the newly added device. 
%m

    Each appearance of %m in the command will be substituted with the mount point where the newly added device was mounted. If the device cannot be mounted (for example printers or keyboards) or if the automatic mounting was disabled, %m will be substituted with the empty string.

---

