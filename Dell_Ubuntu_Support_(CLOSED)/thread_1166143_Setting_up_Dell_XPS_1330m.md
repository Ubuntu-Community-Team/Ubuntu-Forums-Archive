---
title: "Setting up Dell XPS 1330m"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by M3TR1C on 2009-05-21
New to the site hope that this is the right area for it.........I just bought a Dell XPS 1330m and its coming with no OS on it. Since i've been happy with ubuntu for the last year and a half i'm going to install that. Is there anything i need as far as drivers to get it running to its full capacity. Noticed some people were having DVD problems and wonder if there is a fix for it already. Thanks. ):P

---

### Post by AegisTalons on 2009-05-24
Welcome to the Forums. I currently have a XPS m1330, and actually typing this message on it right now. In 9.04, they fixed a lot of issues. For me it works relatively well. For starters, once you install 9.04 and update it, then install the nvidia drivers. Wifi should work off the bat. Same with the SATA drivers for the hard drive.

What I'm currently having issues with is the sound capturing. It captures the sound very faintly. Which is not suitable for Skype and such. I'm not sure what exactly you are talking about the DVD issue, but I'm going to guess the one where you push the Eject button and nothing happens. If that is what you are referring to, it is actually the way Linux is designed. It won't let you eject hardware until you unmount it, just in case other users are using it.

---

### Post by x C0MMAND0 x on 2009-05-25
**FIX FOR THE EJECT BUTTON**

Simply add this to /etc/sysctl.conf:

```
# Unlock the CDROM eject button
dev.cdrom.lock=0
```

You have to restart for it to take effect.

**Follow this thread for the low volume issue**

[_Workaround for low mic volume XPS m1330_]("http://ubuntuforums.org/showthread.php?t=1048568")

---

### Post by M3TR1C on 2009-05-25
yea just started doing all the fixes for it. Working on the volume jumping right now. Cause volume changes in giant intervals. That and the 2nd headphone jack isn't working yet.

---

### Post by x C0MMAND0 x on 2009-05-28
> **M3TR1C said:**
> yea just started doing all the fixes for it. Working on the volume jumping right now. Cause volume changes in giant intervals. That and the 2nd headphone jack isn't working yet.

Open up gconf-editor (Alt-F2, type "gconf-editor"), and go to apps > gnome-settings-daemon, and change volume_step as needed. Changing it to 2 worked perfect for me, but I like it very sensitive.

---

### Post by davethebald on 2009-05-30
I just upgraded to 9.04 on a Dell XPS M1330.  I did so from a CD on which I burned the ISO file.  Could not have been easier, works like a charm.

---

### Post by mariliasaca on 2009-05-30
I have a XPS M1330 that was working fine nder 8.10. Upgraded to 9.04 and the problem began. If I connect anything on one of the usb (mouse, printer, pen-stick, modem, camera) it takes it approximately 15 minutes to find it (measured a few times, it is around this!).
I've looked at the general forums, but couldn't find any similar problem, and I got no answer at all (beginners forum). So, maybe it is something between Dell and Ubuntu? 

Thanks for any help!

---

### Post by zaphod777 on 2009-05-30
> **mariliasaca said:**
> I have a XPS M1330 that was working fine nder 8.10. Upgraded to 9.04 and the problem began. If I connect anything on one of the usb (mouse, printer, pen-stick, modem, camera) it takes it approximately 15 minutes to find it (measured a few times, it is around this!).
I've looked at the general forums, but couldn't find any similar problem, and I got no answer at all (beginners forum). So, maybe it is something between Dell and Ubuntu? 

Thanks for any help!

Try doing a fresh install sometimes the upgrade doesn't work that great depending on what files you said to replace.

---

### Post by hornbake on 2009-06-04
> **mariliasaca said:**
> I have a XPS M1330 that was working fine nder 8.10. Upgraded to 9.04 and the problem began. If I connect anything on one of the usb (mouse, printer, pen-stick, modem, camera) it takes it approximately 15 minutes to find it (measured a few times, it is around this!).
I've looked at the general forums, but couldn't find any similar problem, and I got no answer at all (beginners forum). So, maybe it is something between Dell and Ubuntu? 

Thanks for any help!

I had a similar problem a while back on an Inspiron 700m, now I too use a XPS M1330.  The issue was with the motherboard, which I had replaced and resolved the USB problem.  I'd try calling Dell.

The XPS now needs a new motherboard too, after 14 months of use.  I'm not very confident about the hardware in these Dell notebooks anymore.  The upside is they keep sending me all the new parts I need, but it's such a waste of time to have these repeating problems.

---

