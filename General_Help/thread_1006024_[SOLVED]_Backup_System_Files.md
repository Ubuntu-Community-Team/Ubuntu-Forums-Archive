---
title: "[SOLVED] Backup System Files"
date: 2008-12-08
forum: General Help
---

### Post by fparedesg on 2008-12-08
Hey everyone! I am going to format my computer, but before that, I want to backup all of my system files. I want to keep all of my personal preferences for the next time I install Ubuntu (say, CompizConfig's preferences and options). Which directories should I backup? Should I just drag/drop the folder to my external hard drive? Or should I use a specific program?

Thanks to anyone that helps! I hope I made myself clear..

---

### Post by albinootje on 2008-12-08
Is your external disk using a Linux file-system ? or is it FAT formatted ?
If the latter, it's a good idea to create archives of /home/ and /etc/ and copy those archives to your external disk.

---

### Post by Sorivenul on 2008-12-09
You may find [this guide]("http://www.psychocats.net/ubuntu/backup") useful.

---

### Post by fparedesg on 2008-12-09
> **albinootje said:**
> Is your external disk using a Linux file-system ? or is it FAT formatted ?
If the latter, it's a good idea to create archives of /home/ and /etc/ and copy those archives to your external disk.

It's NTFS formatted.

---

### Post by fparedesg on 2008-12-09
> **Sorivenul said:**
> You may find [this guide]("http://www.psychocats.net/ubuntu/backup") useful.

Thanks for the link, it looks helpful, but I which files should I backup to keep the program's settings (like CompizConfig). I know I should backup /home/username, but which other directory should I backup?

---

### Post by Sorivenul on 2008-12-09
Most of your "configuration" settings for GNOME, Compiz, and so on, are stored in hidden folders in your /home.  Backing up your /home directory should include these files.  Your /etc directory could be included as well, as other various configurations (X11, networking, and so on) are stored there.

---

