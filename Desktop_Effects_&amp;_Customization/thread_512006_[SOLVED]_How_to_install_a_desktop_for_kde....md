---
title: "[SOLVED] How to install a desktop for kde..."
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-07-28
I have just re-installed ubuntu server 6.06.1 and now have to install a gui. I want to go for KDE as i had it on my last install but had problems with it, parts of menus were missing, System > Preferences was missing, so i thought there was maybe a  bug and decided to re-install.

Can someone suggest the best option for me:

apt-get install xubuntu-desktop or
apt-get install kubuntu-desktop.

Or any better suggestions, i want KDE...

I have onboard vga with gig ram and athlon 64.

Thanks

---

### Post by aysiu on 2007-07-28
System > Preferences is Gnome, not KDE.

If you want KDE, do ```
sudo apt-get install kubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start
```

---

### Post by upthelum on 2007-07-28
Thanks for the info...

---

### Post by upthelum on 2007-07-28
Ok i now have a fresh install. Could you please tell me the best way to install compiz-fusion? I tried various ways before which didnt seem to work. How do i add themes in kde? Can you point me in the right direction to get this and other tools to configure my desktop?

---

### Post by clitmaster on 2007-07-29
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by upthelum on 2007-08-03
Thanks all i got it installed after an upgrade.

---

### Post by boob11 on 2007-08-13
Thanks for the info...

---

