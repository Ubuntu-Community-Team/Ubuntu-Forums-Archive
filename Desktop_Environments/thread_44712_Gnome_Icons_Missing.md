---
title: "Gnome Icons Missing"
date: 2005-06-27
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-06-27
yesterday i was using Gnome and all of a sudden the icons in the menu are all messed up, i tried to reboot but its still all messed up,  when i say messed up its missing.....when i login to ubuntu i get two error boxes, one says "Failed to load image gnome-help.png" and the other says "Failed to load image evolution", ii used aptitude to get rid of gnome and to reinstall it but the icons are still missing, can anyone help ?

---

### Post by intangible on 2005-06-27
Did you do anything at all to the machine since you last rebooted the computer? installed any software?  Even something that you wouldn't think was related could be.  Do you know what filesystem you're using, do you think you might have corrupted it?

What does **df -Th** show?

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=intangible]Did you do anything at all to the machine since you last rebooted the computer? installed any software?  Even something that you wouldn't think was related could be.  Do you know what filesystem you're using, do you think you might have corrupted it?

What does **df -Th** show?[/QUOTE]


nah nothign i havent done anything to it, when i typed 

df -Th

this is what it says:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda2     ext3     18G   13G  3.8G  78% /
tmpfs        tmpfs    500M     0  500M   0% /dev/shm
/dev/hda1     ntfs     19G  5.1G   14G  28% /mnt/C
/dev/hdb1     ntfs    112G   69G   44G  62% /mnt/D
/dev       unknown     18G   13G  3.8G  78% /.dev
none         tmpfs    5.0M  2.8M  2.3M  56% /dev


all i can remember doign was i did update the kernel using syanptic and it was fine after rebooting....i was playing unreal tourney2004, and then the game crashed...shortly after the icons were missing....

---

### Post by intangible on 2005-06-27
When UT2004 crashed, did you have to hard reboot your system?

Did you remove any themes recently?

Does this command show anything?:
**sudo updatedb;locate gnome-help.png**

If it does, can you open those icons manually by browsing to the location?

Do you still have "gnome-icon-theme" installed?

Sorry for so many questions, it'd be easier if I was in front of your computer :D

One last thing: Try creating another user, log in as that user and see if the icons show up.
**System->Administration->Users and Groups**

Let me know

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=intangible]When UT2004 crashed, did you have to hard reboot your system?

Did you remove any themes recently?

Does this command show anything?:
**sudo updatedb;locate gnome-help.png**

If it does, can you open those icons manually by browsing to the location?

Do you still have "gnome-icon-theme" installed?

Sorry for so many questions, it'd be easier if I was in front of your computer :D

One last thing: Try creating another user, log in as that user and see if the icons show up.
**System->Administration->Users and Groups**

Let me know[/QUOTE]
 yea i had to hard reboot

nah i did not remove any themes

when i locate gnome-help.png here is what it shows
/usr/share/icons/hicolor/48x48/apps/gnome-help.png
/usr/share/icons/hicolor/16x16/apps/gnome-help.png
/usr/share/icons/hicolor/24x24/apps/gnome-help.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/gnome-help.png
/usr/share/icons/HighContrastLargePrint/48x48/apps/gnome-help.png
/usr/share/icons/LowContrastLargePrint/48x48/apps/gnome-help.png

yea i can open them, i've only checked a few, but those that i checked i can open and view

i went to synaptic and i checked if i have gnome-icon theme installed and it is installed, so i marked it for re-installation just now and i logged out and back in, but still no luck, icons are still messed up.

i am usually logged in as root, and upon installin ubuntu i had to create a main user (non root user) and i logged in with that just now and the icons are still missing and the same error messages show up.

i dont mind the questions :)

---

### Post by DarkManX4lf on 2005-06-27
bump

---

### Post by intangible on 2005-06-27
Try an alternate theme too... I'm starting to run out of ideas :D

Can you launch an individual program and have it give an error message about the icons?

If you can, we may be able to do something with "strace"

---

### Post by DarkManX4lf on 2005-06-27
[QUOTE=intangible]Try an alternate theme too... I'm starting to run out of ideas :D

Can you launch an individual program and have it give an error message about the icons?

If you can, we may be able to do something with "strace"[/QUOTE]
 hmm i tried different themes and any prog i launch it doesnt complain about the icons...

---

### Post by intangible on 2005-06-28
if you "killall gnome-panel" does it complain when it comes back up?

---

