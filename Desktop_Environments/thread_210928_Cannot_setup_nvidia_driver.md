---
title: "Cannot setup nvidia driver"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Flaystus on 2006-07-07
Runing Ubuntu 6.06, freshly installed and just updated. 

When I tried to follow these commands:
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

which worked like a week ago I get this:
ubuntu nvidia Error: your X configuration has been altered.

Have I messed something up already? This WAS working before I had to reinstall.

nVidia 6600gt btw.

---

### Post by Flaystus on 2006-07-07
uhoh I tried running the two commands it suggested

md5sum /etc/X11/xorg.conf 
sudo tee /var/lib/x11/xorg.conf.md5sum

the second one is taking a very long time. Is something wrong?

---

### Post by tzulberti on 2006-07-08
I just used this post, and it worked for me:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

