---
title: "Help with a .deb package"
date: 2005-09-28
forum: Desktop Environments
---

### Post by Master Shake on 2005-09-28
OK, one station I installed  Ubuntu on has absolutely no internet access at all, and so if I want to add something to it, I have to download the .deb file to a floppy on my (yuk) Windon'ts machine, and then put the floppy in the Ubuntu machine, and copy it.  The question is how do I install this?

the package is tilda_0.08.1-0ubuntu1_i386.deb

---

### Post by psychicdragon on 2005-09-28
```
sudo dpkg -i tilda_0.08.1-0ubuntu1_i386.deb
```
I hope you have all the dependencies.

---

### Post by XDevHald on 2005-09-28
Just a quick note with psychicdragon's post, root must be where the .deb package is in order to dpkg it. so if it is on your desktop (you might already know this command) but it's **cd /home/yourusername/Desktop/ **same with the other locations on your HD.

Hope it works well installing!

---

### Post by psychicdragon on 2005-09-28
I guess that's true. I save everything to my home dir, I don't even have a desktop, so I didn't think of that.

---

### Post by Master Shake on 2005-09-28
Nope, gotta get all the dependencies, and there's apparently a LOT.  I'm gonna have to wait until I get home to grab 'em and put 'em on CD.

---

