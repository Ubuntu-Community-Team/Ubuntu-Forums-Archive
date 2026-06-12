---
title: "Lost my desktop"
date: 2014-08-21
forum: Desktop Environments
---

### Post by grantmcduling on 2014-08-21
I am running with unity and tried to download and install a nvidia driver for my webcam. All went well and I had to reboot to complete the install. Now when I reboot I am faced with my terminal login. No destop environment. I also need to access my mobile broadband dongle on the DE to fire up the web. I have tried all I can think of to get the DE back without success. I am writing this on my laptop (Crunchbang) as I have no access to internet without being able to connect the dongle up without the DE. Any ideas?

---

### Post by ajgreeny on 2014-08-21
Did your unity desktop work without the nvidia driver?

What driver was this and where did you download it from?

If you installed it from the repos Additional drivers, you can use Ctrl+Alt+F1 to get to a tty command line, and from that run ```
sudo apt-get remove nvidia*
``` which should get you back to the open source nouveau driver.  Reboot and then see if you can install another, and hopefully, more successful driver.

---

### Post by grantmcduling on 2014-08-22
Thanks, worked fine. Removed nvidia-304 and now my DE is back once more. Wonderful help.

---

### Post by ajgreeny on 2014-08-22
Great!

Please mark this as solved from the Thread Tools menu at the top of the page.

---

