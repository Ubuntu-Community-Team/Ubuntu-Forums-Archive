---
title: "Gnomebaker: format DVD+RW problem"
date: 2005-11-23
forum: Desktop Environments
---

### Post by VosaxAlo on 2005-11-23
Hi,

I have a laptop Dell Inspiron 5150 with a DVD+RW writer, and I have a Sony DVD+-RW external writer.
I use the Ubuntu Breezy distro and I have installed GnomeBaker 0.42-1
I tried to format a DVD+RW with the internal DVD writer and I receive this error message:
-----------------------------------------------------------------------------------
* DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
-lead-out to elicit lead-out relocation for better
DVD-ROM compatibility, data is not affected;
-force to enforce new format (not recommended)
and wipe the data.
--------------------------------------------------------------------------------------



I tried to format a DVD+RW with the external Sony DVD writer and I receive this error message:
-----------------------------------------------------------------------------------
* DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD+RW media detected.
umount: /media/cdrecorder not found in fstab (not root)
Sad unable to proceed with format: Device or resource busy
--------------------------------------------------------------------------------------

no way to blank the DVD+RW and use it!

can you help me?
many thanks

---

### Post by dcstar on 2005-11-23
[QUOTE=VosaxAlo]Hi,
......
no way to blank the DVD+RW and use it!

can you help me?
many thanks[/QUOTE]
What do you see in Edit-Preferences-Devices?

---

### Post by VosaxAlo on 2005-11-24
[QUOTE=dcstar]What do you see in Edit-Preferences-Devices?[/QUOTE]

Thank's to Ubuntu backports I have updated GnomeBaker from version 0.42-1 to 0.5.0-3, but the problem remain.

Attached to this message I send you an image with the Preferences/Devices.
I have tried to import a session from a DVD+RW and a long error message  is displayed. I have attached this message too.

thank's a lot for your help.

---

### Post by metoo on 2005-11-24
Might not be an option for you, but people report success with k3b.
(That's a KDE application and will most likely install quiet some stuff if you choose to try it)
Never hat a problem with it (Kubuntu user that I am).

---

