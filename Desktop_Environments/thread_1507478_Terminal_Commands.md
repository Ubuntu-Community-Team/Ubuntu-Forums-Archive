---
title: "Terminal Commands"
date: 2010-06-11
forum: Desktop Environments
---

### Post by TheNewbieGeek on 2010-06-11
Hi I am doing a how to for installing a OS onto a sd card. The instructions were incorrect and someone posted that it was but did not post the correct command lines. I would like to know the correct commands. I will give you the the command of the original poster along with the how to follower persons sentence mentioning there needed to be a correction. I feel that probably the how to followers sentence mentioning that it was incorrect is enough if you know enough about linux commands well enough but I don't.

Here they are:

Original Posting instructions:

7) type: apt-get install xserver-xorg-video-fbdev xfce4 xfonts-base  xinit    press enter 

How To Followers Edit To The Above LIne (Somewhat): 

Edit2 : the package xserver-xorg-video-fbdev-xfce4 isn't exists, it's in  2 packages : xserver-xorg-video-fbdev and xfce4.


I need the correct commands to execute line 7 above. Thanks for the replies

---

### Post by gingivere0 on 2010-06-11
It sounds to me like it would be:

```
sudo apt-get install xserver-xorg-video-fbdev xfce4
```

That seems appropriate for what you are trying to do, but if those aren't the correct package names, or if they aren't in the repositories, then that won't be helpful to you at all. Good Luck!

---

### Post by gingivere0 on 2010-06-11
I just checked synaptic and those packages are available to me, so they should also be to you.  Have fun!

---

### Post by garvinrick4 on 2010-06-11
[tuXfiles - the Linux newbie help files, tutorials, and tips]("http://www.tuxfiles.org/")

---

