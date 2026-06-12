---
title: "Could not open default font &quot;fixed&quot;"
date: 2007-03-03
forum: Desktop Environments
---

### Post by &lt;sVERLo&gt; on 2007-03-03
Hello! I'm newbie in Linux but not computers. Ubuntu is my first Linux, and I'm using it since Dapper. I want to install xgl/compiz. I've tried tons of different manuals and howto's
but all result the same. I even tried to reinstall whole system! 
For example, after doing everything like in here 

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

any way i try to log in with xgl causes the same error:

Your session only lasted less than 10 seconds... cant rememeber the rest of text.

Contents of .xsession-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sverlo"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
Could not init font path element /usr/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/lib/X11/fonts/75dpi/, removing from list!

Fatal server error:
could not open default font 'fixed'

(gnome-session:5362): Gtk-WARNING **: cannot open display:  


My pc conf is 
Athlon XP 2700+
512 DDR PC2700
Soltek KT400A
Nvidia GeForce FX5700 128 mb
HDD Samsung SP1203N
Running Ubuntu Edgy

"could not open default font 'fixed'" As i see the problem is not exactly in xgl. But i have no idea what to do. GNOME without xgl works good, no sign of troubles with fonts. It happens even on just installed, with nothin changed system.

---

### Post by &lt;sVERLo&gt; on 2007-03-06
If nobody helps me, I will kill myself!

---

### Post by jasonbrisbane on 2007-03-07
Since there wasnt any other solutions posted, I thought I'd offer something...


Its sounds like you've messed with something that really shouldnt be messed with.
X doesnt need any playing with. I've had Dapper and now Edgy Eft both working on a Compaq Presario M2000 from scratch and I only needed about 8 lines entered (7 for wpa_supplicant.conf and one to keep the nameserevr in resolv.conf upon networking restarts) to get the entire thing working perfectly.

Its amazing what a quick reinstall of Ubuntu will do!

---

### Post by &lt;sVERLo&gt; on 2007-03-07
How to perform quick reinstall?

---

### Post by jjalocha on 2007-03-10
From what i remember, the 'fixed' font, together with all bitmap fonts, is disabled by default in Debian and Ubuntu. It should be possible to enable them with:

```


sudo dpkg-reconfigure fontconfig


```

---

### Post by jjalocha on 2007-03-15
Sorry, the correct package is:

```

$ sudo dpkg-reconfigure fontconfig-config

```

---

