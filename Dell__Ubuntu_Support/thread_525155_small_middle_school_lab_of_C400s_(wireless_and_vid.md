---
title: "small middle school lab of C400s (wireless and video)"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by jjf on 2007-08-14
My school bought some Dell Latitude C400's for a small "mobile computer lab."  The benefit of being "the computer guy" a very small school is that I don't have to butt heads with a sys admin who doesn't want to try something new (namely, something non-Microsoft).  The drawback is I don't know very much.

I need some help with three issues.  

**1)  Wireless.**  I bought the C400s because a lot of people said their built-in wireless worked right out of the box with Fiesty.  Mine doesn't.  Ubuntu recognizes the cards, but the cards don't see my WEP secured home network (which I know is configured fine because my personal laptop connects to it).  

Here's the output of the command **iwconfig eth1** (the wireless card)

```
eth1      IEEE 802.11b/g  ESSID:"F"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The line "Access Point: Invalid" looks like trouble to me.  Any ideas?

2) My second problem has to do with video.  At first, when I closed and reopened the lid, the GUI would be garbled for about a minute then restart (to the gnome login screen).  I found a custom xorg.conf file that fixed this problem here:

[http://supernovae.in2p3.fr/~guy/linux/](http://supernovae.in2p3.fr/~guy/linux/)

But when I try to get to one of my terminals (CTRL+ALT+F1), the resolution is too big.  The text is misshapen and I can't see the command prompt or output.  This is important because I sometimes CTRL+ALT+F1 to a command prompt to kill unresponsive programs.  

When I boot into recovery mode, the text is normal, so I know the screen is capable of rendering it.  

3) I need some easy way to just set up one laptop, then clone its hard drive to all the others.  Can rsync do this?  I've also read about a program called "Ghost for Linux," but it looks like I'd need to secure an IDE-to-USB cable for that.  I don't have one.  I'll get one if that's the best way, but if I can do it with rsync, I'd rather.

Thanks for the help.

---

