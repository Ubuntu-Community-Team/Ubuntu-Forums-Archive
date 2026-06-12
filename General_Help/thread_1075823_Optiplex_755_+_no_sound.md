---
title: "Optiplex 755 + no sound"
date: 2009-02-20
forum: General Help
---

### Post by snick525 on 2009-02-20
I know that there are several different posts of this already, but none of them had a solution that worked for me. I have a Dell Optiplex GX755 that does not have any sound.

I have tried using module-assistant to install the alsa driver, but still no change. I also have the latest BIOS (A12).

alsamixer and gnome-alsamixer load fine and I have all of the sliders to 100% and none are muted.

Any suggestions?

---

### Post by Therion on 2009-02-20
Do you see a "Switches" tab in your Sound Properties?  

Under that tab do you see a tic-box for something called "Audigy Analog/Digital Output Jack" or something very similiar (sorry, I'm stuck behind my WinXP machine at work right now)?

If you do, UN-tic that box and see if you get sound.

---

### Post by snick525 on 2009-02-20
I do not see a box that says that.  :(

---

### Post by Therion on 2009-02-20
Just to double-check...  You right-click on the "Volume" icon in your system tray, click on Properties and there's no "Switches" tab?  Okay, so much for the simple solution.

See this "Comprehensive Sound Problems/Solutions Thread" and follow it STEP-BY-STEP:  

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Good luck!

---

### Post by snick525 on 2009-02-20
That guide worked great. Thanks Therion!

It turns out that I wasn't apart of the audio group.  As in, when I typed in:

```
grep 'audio' /etc/group
```

It came back with

```
audio:x:29:
```

Instead of 

```
audio:x:29:(myusername)
```

---

### Post by Therion on 2009-02-20
> **snick525 said:**
> That guide worked great. Thanks Therion!

Excellent.  Glad that worked out for you.  :)

---

### Post by thinkinhurtz on 2009-05-09
Therion, Your guide was great. Thanx very much for you help!

---

