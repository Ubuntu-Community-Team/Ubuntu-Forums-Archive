---
title: "Font size changes not having effect on some applications"
date: 2012-10-11
forum: Desktop Environments
---

### Post by Witra on 2012-10-11
Recently I switched my HTPC from windows to kubuntu. It's connected to a 720p TV via HDMI from Asus geforce GT 520. I installed NVidia drivers, and they do seem to work rather well.

However, as soon as I did that I noticed all the font sizes were tiny enough to be utterly unreadable. I changed the sizes from application appearance in system settings to size 26 and forced font dpi to 40. [[tinypic.com]]("http://oi48.tinypic.com/34dqwzb.jpg")

 I was, and am, very pleased with the result. 
However, KDE partition manager still has those tiny fonts, and is almost unusable, even with KMag [[tinypic.com]]("http://oi49.tinypic.com/2li8xgn.jpg"). I haven't yet gone through every application, but I assume there are a few more with the same problem.

I'm rather lost as to what even could be causing this, thus I'd like to ask if anyone here had an idea?

---

### Post by bra|10n on 2012-10-11
You might try the following to see if it fixes font sizes for apps running with elevated privileges;

Alt+F2, kdesu systemsettings

Repeat the font, font size and dpi changes you made earlier.
A login/out may be required before the changes take effect.

---

### Post by Witra on 2012-10-13
Good idea. 
However, after logout, I only get a blank screen. Same if I try to restart kdm. 
If I stop KDM, I do get a CLI login, but after starting it up again, it's back to blank

---

### Post by bra|10n on 2012-10-13
Sorry Witra can't help with Kubuntu specifics...
There has been a few posts reporting similar complaints of KDM / black screen recently.
Good luck, I hope you find a fix :KS

---

### Post by bra|10n on 2012-10-17
Having had the opportunity to install Kubuntu 12.10 in the last few days I can confirm that updating 723 packages using Muon fails, resulting in CLI prompt **dead-end **as the OP reports.
A reinstall and update via the CLI with the following command is successful however,
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

