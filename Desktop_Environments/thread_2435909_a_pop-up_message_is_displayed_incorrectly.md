---
title: "a pop-up message is displayed incorrectly"
date: 2020-01-28
forum: Desktop Environments
---

### Post by martin-1963 on 2020-01-28
Hi all!

Ubuntu 18.04.3 
CPU: Intel® Core™ i5-7500 
VGA: Radeon HD 6450 2GB
Memory: 16GB

a pop-up message is displayed incorrectly, in my browser, and in apps.
I show this:
[http://kepkezelo.com/images/kcoirdf9hrdxm4a8h51l.png](http://kepkezelo.com/images/kcoirdf9hrdxm4a8h51l.png)

How to fix it?

---

### Post by vdelll on 2020-01-28
Hi ! 

I have the same problem, and I don't know how it come. Yesterday, I have published a message about this in a french ubuntu forum and I have no response for the moment.

So I follow this post.

---

### Post by deadflowr on 2020-01-28
There was an update that was suppose to fix this yesterday:
[https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718]("https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718")
Please confirm the updated package was installed;
```
apt policy xserver-xorg-video-ati-hwe-18.04
```
Package version should be: 1:19.0.1-1ubuntu1~18.04.1
If it was installed then please report it: [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
Following sil2100's advice in comment #48: [https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718/comments/48]("https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/1841718/comments/48")

---

### Post by paydaydaddy on 2020-01-30
There are several threads going in the forum about this issue.
[https://ubuntuforums.org/showthread.php?t=2435305]("https://ubuntuforums.org/showthread.php?t=2435305")
[https://ubuntuforums.org/showthread.php?t=2435494]("https://ubuntuforums.org/showthread.php?t=2435494")
[https://ubuntuforums.org/showthread.php?t=2435987]("https://ubuntuforums.org/showthread.php?t=2435987")
There are probably more than listed here, but you can get a feel for what others have experienced. There does seem to be a work around for Kubuntu that does not work in Ubuntu. So far, no updates have fixed the problem on my Kubuntu 18.04.03 machine so that I can go back to the default backend rendering (a little crisper display), but I am getting by fine with the described work around.

---

### Post by vdelll on 2020-02-02
Hi,

I had an update today and that fixed the problem.

---

### Post by josephmmorgan on 2020-02-03
Are you on Kubuntu or Ubuntu?  I'm seeing the same issue on an Ubuntu machine.

---

