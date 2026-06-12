---
title: "xserver-xorg-video-intel driver issues"
date: 2007-05-24
forum: Desktop Environments
---

### Post by schmelly on 2007-05-24
Hello together,

i am using ubuntu feisty and have some problems with logging in into gnome:

after upgrading from the xserver-xorg-video-i810 to the xserver-xorg-video-intel driver im not able to log in into gnome with my main user account anymore (only via an xterm session). the x server crashes immediatly after logging in via gdm with the following error message:

```
May 24 12:05:11 laptop gconfd (schmelly-23135): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle aufgelöst
May 24 12:05:11 laptop gconfd (schmelly-23135): Die Adresse »xml:readwrite:/home/schmelly/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
May 24 12:05:11 laptop gconfd (schmelly-23135): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelöst
May 24 12:05:11 laptop gconfd (schmelly-23135): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle aufgelöst
May 24 12:05:11 laptop gconfd (schmelly-23135): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelöst
May 24 12:05:13 laptop gconfd (schmelly-23135): Signal 15 erhalten, ordungsgemäßes Herunterfahren
May 24 12:05:13 laptop gconfd (schmelly-23135): Beenden
May 24 12:05:13 laptop gdm[23073]: gdm_slave_xioerror_handler: Schwerwiegender X-Fehler - :0 wird neu gestartet
```

however logging in with a new created user is no problem.


any ideas how to fix this problem? maybe i can reset the whole gnome configuration but how can i do this?

---

### Post by schmelly on 2007-05-24
i removed all gnome specific folders in my home directory (like .gnome, .gnome2, .metacity, .gconf, .gconfd,...) and it works again


im not sure if this is the best way to fix the problem...

---

