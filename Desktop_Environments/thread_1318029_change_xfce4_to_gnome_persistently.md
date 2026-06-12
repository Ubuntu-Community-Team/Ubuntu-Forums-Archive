---
title: "change xfce4 to gnome persistently"
date: 2009-11-07
forum: Desktop Environments
---

### Post by Sempfinger on 2009-11-07
Hi folks!

I installed xubuntu a while ago (7.04 I think) and used it until 8.04. Then I decided to switch to gnome instead of xfce4. That went very well and I used gnome in 8.10 and 9.04. Now, during the upgrade to 9.10 (with gnome), many xfce4 packages were installed. Prior upgrades did not do this - but that is just a side issue.

My login screen is also xfce4-style again. I understand, that there is no gui tool for customization of gdm anymore. So my actual question: How do I get rid of ALL xfce4 packages / files / settings, so that they wont come back (e.g. on upgrade)?!

Can anybody give me advice on this?

Thanks in advance,
greetings

---

### Post by jollysnowman on 2009-11-07
Here's a start...

sudo apt-get remove:
xfce4
xubuntu-desktop
xfce4-goodies

I'm not sure about the login screen... they made it almost impossible to customize...

---

### Post by Sempfinger on 2009-11-07
Thanks, now I removed every xfce4 and xubuntu related package. I did miss some... lets see if this goes well

---

