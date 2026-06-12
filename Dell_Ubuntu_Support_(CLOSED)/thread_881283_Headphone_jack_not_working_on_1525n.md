---
title: "Headphone jack not working on 1525n"
date: 2008-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Spooky5 on 2008-08-05
I had to reinstall Ubuntu 7.10 about a week ago. Now one of my headphone jacks isn't working. I looked at the Dell wiki which says to do this

> 1. Open the GNOME volume control tool:

```
$ gnome-volume-control
```

Select Edit -> Preferences and verify the following tracks are visible: Surround, Front and Line In as Output. Click Close when done. 

I don't have any of these options when I open the volume control. :confused:

How do I get my headphone jack working?

---

### Post by ms_whosit on 2008-08-06
What options do you have in the volume control? Does it say Conexant HSF (OSS) or Alsa mixer? The reason I ask is I thought it might be related to this:

[http://ubuntuforums.org/showthread.php?t=871256](http://ubuntuforums.org/showthread.php?t=871256)

..which, btw, isn't solved yet..at least for me.

In addition to this issue, I noticed that both headphone jacks do not work at the same time, although each works by itself (at least under the old kernel, where sound works otherwise correctly).

---

### Post by Spooky5 on 2008-08-06
Mine is the Conexant HSF. I've noticed issues with the volume control as well but I've pretty much learned to live with it, lol.

---

### Post by ms_whosit on 2008-08-07
yeah. It's my understanding that this means it's using the modem as the sound card, which I guess is not a major problem (?), but I'd like to get the primary soundcard working.

---

### Post by cszikszoy on 2008-08-07
I've heard a lot of people saying to disable the internal modem in the bios (unless you need it...?).

On some dell laptops (yours I assume) the internal modem and sound card share some resources.  Because of this, when ALSA (for 7.10) is setup, it gets confused and often will not work properly.  Disabling your modem will free these shared resources and then, reconfiguring ALSA should make things better.

This is just what I've heard, I haven't tried it though.

---

### Post by ms_whosit on 2008-08-09
thanks. I need my modem though because I use it. I think there must be some way to get them both working because they both work fine under the old kernel. (2.6.22.14).

---

