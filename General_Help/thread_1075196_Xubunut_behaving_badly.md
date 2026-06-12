---
title: "Xubunut behaving badly"
date: 2009-02-20
forum: General Help
---

### Post by Xtudent on 2009-02-20
I am newbie that installed Xubuntu 8.10. I have not done anything to my system (other then normal updates) after installation and now my system is going slowly to hell.

Programs have started to crash regularly, disc access can be lost (Windows XP has no problem with the same physical drive nor it's FAT32 partion). Files can't be copied like expected, several programs has problems with reading files correctly, the Xfce is losing configurations, etc. etc.

I assume that it must be something wrong with the handling of the file system that causes all of these symptoms but I have not nearly enough understanding of how Linux operates to neither figure out what is wrong nor how to fix it. This problem also seems to effect all portions mounted and also other media like my DVD.

What can possible bee wrong and how do I fix it? I still want my user account intact if possible, mainly since I want to know how to fix things and preserving data without backing up first for future needs (have things gone wrong once they might again).

I have an AMD Athlon 2500+ (32 bit version) with 512 MB RAM and sufficient disc space.

---

### Post by Xtudent on 2009-02-20
Due to my problem my panels crashed. Seen a question about how to restore the original panel in the archive and since I can't reply there I thought it might be of interest and decided to post how I solved that problem (that was caused by my system behaving badly in general.

1.  I opened a terminal.

2.  I opened the System Monitor and ended the process Xfce4-Panel.

3.  Used the terminal to remove xfce4/panel

4.  Started Xfce4-panel using sudo.

5.  Restarted the system.


After that my original panel was restored :-)

---

