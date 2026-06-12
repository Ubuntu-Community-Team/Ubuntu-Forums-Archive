---
title: "how do I reinstall Kubuntu without losing my data?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by muzza on 2005-11-06
I rearranged my partitions while using Windows and now hoary Kubuntu won't start.  I get a message at startup saying something like 'kernel panic' and tried to 'kill' something.

I have the Hoary Kubuntu cd, but don't know how to reinstall without losing my data.  I've done a search, but can't find any answers.

Any advice?

---

### Post by mo_x on 2005-11-06
What did you change to your partitions? What data are you trying to save?

---

### Post by muzza on 2005-11-06
I was 'streamlining' my partitions.  I had way too many, so I copied all the files to the largest partition and reformatted the unused ones.

Anyway, I sorted it! I've been using OSX a lot in the past few weeks, and I've gotten a bit rusty on Linux - it isn't easy.   I remembered that my /home directory was on its own partition, so I reinstalled Kubuntu from the CD, but left the /home partition untouched.

All of my files are still there, but I'll have to reinstall a lot of programs.

I think I'm going to return to Macintosh OS - it's so straightforward.  I'll give Breezy a try before I commit entirely to OSX.

Anything but Windoze, eh??

---

### Post by teaker1s on 2005-11-10
reinstalling kubuntu-desktop will solve it

---

### Post by der_joachim on 2005-11-11
Hmmm... Sounds like you have to get a rescue disk somewhere, (Knoppix is excellent btw) and edit your /etc/fstab and /boot/grub/menu.lst. Point them to the right partitions and try to boot Kubuntu again. 

Disclaimer: I have not tried this myself, so I could be wrong.

---

### Post by hoy_pogi on 2005-11-12
there's an easier way I read in the forums. Go through the normal process of reinstalling kubuntu. At the partition setup screen, make sure you mount your partitions properly, go to the setup grub screen, and then abort install. It will reinstall grub and mount your /home, /, and other system partitions (if they exist).

---

