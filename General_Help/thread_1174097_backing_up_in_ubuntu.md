---
title: "backing up in ubuntu"
date: 2009-05-30
forum: General Help
---

### Post by Sparky-da on 2009-05-30
hi guys,
 
is there any way to backup ubuntu files from windwos x.p?
coz I can't access ubuntu anymore.

---

### Post by Rocket2DMn on 2009-05-30
You can install a driver that can read ext2/3 filesystems - [http://www.fs-driver.org/](http://www.fs-driver.org/)
During installation you will select a drive letter, and you may need to reboot after installing it.  The page says it is for ext2 filesystems, but it also works for ext3 (it just doesn't journal).

---

### Post by ajgreeny on 2009-05-30
> **Sparky-da said:**
> hi guys,
 
is there any way to backup ubuntu files from windwos x.p?
coz I can't access ubuntu anymore.
What exactly do you mean by "can't access ubuntu"?  You should be able to easily run the Ubuntu live CD and find all your files, which you can then copy to a USB drive, or anywhere else, again using the live CD.  But why can't you access the Ubuntu install?  If you have simply lost grub we can restore that easily with the live CD.  Tell us what the problem is and more help may come your way.

---

### Post by Sparky-da on 2009-05-30
I can't access [COLOR=darkorange]ubuntu[/COLOR] according to this error I have posted earlier there.
 
[http://ubuntuforums.org/showthread.php?t=1174023](http://ubuntuforums.org/showthread.php?t=1174023)
 
its getting on my nerves...there is no much support for [COLOR=darkorange]ubuntu[/COLOR]..unlike [COLOR=blue]windows[/COLOR].

---

### Post by ajgreeny on 2009-05-30
You installed using wubi, am I correct?  It certainly looks that way from your original post you refer to in post #4.  I think that may present some dificulties as I know of no way to open the compressed file or folders of a wubi installed Ubuntu.  There may be a way, but I'm afraid you will have to wait for others to answer as I have no clue.

---

### Post by Sparky-da on 2009-05-31
thanks man...
about waiting...I think I'll wait forever!

---

### Post by VMC on 2009-05-31
Have you tried burning something like Knoppix or Parted Magic. Then boot up with that mini-distro and mounting Windows then look for your Wubi directory and see it its still intact. If so then you could use partimage to back it up.

---

