---
title: "Dell Studio 1747 freezes randomly at boot"
date: 2010-02-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by merry_meerkat on 2010-02-14
Hello,
I'm experiencing a very frustrating issue with booting my new Dell Studio 1747.

The problem is that it hangs/freezes during booting up. It does so randomly, however, I would estimate that it does so at least half the time!

It's a dual-boot machine and GRUB comes up fine. Then, after choosing Ubuntu, it proceeds to the small white Ubuntu logo on black background... and then - nothing!
...i.e. when it hangs, it hangs just before switching from white Ubuntu logo on balc background to the fancier one on brown background with the "pulsating white line" (I hope I am explaining this well enough).

When it does not freeze, the the white Ubuntu logo will become fuzzy around the edges for a second or so before switching to the next boot stage.

All this leads me to guess that it has to do with the ATI display driver, but I have no idea. And even less of an idea of what to do about it.

I have not installed the ATI driver that can be enabled through the "hardware drivers" setting under > System > Administration. Rather, I installed the newer version directly from the ATI website - so I'm running the "ATI Catalyst Control Center" version 2.11.

Then again, it may be something completely unrelated to the display driver.

Any suggestion?

Thanks a lot!!

---

### Post by SuperJames on 2010-03-12
I have exactly this same problem.  I have tried the proprietary driver from the "proprietary drivers" tool, and the download and install from the ati website.  I am also using a new Dell Studio 1747.

To be clear this is a hard freeze.  Ctrl-Alt-F1 through Ctrl-Alt-F9 do nothing but draw a green or blue line on the screen.  Have to hold down the power button to reboot.

Now, if I boot in rescue mode, and select boot normally to a prompt I can login and "sudo gdm" and that works every time.

-J

---

### Post by SuperJames on 2010-03-12
Ok, I think I solved it.  It was "splash".  I followed the suggestions in this post to try and narrow down what was causing it to freeze: [http://ubuntuforums.org/showthread.php?t=1374337]("http://ubuntuforums.org/showthread.php?t=1374337")
However in removing the "splash" screen to see what the problem was, the problem went away!

To remove the "splash" option and or "quiet" too, follow these instructions: [http://unixlab.blogspot.com/2009/12/disabling-splash-screen-in-ubuntu-910.html]("http://unixlab.blogspot.com/2009/12/disabling-splash-screen-in-ubuntu-910.html").

So, perhaps the "splash" is not compatible with the ati video driver???
whatever, it is gone now.


PS. if you have no sound on your Dell Studio 1747 the answer is in this post: [http://ubuntuforums.org/showthread.php?t=1395682]("http://ubuntuforums.org/showthread.php?t=1395682")
Scroll down to post #7 and add that code to the end of your /etc/modprobe.d/alsa-base.conf file


Cheers,
J.

---

### Post by merry_meerkat on 2010-03-13
Hey SuperJames,
thanks for the reply.

I recently did exactly the same as you. I disabled the boot splash as outlined in your post in order to have a more verbose boot process and hopefully find out what might be causing the freeze... My result is the same as yours: when booting just in text mode it works every time!

Now it doesn't look quite so elegant, but I can live with this.

Just a recap if anyone else comes across this problem:

edit grub:
```
sudo gedit /etc/default/grub
```

...change the following line...
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

...to...
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

...after saving the change you need to run the following command (as specified within the file):
```
sudo update-grub
```

That's it.


Note that there's also an in-between option where you change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="splash"
```
...this gives you a little text and still a background splash image. However, this option would still result in frequent freezes at boot in my case.

---

