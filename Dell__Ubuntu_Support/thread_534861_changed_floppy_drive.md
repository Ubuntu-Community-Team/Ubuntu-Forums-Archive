---
title: "changed floppy drive"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by martianvamp on 2007-08-25
I have a dell dimension 2350. Had to put a new floppy drive in and now  I am not listed as owner. I can't get it to work at all. Where can I go to change owner from unknown to my self?

---

### Post by iggykoopa on 2007-08-25
try from the commandline :
sudo chown [your username] [path to drive]
if that doesnt work for you try:
sudo nautilus
 then go to the drive right click and select properties and go to the permissions tab and you can change it there

---

### Post by martianvamp on 2007-08-25
don't know what the path is but will try sudo nautilus. thanks.

---

### Post by martianvamp on 2007-08-26
tried the sudo. didn't work. could'nt find the drive.

---

### Post by martianvamp on 2007-08-26
found drive. changed permissions,but they do not hold. still can't use floppy. any other idea's?

---

### Post by martianvamp on 2007-09-06
DOESN'T ANYONE KNOW HOW TO CHANGE PERMISSIONS IN 7.04?

i WENT INTO ROOT TO DO IT BUT THE CHANGES DID NOT TAKE. THEY DO NOT HOLD ANY WHERE.:confused::confused:

---

### Post by gbrainin on 2007-09-07
I'm not entirely sure what you mean by not being listed as owner.  If you're talking about the floppy disk icon in the file browser window, I can confirm that on mine when you right-click that, select Properties, and go to the Permissions tab, it does list the owner as unknown.

However, that has not stopped me from using the floppy drive.  The drive mounts at /media/disk, and that directory is owned by me.  I am able to read and write to the drive without a problem.

---

### Post by Afishionado on 2007-09-07
Are you talking about

1. The icon that automatically appears in Nautilus/the desktop,
2. The device file, or
3. The mount point?

What do you mean by it not working? Can you tell us what kind of error messages you get?

---

### Post by martianvamp on 2007-09-11
It tells me I can read only. will not let me write at all. I changed all of this in root and it will not hold. It returns to read only.
I am about to give up on linix and go back to windows. Can't get any help any more.

---

### Post by martianvamp on 2007-10-10
IS THERE ANYONE OUT THERE THAT HAS SOME BRAINS AND TELL ME HOW TO FIX MY PROBLEM? :confused::confused:

---

### Post by gbrainin on 2007-10-11
I obviously don't have any brains, but have you considered that this might be a hardware problem?  I know floppies are a pretty well-tested technology, but the first floppy drive I had in my computer was bad, and led to some strange errors that looked like software but went away when I swapped out the drive.

---

