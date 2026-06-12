---
title: "hardy stopped automounting CD's"
date: 2009-06-21
forum: General Help
---

### Post by VOLKOV9 on 2009-06-21
if I put a CD in, it spins a bit, but nothing happens.  Going into nautilus and clicking "cdrom0" mounts it and then it works fine.

Less imperatively, once mounted, pressing the physical eject button no longer does anything (it used to) - I need to right click the drive's icon and click eject.  

I've tried playing with gconf-editor to no avail (automount_drives, automount_media, show_desktop, volumes_visible).  My fstab has udf and no unhide option listed for the cdrom0 drive, but changing this does nothing.  (Well, anytime I change fstab, as soon as I save it, the computer mounts the CD drive.  This happens even when I change it back to the original.  But it doesn't make it _auto_mount.)

I've installed a bunch of programming libraries etc since last I noticed it working... nothing that obviously has anything to do with drives or mounting...

Thanks in advance!

---

### Post by ajgreeny on 2009-06-21
Have a look at the Media tab of **nautilus > Edit > Preferences**.  Maybe something has changed in the settings there for some reason.

---

### Post by VOLKOV9 on 2009-06-22
"Browse media when inserted" was already checked.  Thanks for the suggestion though.  Any other thoughts?

---

### Post by mc4man on 2009-06-22
Bit of a longshot here, though quite harmless.( Did help me with an amarok autoplay for cd's script that stopped working suddenly.

Anyway search hal in synaptic, you'll have to scroll down a ways. Highlight it and under packages tab you should be able to 'force version' (back to hardy version vs. hardy updates. 
Click force version and see if any change. (or restart and see.

(note that after the force version runs, when you go to exit synaptic it will try to update hal back to current, click cancel.

---

### Post by VOLKOV9 on 2009-06-22
That didn't change anything - thanks though.  But longshots are appreciated if anyone has more.

---

