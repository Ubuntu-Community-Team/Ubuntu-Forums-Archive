---
title: "Forced Shut Down broke Gutsy"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by danfrankj on 2008-03-31
So I've been running Gutsy and after following many of the guides here I had Compiz and Emerald working for me as well as video playback in all forms.  My computer froze while I was on gmail and I had to shut it down by holding down the power button.

When I got back to the login screen, it looked fine but my input in username and password are now huge and if I check the options menu, it fills the entire screen and almost unusable since the font is so big.  And when I log on, desktop effects are gone and anything graphical (including web browsing) is very choppy as the screen takes a long time to "refresh".   

I've had things go wrong before when I did a forced shutdown and I usually gave in to reinstalling, but since everything was working so nicely before, I was hoping not to have to do that this time.  I know that's not a lot to go on, but any help would be much appreciated.

Thanks,
DAN

---

### Post by Zorael on 2008-03-31
You could try reconfiguring your xorg.conf file. You'll likely have to reenable your Restricted driver afterwards, though.

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

Basically, it'll revert to your default settings for videocard and input drivers. You may want to back up your existing file. It's located at **/etc/X11/**, and again, named **xorg.conf**.

---

### Post by danfrankj on 2008-03-31
Yep, that got me on the right track, thank you.  Apparently, my xorg.conf got replaced by xorg.conf~ so there actually was no xorg.conf file in /etc/X11 when I checked.  But copying xorg.conf~ back to xorg.conf got things working again automatically.

Now that I've got things working again, this is more for my own edification, but why would a "forced shut down" change the xorg.conf to xorg.conf~ . Moreover, what exactly does xorg.conf control and what does reconfiguring it with $ sudo dpkg-reconfigure -phigh xserver-xorg  mean/do?

Thanks again, Dan

---

