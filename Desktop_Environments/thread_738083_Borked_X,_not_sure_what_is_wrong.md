---
title: "Borked X, not sure what is wrong"
date: 2008-03-28
forum: Desktop Environments
---

### Post by revoohc on 2008-03-28
Everyone,

(I hope this is the correct forum.)

Last night, I had KDE running with Compiz on my laptop (Latitude D800) and life was pretty good.  I went to play with Crossover Games and it stated that my Nvidia driver was out dated.  Since I knew I was as current as 7.10 was, I went to Nvidia and tried to d/l the latest driver.  Well, it did not work with my card.

So, I did reinstalled nvidia-glx-new.  However, when I did this, I was not able to get into my desktop. I keep getting the following in my .xsession-errors:

Xsession: X session started for choover at Fri Mar 28 09:13:29 EDT 2008
Checking for nVidia: present.
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama

Fatal server error:
no GLX visuals available

rm: cannot remove `/tmp/.X1-lock': No such file or directory
rm: cannot remove `/tmp/.X11-unix/X1': No such file or directory
xmodmap:  unable to open display ':1'


So, I uninstalled and reinstalled nvidia-glx-new and nvidia-kernel-common (and even rebooted), but still no joy.  I still get the same errors.

What is going on here?  Why can't I get back into my KDE?  The only way I have found to do this is to uninstall xserver-xgl.  But like I said, before the nvidia driver update, everything was working with xserver-xgl.

How do I re-enable the glx?

Thanks,

Chris

---

