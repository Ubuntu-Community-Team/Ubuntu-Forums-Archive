---
title: "can I reformat my windows program"
date: 2006-01-13
forum: General Help
---

### Post by angeleyes on 2006-01-13
Can I reformat my Windows XP program without losing Ubuntu?
I need to reformat XP because I somehow lost a boot file (<Windows root>/system32/hal.dll.)and I dont have a disk to pull the file from so it only gives me the option to Reformat.
I recently found Ubuntu and like the way it works but I still like some Windows programs that Ubuntu doesnt have.

---

### Post by nocturn on 2006-01-13
If you do this, windows will overwrite the master boot record, so you can no longer boot Ubuntu.

You can recover this with a LiveCD, but it requires some comands...

---

### Post by earobinson on 2006-01-13
This will be a pain becasue windows will overwrite the MBR when you insall it, you way want to check this out: [http://www.ubuntuforums.org/showthread.php?t=114812&highlight=mbr+grub+linux](http://www.ubuntuforums.org/showthread.php?t=114812&highlight=mbr+grub+linux)

---

### Post by angeleyes on 2006-01-13
ok so now my question is this ...if I reformat XP, and reinstall Ubuntu will I have 2 Ubuntus?

---

### Post by nocturn on 2006-01-13
[QUOTE=angeleyes]ok so now my question is this ...if I reformat XP, and reinstall Ubuntu will I have 2 Ubuntus?[/QUOTE]

You don't have to reinstall Ubuntu, it will be untouched.  You'll have to rerun grub so it gets back in the MBR.

---

### Post by nocturn on 2006-01-13
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

This explains the procedure

---

### Post by angeleyes on 2006-01-13
Will I need the Ubuntu disk to reinstall GRUB?-I no longer have it as I got it from a friend who was here visiting from out of state-he just left yesterday and took the disk with him.

---

### Post by nocturn on 2006-01-13
[QUOTE=angeleyes]Will I need the Ubuntu disk to reinstall GRUB?-I no longer have it as I got it from a friend who was here visiting from out of state-he just left yesterday and took the disk with him.[/QUOTE]

Yes, you do.

Do you have any other Linux boot disk?  Or you could download it yourself...

You can order an Ubuntu CD, but it'll take 4 to 6 weeks to arrive.

---

### Post by angeleyes on 2006-01-13
can I download the program from the internet and boot it that way?

---

### Post by nocturn on 2006-01-13
[QUOTE=angeleyes]can I download the program from the internet and boot it that way?[/QUOTE]

You'll need to download the Ubuntu ISO images and burn them to a CDR.

---

### Post by angeleyes on 2006-01-13
ok ..so where do I find those?(I feel silly but im still really new to Ubuntu)

---

### Post by Titus A Duxass on 2006-01-13
Take a look at the top of this page (right hand corner) it says download Ubuntu.

---

### Post by angeleyes on 2006-01-13
thanks got it

---

