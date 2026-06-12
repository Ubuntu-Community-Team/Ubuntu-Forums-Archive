---
title: "How to rename a UDF Volume?"
date: 2008-12-31
forum: General Help
---

### Post by Donalb on 2008-12-31
Hi all,
 I have two Iomega Rev drives ( 35gb & 70gb) that I use for backup/sneakernet.

They were originally formatted in Windows (using the Iomega Windows System Tools utility).
Rev use the UDF filesystem (same as optical), and Linux reads/writes it as default. However like an idiot, i.e. a long-term Windows User, I labelled the volumes ala "Rev 35" with the space instead of an underscore. I'd want to relabel the various volumes. So the question is: HOW?
Since, of course the space is causing problems in the CLI.
Of course, I could reboot into Wins and do it, but would prefer the linux way. 
Suggestions?

Regards

---

### Post by dcstar on 2008-12-31
> **Donalb said:**
> Hi all,
 I have two Iomega Rev drives ( 35gb & 70gb) that I use for backup/sneakernet.

They were originally formatted in Windows (using the Iomega Windows System Tools utility).
Rev use the UDF filesystem (same as optical), and Linux reads/writes it as default. However like an idiot, i.e. a long-term Windows User, I labelled the volumes ala "Rev 35" with the space instead of an underscore. I'd want to relabel the various volumes. So the question is: HOW?
Since, of course the space is causing problems in the CLI.
Of course, I could reboot into Wins and do it, but would prefer the linux way. 
Suggestions?

Regards

These are the Linux rename instructions, UDF is not listed:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Donalb on 2009-01-02
Thanks anyway David.
In terminal mlabel can't even read the current UDF label. With MountMan etc all I can do is mount/unmount.
I decided to just relabel in Wins anyway, added the underscore, but when I booted back to Intrepid, there was no sign of the underscore. I'm beginning to think the Rev 35 & Rev 70 labels are not those on the cartridges/volumes anyway but are passed by the drive as a ID string...  
So I might be out of luck. It's not a big deal but I was trying to delete an empty directory on the rev35 thru terminal (that i couldn't delete in Nautilus), but the space in the volume name was screwing with that.
I seem to recall there's an option that can be set to ignore the space in terminal so I'll go back and try that.

Regards

---

### Post by dcstar on 2009-01-02
> **Donalb said:**
> ........
I seem to recall there's an option that can be set to ignore the space in terminal so I'll go back and try that.

Regards

All strings with spaces should be surrounded by quotes in terminal commands.

---

