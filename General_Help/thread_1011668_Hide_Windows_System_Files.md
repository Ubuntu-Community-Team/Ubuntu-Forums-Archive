---
title: "Hide Windows System Files"
date: 2008-12-15
forum: General Help
---

### Post by dlew86 on 2008-12-15
Is there a way to hide XP system files on my external hdd without having to rename them. I see the recycling bin, and a bunch of desktop.ini files along with a few others that are just annoying to look at. I would just delete them but I still use XP from time to time. I've checked out [this]("http://ubuntuforums.org/showthread.php?t=1010403") thread but it really wasn't all that helpful. Any help would be appreciated.

---

### Post by hikaricore on 2008-12-15
If you make a text file called:  **.hidden**

On the drive in question, you can type the names of whatever files or folders you don't want to be shown in Nautilus and save it.
Upon a refresh any filename you typed in that document should be hidden.

---

### Post by studavis on 2008-12-28
Thank for the tip, works well but if I want to hide the Windows folder, its not possible to add all the files names. I tried wildcards e.g. *.exe and *.* but to no avail. any ideas?


Edit:

Just i case anyone else is looking for solution, it was pretty obvious once I thought about it. Just make a .hidden file in root of c: drive and add all the folder names you want to hide. (don't forget names are case sensitive)

---

