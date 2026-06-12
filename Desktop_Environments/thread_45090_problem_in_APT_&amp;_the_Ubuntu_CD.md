---
title: "problem in APT &amp; the Ubuntu CD"
date: 2005-06-28
forum: Desktop Environments
---

### Post by ^NoX on 2005-06-28
why does apt insist that i`ll insert the Ubunyu CD into the drive?
can`t it download the program im asking (KSIRC) from the web?

something weird, that when i did: "apt-get install nvidia-glx" it downloaded it from the internet.
and when ive entered the same command @ my friend computer, it says to insert the cd..

why is that happening? tha alot :)

---

### Post by angkor on 2005-06-28
if you don't want to install from the cd, you need to comment it out in your apt sourcelist:

/etc/apt/sources.list

---

### Post by Bil-E-daKid on 2005-06-28
Hey there!

I've experienced similar things and it's all to do with your apt sources file.

Edit the file (/etc/apt/sources.list) on your friends computer and remark out the line (usually near the top) that references the CD media.

Save that edited file and run a 'sudo apt-get update' and you won't be asked for the CD anymore.

:-)

---

### Post by ^NoX on 2005-06-28
thanx you very much!! i have managed to do it :)

---

