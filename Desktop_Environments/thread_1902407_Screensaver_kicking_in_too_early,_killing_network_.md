---
title: "Screensaver kicking in too early, killing network connection"
date: 2011-12-30
forum: Desktop Environments
---

### Post by bkline on 2011-12-30
I've got a fresh Xubuntu installation on my laptop, and I've run into a problem which I'm not seeing on my other Ubuntu system (where I'm also running Xubuntu, but installed with apt-get install xubuntu-desktop on top of plain Ubuntu).  The problem is that the screen saver is kicking in way before it's supposed to, locking the screen, and (worst of all) killing the network connection.  I've got Lock Screen turned off in the screen saver settings; the mode is set to "Blank screen only" with the "Blank After" value set to 720 minutes.  Power management (under "Advanced" settings) is disabled.  The laptop is running on utility power, not the battery.  If I walk away from the laptop for five minutes I come back to a locked screen, a dead network connection, and therefore all of my ssh connections killed.  This is really annoying.  Why is the screen saver not honoring the settings I'm giving it???

---

### Post by dentaku65 on 2011-12-30
> **bkline said:**
> I've got a fresh Xubuntu installation on my laptop, and I've run into a problem which I'm not seeing on my other Ubuntu system (where I'm also running Xubuntu, but installed with apt-get install xubuntu-desktop on top of plain Ubuntu).  The problem is that the screen saver is kicking in way before it's supposed to, locking the screen, and (worst of all) killing the network connection.  I've got Lock Screen turned off in the screen saver settings; the mode is set to "Blank screen only" with the "Blank After" value set to 720 minutes.  Power management (under "Advanced" settings) is disabled.  The laptop is running on utility power, not the battery.  If I walk away from the laptop for five minutes I come back to a locked screen, a dead network connection, and therefore all of my ssh connections killed.  This is really annoying.  Why is the screen saver not honoring the settings I'm giving it???

On Xubuntu is happened to me too (but network connection stay on); I fixed in this way:
[http://ubuntuforums.org/showpost.php?p=11567191&postcount=6](http://ubuntuforums.org/showpost.php?p=11567191&postcount=6)

---

### Post by bkline on 2011-12-30
> **dentaku65 said:**
> On Xubuntu is happened to me too (but network connection stay on); I fixed in this way:
[http://ubuntuforums.org/showpost.php?p=11567191&postcount=6](http://ubuntuforums.org/showpost.php?p=11567191&postcount=6)

Excellent, thanks!

---

