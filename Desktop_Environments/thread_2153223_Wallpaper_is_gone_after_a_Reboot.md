---
title: "Wallpaper is gone after a Reboot"
date: 2013-06-10
forum: Desktop Environments
---

### Post by LSHINE on 2013-06-10
After I apply a custom wallpaper, everything seems to be fine. Its being shown in the desktop background images list, and even after a Reboot, sometimes(!) it is being shown in the list, but I cant see no wallpaper. After the Reboot that is. Any suggestions?

Thanks.

---

### Post by ajgreeny on 2013-06-10
Where is the image that you're trying to use?

---

### Post by LSHINE on 2013-06-11
Its on another partition. Xubuntu is on C (same as Win7), and the wallpaper files are on D.

---

### Post by ajgreeny on 2013-06-11
So this is a wubi install, and the image is on a windows partition, even though it's a different one to your windows OS where ubuntu is sitting.  That I think is the problem as that partition, D in your way of describing, is not mounted at boot time so the image is not immediately available.

I regret I know so little about wubi that I can not tell you how to mount your windows partitions in a wubi installation, at boot time.  I will leave that to others who know that system to tell you how it can be done, or you can do your own search using the link here for [Wubi-megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

---

### Post by LSHINE on 2013-06-11
Thanks. I'll try to find that out. I'll try to do something with partition manager. By the way, do you know of any other problems like that, using linux installed on Wubi?

---

### Post by ajgreeny on 2013-06-11
Sorry, not really.  I do not even have windows so am very out of date with anything MS.

Wubi, however, was never meant as a means of running a dual boot for permanent use, just as a better way to figure out if ubuntu would run on your hardware, so if you can do so, I recommend you try a proper partitioned install.

---

