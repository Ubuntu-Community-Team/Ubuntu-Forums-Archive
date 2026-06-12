---
title: "Boot-Up Freeze on &quot;Configuring Network Interfaces&quot;"
date: 2006-08-27
forum: Desktop Environments
---

### Post by erusan on 2006-08-27
I recently tried (for the millionth time) getting ndiswrapper to work.  After getting a segmentation fault, I did a reboot, and now Ubuntu hangs on "configuring network interfaces."  It eventually switches out of the splash screen and into text mode, but it still hangs.

The installation was pretty much brand new and uncorrupted by me playing with anything.  Is there anyway I can use a live CD or something to repair my system?  Thanks.

---

### Post by spin2cool on 2006-08-27
Try hitting CTRL-C as soon as the network interfaces line appears.  This may allow you to bypass that step.  You can also boot into text-only repair mode by choosing that option from the GRUB menu

---

### Post by HBloomer on 2007-01-30
Hey,
 I am having the same problem and I can bypass by using Ctrl-C but, if i go into the GUI my screen is all chocolate colored and nothing else happens.  From terminal I can input commands but, how do i fix this problem???  Any help much appreciated, thanks!
HB

---

