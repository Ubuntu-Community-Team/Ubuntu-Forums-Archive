---
title: "Inspiron 1525 / XPS M1330 webcam issue"
date: 2008-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cisoprogressivo on 2008-11-05
The webcam of my Inspiron 1525 and my XPS M1330 stops working after installing Ubuntu 8.10.
Both cheese and Skype have the same problem, the led is lightened but camera doesn't work.

Sorry for my English :)

---

### Post by Technoviking on 2008-11-06
There are problems with the v4l libraries. Skype should work if you don't use Cheese first after boot up.

---

### Post by motin on 2008-11-08
The relevant bug report is found at [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

---

### Post by naaman on 2008-11-14
I have found [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506) to be the most useful bug report page on the issue so far..

The info on the bug report page about using the updated kernel from Stefan Bader may be a little vague for some Ubuntu users.  The kernel can be installed by adding the following lines into /etc/apt/sources.list:

```
# broken webcam kernel modules fix - launchpad bug #290506
deb http://ppa.launchpad.net/stefan-bader-canonical/ubuntu intrepid main
```

then running the following:

```
sudo apt-get update
sudo apt-get install linux-image-2.6.27-8-generic
```

A reboot will be needed.  The problem is that it broke my X environment because I use the closed-source nvidia driver.  At that point in time I put it into the "too hard basket" and decided to reboot back into the official kernel to wait for a fix to trickle down.  Trickle down most likely means to wait for the next release of Ubuntu.

YKMV (K = kilometre-age)

---

### Post by motin on 2008-11-20
The webcam now works for me after upgrading v4l to 0.5.3. No need to change the kernel. Using an M1330 atm. The workaround is available in the bug report mentioned two posts above.

---

