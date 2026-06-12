---
title: "Changing Desktops"
date: 2014-08-02
forum: Desktop Environments
---

### Post by gordon99 on 2014-08-02
Having installed Ubuntu 14.04 with Unity desktop I later changed to Classic desktop. I would now like to try xfce desktop which has been recommended. Would someone please let me know how best to install xfce and remove any clutter that might be left from Unity/Classic desktops.
Thanks

---

### Post by startas on 2014-08-02
Download xubuntu -> burn xubuntu iso to cd/usb -> boot from it -> format current ubuntu partition and install xubuntu on it. I do not recommend to just install xfce from synaptics, as it would be pain is the ass, because that xfce would be just plain xfce without configurations and other stuff, plus uninstalling unity from ubuntu will mess up your system with a high chance, so using xubuntu is the best and easiest way.

---

### Post by gordon99 on 2014-08-03
Thanks for your advice startas. Could you enlighten me further please? When you say format the ubuntu partition is this the Ext 4, File system root partition? Presumably,if it is, I leave the /data and the swap partitions well alone. Is the procedure order exactly as you say, i.e burn-boot-format-install ? Will both Unity and Classic desktops files be removed with ubuntu?

---

### Post by startas on 2014-08-03
Well, it would be more easy to just copy your personal data to some usb flash, cd/dvd or anything else, and just completely format hdd and install xubuntu same way you installed ubuntu. Yes, xubuntu is same ubuntu, just with only xfce de, and it also has completely removed unity.

---

### Post by felly2 on 2014-08-03
just like installing new apps on it

---

### Post by sammiev on 2014-08-03
> **startas said:**
> Well, it would be more easy to just copy your personal data to some usb flash, cd/dvd or anything else, and just completely format hdd and install xubuntu same way you installed ubuntu. Yes, xubuntu is same ubuntu, just with only xfce de, and it also has completely removed unity.

+1 but I would not completely format the whole hdd unless you only have linux on it. Just need to delete and format the part with Ubuntu on it and format that area.
Gparted is a great tool for that and is included on the installation DVD/USB.

---

### Post by oldrocker99 on 2014-08-03
I have had no problem using
```
sudo apt-get xubuntu-desktop xcfe
```

This installs the official Xubuntu desktop and all the XCFE files that are not included in the Xubuntu installation. There's [/b]no need[/b] to reformat; choice of which desktop you log into is one of the greatest features of this OS.

---

### Post by drfox on 2014-08-03
> **oldrocker99 said:**
> I have had no problem using
```
sudo apt-get xubuntu-desktop xcfe
```

This installs the official Xubuntu desktop and all the XCFE files that are not included in the Xubuntu installation. There's [/b]no need[/b] to reformat; choice of which desktop you log into is one of the greatest features of this OS.

Totally agree. Once you're sure that you like xubuntu, you can remove the gnome desktop. There's a tutorial here for version 13.04:
[http://www.psychocats.net/ubuntucat/pure-xubuntu-13-04/](http://www.psychocats.net/ubuntucat/pure-xubuntu-13-04/)
but it might not clean everything or it could break your system if you're running 14.04.
Instead of using UbuntuCat's script, I would suggest selecting and removing the gnome programs you don't like. You may choose to keep some gnome programs (like gedit or nautilus) if you like them better than their xfce analogs.
HTH
Larry

---

### Post by Bucky Ball on 2014-08-03
Just do this:
```

sudo apt-get install xfce4
```

Log out, choose 'xfce session' from the Sessions menu.

_Do not_ install xubuntu-desktop! Bad advice and will drag in LOTS of stuff you don't want or need. If you install xubuntu-desktop, you may as well just install Xubuntu on another partition or try it from the disk and save yourself some bloat (and possible conflicts, confusion and duplication).

PS: There is no such thing as 'xfce' to install that I know of; it is 'xfce4' and if you install xubuntu-desktop, as advised by other posters, xfce4 is pulled in anyway. Redundant to install it. If there is a link that says to 'sudo apt-get xubuntu-desktop xfce' please provide it.

PPS: To the OP; removing clutter from this might be a nightmare/needle in a haystack ride involving breakage. I think psychocats has a guide to something like it. Have a look. They also have guides on how to install xfce4 to try it, as do many other websites ...

---

### Post by gordon99 on 2014-08-04
Thanks everybody for your interest and suggestions. In the end I came across the following website which I found easy to follow," https://sites.google.com/site/easylinuxtipsproject/alternative".
I followed the guide, including some of the follow-up tips and it all seems to be working ok. The keyboard ampersand and italics keys swapped places but I sorted that out. Thanks once again.

---

