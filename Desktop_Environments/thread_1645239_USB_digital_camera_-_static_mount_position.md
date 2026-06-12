---
title: "USB digital camera - static mount position"
date: 2010-12-14
forum: Desktop Environments
---

### Post by bullpup on 2010-12-14
Hi, I hope this is the correct category, but I THINK this is a gnome question.

I have digital camera (Canon EOS 550d) which I connect to my computer using a USB cable. I can see that the camera file system is mounted under "~/.gvfs/gphoto2-XYZ" where XYZ seems to be a dynamic device dependent string that changes every time I connect the camera.
The thing is: I need the mount position ALWAYS to stay the same, so my photo management program (Bibble) knows where to download the images from.
I am not sure how to do this, but I guess there must be a way to configure GVFS/FUSE or whatever is responsible for mounting the camera to use a fixed mount point (like /media/camera or something).

Thank you!

---

### Post by Jerubaal on 2010-12-30
Hi, have you found a solution to this yet?

---

### Post by bullpup on 2011-01-05
Well a workaround is to use "~/.gvfs" and scan the folder recursively for images, but at the moment I am using gthumb to import the images to a special "Inbox" folder.

---

