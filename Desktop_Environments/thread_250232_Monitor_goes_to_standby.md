---
title: "Monitor goes to standby"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Corp_Punisher on 2006-09-03
I have read on this topic in several forums as well as this one and many of the dates of those posts are quite old.

In my Power Management I have all setting to never sleep or standby but to always be on (so those settings are "never") I also have my screensaver turned off.

The Screensaver does remain off, but after a short time of inactivity (possibly 20 minutes) the Monitor goes to standby. Fortunately this has had no ill effects when ripping and burning a DVD, but it is a major pain in the *** when watching a movie.

Has this issue ever been resolved yet? Kubuntu, as far as I can remember did not have this problem. Is it a difference of the Gnome Environment as opposed to the KDE? Or is it a deeper difference between Ubuntu and Kubuntu?

---

### Post by Corp_Punisher on 2006-09-03
Bump

---

### Post by Omnios on 2006-09-03
Not 100% shure but think it has to do with the 
```

Section "Monitor"
    Identifier    "A91f+"
    Option        "DPMS"
    HorizSync    30-100
    VertRefresh    50-160

```
 DPMS option in the xorg.conf

---

### Post by orb9220 on 2006-09-03
command 
xset q
will give the states of various settings.

I had to go into my xorg.conf file and comment # in front of the line about DPMS so it would turn off dpms

---

### Post by Corp_Punisher on 2006-09-03
I just now editted the xorg.conf file as such:

[http://www.ubuntuforums.org/showpost.php?p=988498&postcount=6](http://www.ubuntuforums.org/showpost.php?p=988498&postcount=6)

I'll post the results. Thx ;)

---

