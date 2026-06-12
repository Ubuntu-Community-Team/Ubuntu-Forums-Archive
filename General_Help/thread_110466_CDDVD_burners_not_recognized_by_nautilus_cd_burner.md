---
title: "CD/DVD burners not recognized by nautilus cd burner"
date: 2005-12-30
forum: General Help
---

### Post by justinjstark on 2005-12-30
I started up my computer today and was going to back up my data to dvd when I found that nautilus cd burner was not recognizing my burners anymore.  It worked flawlessly a few days ago.

If I go to system->administration->disks both of my drives are there.  They are both listed as CDROM but they have the correct Supported Features.  ie: Write CD-R, write DVD, etc.

When I go to Computer in nautilus it shows both of my drives as "CD-ROM" and "CD-ROM/DVD-ROM Drive" rather than "CDRW/DVDRW" or whatever it usually shows.

When I open nautilus-cd-burner (cd/dvd creator) and go to write a disk I only have the option of writing to a file image.  Neither of my burners are shown.

Gnomebaker is working fine but I really want to get nautilus cd burner going again.

Any ideas on how to diagnose this issue?

EDIT: Oh, btw, I just recently unplugged my floopy drive (who uses a floppy these days?) from my motherboard and took it out earlier today.  I have a feeling this could have caused gnome to get confused.  ???

---

### Post by justinjstark on 2005-12-30
At the very least does anybody know where gnome stores the information about removable media so maybe I can edit it by hand?

---

### Post by justinjstark on 2005-12-30
Nevermind...removing the floppy entry from fstab and rebooting did the trick.  Everything is working fine now.  :)

---

