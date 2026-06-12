---
title: "My review of Ubuntu 7.10 on Dell Inspiron 6400 with ATI Mobility Radeon X1400"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by djRob on 2007-10-23
Before reading this post please read my review of Kubuntu 7.10 at
[http://ubuntuforums.org/showthread.php?t=581715](http://ubuntuforums.org/showthread.php?t=581715)


I used text install from Ubuntu 7.10 Alternate CD.
Installation  went OK (I have turned off Wi-Fi and Bluetooth, because I don't use them). Of course Gnome didn't want to start because I have ATI card so I had to install ATI driver manually. 

After logging in I saw much nicer and polished user interface than that in Kubuntu. In adidtion there is control panel for touch pad, 
Dell function keys work, desktop search works. Everything works better than in Kubuntu - e.g. in Kubuntu, in VLC moving slider in order to listen 
to the farther part of file doesn't work well.
Suspend/Hibernate doesn't work.
The bug or error  that is present in Ubuntu but not present in Kubuntu is that Ubuntu starts in balanced CPU mode, i.e. CPU works at 50% frequency 
unless more is needed, but nowhere it is shown to the user.

So after this experience I decided to switch to Ubuntu, especially because Canonical really supports only one window manager - Gnome - 
- my bug report about lack of control panel for touch pad in Kubuntu Feisty ([https://bugs.launchpad.net/ubuntu/+bug/118617](https://bugs.launchpad.net/ubuntu/+bug/118617)) has been ignored. 

Another problem that I found, which was present in Kubuntu Feisty and Gutsy is worse quality of sound in comparison to Windows Vista which I have installed too. 
The sound is flatter (less dynamic) than in Vista, especially it is audible using Real Player. 
 
I wish that the future version of Ubuntu will:
1. install ATI proprietary driver by default,
2. have working Suspend/Hibernate,
3. play sound as good as Vista does.

--------------------------------------------------------------------------
Update

After reading about this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

I would like to change point 1. to 1. detect  ATI card and when detected will inform user that  ATI sucks because they didn't provided good open source driver, and if the user wants to complain, here is the address
[http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web](http://support.ati.com/ics/survey/survey.asp?deptID=894&surveyID=508&type=web) 

Robert

---

### Post by Gen2ly on 2007-10-23
Yeah, until the new version of KDE is out, GNOME gonna have a better look and feel to it.  GNOME releases on a regular 6 month-cycle that Canonical syncs very well to.

Did hibernate suspend operate ok in Kubuntu?  The kernel is the same so I'd expect similar.  Ram suspend should just work try

```
echo mem >/sys/power/state
```

Hibernate requires a suspend 2 sources kernel that I'm not sure Ubuntu supports?  Anyone?

As for sound have you tried another sound player, real player is ok but there are a few better.

---

### Post by djRob on 2007-10-23
> **Dirk.R.Gently said:**
> Yeah, until the new version of KDE is out, GNOME gonna have a better look and feel to it.  GNOME releases on a regular 6 month-cycle that Canonical syncs very well to.

Did hibernate suspend operate ok in Kubuntu?  
No, it didn't.

> 
The kernel is the same so I'd expect similar.  Ram suspend should just work try

```
echo mem >/sys/power/state
```

I got "bash: /sys/power/state: Permission denied" error. Of course I used sudo.
> 
Hibernate requires a suspend 2 sources kernel that I'm not sure Ubuntu supports?  Anyone?

As for sound have you tried another sound player, real player is ok but there are a few better.
I tried many players, the result is similar (maybe RealPlayer has the worst quality of sound). I think that Vista has better driver for my sound card.

---

### Post by djRob on 2007-10-24
Because Compiz didn't want to start by checking an option in menu [FONT=Courier New]Visual Effects[/FONT] I had to install it manually. Compiz works OK although Gnome starts up much slower than previously and installation of Compiz removed control panel for touch pad so I had to install gsynaptics.

---

### Post by Desigen on 2007-12-30
Hi, did anyone of you guys solve the sleep problem ? 

Thanks

---

