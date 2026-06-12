---
title: "Intel driver"
date: 2009-04-22
forum: General Help
---

### Post by Uzi304 on 2009-04-22
I have an Intel 945GM video card, how can I find which driver Ubuntu is using for it and if it isn't the latest driver, where can I get the latest one for Ubuntu?

---

### Post by orlox on 2009-04-22
For your graphics card, ubuntu should default to the intel driver.

However, for both Jaunty and intrepid, there are important regressions in performance due to some big rewrite of the driver. Check out this link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094?comments=all)

If you are having problems of performance in intrepid or jaunty, I could tell you how to try an experimental thingy to improve those (however, for your video card some have reported this trick to cause freezes). Tell me if youre interested...

---

### Post by Uzi304 on 2009-04-22
Yes I am interested. If you are talking about the UXA thing, I've already done it but do tell.

---

### Post by orlox on 2009-04-22
jajaj, well, I was talking about UXA. It faired pretty well for my graphics card (A G965 or something like that...). if you still cant get to much improvement in performance, guess youll just have to wait for intel to improve their driver...

---

### Post by Uzi304 on 2009-04-23
Right but how can I tell which driver I'm using at the moment?

---

### Post by Kareeser on 2009-04-23
apt-cache policy xserver-xorg-video-intel :)

---

### Post by Uzi304 on 2009-04-23
```
xserver-xorg-video-intel:
  Installed: 2:2.6.3-0ubuntu9
  Candidate: 2:2.6.3-0ubuntu9
  Version table:
 *** 2:2.6.3-0ubuntu9 0
        500 http://us.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```
Is the "2:2.6.3-0ubuntu9" my driver version? If so, is that the latest one? And is there anyway I can use an official Intel driver?

---

