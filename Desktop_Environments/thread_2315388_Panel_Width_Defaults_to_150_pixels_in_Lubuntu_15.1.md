---
title: "Panel Width Defaults to 150 pixels in Lubuntu 15.10 and 16.04"
date: 2016-02-28
forum: Desktop Environments
---

### Post by wjbmd48 on 2016-02-28
Hi:

I like to keep my panel on the right margin, to maximize my vertical screen dimension.

I've noticed a problem in Lubuntu 15.10 and the beta of 16.04, but not in 14.04, which is that the panel width defaults to 150 pixels, no matter what I set it at, with each reboot.

This, apparently, is a well-reported bug:

[http://askubuntu.com/questions/721756/lxpanel-wont-save-width-settings-when-its-at-the-left-edge](http://askubuntu.com/questions/721756/lxpanel-wont-save-width-settings-when-its-at-the-left-edge)

supposedly you can fix it with:
sudo apt-get remove lxpanel-data lxpanel
  then you can install lxpanel-data and then lxpanel.

  To avoid system auto-update to 0.8.1 you can launch

  sudo apt-mark hold lxpanel
sudo apt-mark hold lxpanel-data

And also by changing the icon size by even one pixel.


But neither of those fixes work for me.

I'd happily stay with 14.04, but this runs into another bug, which is that that 14.04 only recognizes 64G of 
my 128 GB Kingspec SSD on encrypted install, which doesn't happen with later distros.

Any ideas?

Bill

---

### Post by egeezer on 2016-02-29
Instead of just your original remove, you might try ```
 sudo apt-get remove --purge
``` or if you want to get really down to it, go to superuser status with ```
sudo -i
``` and use # dpkg –purge   (the initial # is the superuser prompt signal that compares to $ in normal user mode)  When you're done, make sure to exit the superuser status and then exit regular.

---

### Post by wjbmd48 on 2016-02-29
Thanks!!  

But no joy; after entering all those into terminal and exiting out of superuser then admin, still defaults back to 150 wide on reboot.

Bill

---

