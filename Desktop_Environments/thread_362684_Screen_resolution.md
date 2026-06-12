---
title: "Screen resolution"
date: 2007-02-15
forum: Desktop Environments
---

### Post by gentoo_zach on 2007-02-15
Hello all,

I'm new to Ubuntu.  I'm testing it out compared to my Gentoo installation (which I really like).  I'm having a little problem with screen resolution though.  I can't seem to get anything above 800x600.  When I had this problem in Gentoo, I simply used:

```

nano /etc/X11/xorg.conf

```

And made sure that I had "1280x1024" in my "modes" section for my "DefaultDepth."  However, when I looked on this Ubuntu installation, I realized that it is already there, but doesn't show up in the options when I try to change the screen resolution.

Any ideas?

Thanks,
Zach

---

### Post by Scooter7 on 2007-02-16
Zach, here's what you need to do (at least, this should work, I had the same problem today and this is how I fixed it):

First, open up the terminal (Applications -> Accessories -> Terminal), and type

```
sudo dpkg-reconfigure xserver-xorg
```

Go through the steps.   When you get to the part asking if you want to autodetect your monitor, select No.   When asked if you want to enable kernel buffering, say yes.   Then, when presented with a list of resolutions, go to the resolution you want to use, and select it by pressing the Space key.   When done, hit enter, and continue the rest of the config.   When it's done, restart your computer.   You should be able to select your resolution then (and after that, you may have to restart again).

---

### Post by gentoo_zach on 2007-02-16
I appreciate the information and I will try it in a little bit.  The only thing I'm a little confused about is why it won't simply read my xorg.conf file for the resolution information.  Does Ubuntu utilize a different method for X11 configuration?

---

### Post by ubix on 2007-02-16
See also [ similar problem :confused: ]("http://ubuntuforums.org/showthread.php?t=362463")

---

### Post by Scooter7 on 2007-02-16
No, it doesn't.   Unfortunately I'm just as confused as you are.   However, what I told you should work.   If it doesn't, let me know.

---

### Post by veloce on 2007-02-16
> **gentoo_zach said:**
> Hello all,

I'm new to Ubuntu.  I'm testing it out compared to my Gentoo installation (which I really like).  I'm having a little problem with screen resolution though.  I can't seem to get anything above 800x600.  When I had this problem in Gentoo, I simply used:

```

nano /etc/X11/xorg.conf

```

And made sure that I had "1280x1024" in my "modes" section for my "DefaultDepth."  However, when I looked on this Ubuntu installation, I realized that it is already there, but doesn't show up in the options when I try to change the screen resolution.

Any ideas?

Thanks,
Zach

What graphics card are you using?  alternatively, can you copy the "device" section of your xorg.conf here.

---

### Post by Henry Rayker on 2007-02-16
the problem probably lies in the fact that the graphics driver the system is using doesn't match your graphics card (probably the vesa driver or somesuch). That's one thing I'd check out.

---

