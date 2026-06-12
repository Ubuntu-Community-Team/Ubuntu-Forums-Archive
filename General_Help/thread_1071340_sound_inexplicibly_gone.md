---
title: "sound inexplicibly gone"
date: 2009-02-16
forum: General Help
---

### Post by dlm4849 on 2009-02-16
Im at a complete loss...have been on my laptop on and off throughout the evening and now the sound refuses to work at all under Ubuntu. No login sound or anything, but sound works fine in XP. I checked under alsamixer and the volume was up. I have restarted several time, with nothing. Is there anything Im missing?

Also, there were no updates or installed anything that could explain it.

---

### Post by desm on 2009-02-16
Did you take care to unmute the channels under alsamixer?
Press m to unmute a channel. By default they're muted and have 'MM' beneath them. Once you press 'm' they will display '00'. 
After that you probably wanna run 'alsactl store' to store those settings. At least I have to on Arch.

---

### Post by OscarWabbit on 2009-02-16
> **dlm4849 said:**
> Im at a complete loss...have been on my laptop on and off throughout the evening and now the sound refuses to work at all under Ubuntu. No login sound or anything, but sound works fine in XP. I checked under alsamixer and the volume was up. I have restarted several time, with nothing. Is there anything Im missing?

Also, there were no updates or installed anything that could explain it.

I'm having exactly the same problem too.

Sound has suddenly stopped working.  Sound works in XP (laptop is dual boot).

Computer is a Toshiba Satellite M70-122 laptop. 

Sound used to work fine, so I think an update must have broken it, but I don't exactly remember when that might have been.  Sound hasn't been working for a few weeks, but I didn't realise for some time as I use this computer mainly for surfing.


edit: thinking about it, I think the sound stopped working when I upgraded from 8.04 to 8.10, but I may be mistaken.

---

### Post by eviltwin on 2009-02-16
I'm having similar issues. I ran a bunch of updates last night and my sound has spontaneously stopped working. Perhaps a problem in a kernel update? I may just try booting into the old kernel and see what happens...

EDIT: Ok, yeah, 2.6.27-11 breaks sound on my Audigy 2 ZS. Booting to 2.6.27-9 resolves the issue. This is a regression and one of us ought to report it on launchpad...
EDIT2: [Bug already exists]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179") on launchpad (at least for my card, but I think that driver has a larger scope. There is a fix included, I hope this helps... :)

---

### Post by dlm4849 on 2009-02-16
Thanks for the help guys. As late as it was, I didnt think to add the volume applet to my panel and see what all the controls on there were saying. Somehow my main volume was turned off and the master volume wasnt set to be controlled by the keyboard so changing the volume wasn't actually doing anything. Wierd that the volume was showing as turned up in alsamixer...

---

### Post by desm on 2009-02-18
I'd bet my bottom dollar it wasn't showing as unmuted...
It has to display to zeroes instead of doubls Ms.

---

