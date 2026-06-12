---
title: "bzflag errors"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by akurashy on 2005-11-10
my friend invited me for a nice game of bzflag, but i can't run it, it gives me this error

> 
david@akulinux:~$ bzflag
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x115
  Serial number of failed request:  123
  Current serial number in output stream:  125
david@akulinux:~$


I thought it was the driver (and since I didn't had nvidia driver i installed it right away ([http://flickr.com/photos/akurashy/61864764/](http://flickr.com/photos/akurashy/61864764/))

---

### Post by Neeko on 2005-11-10
I get this error when trying to play in full screen. The only "fix" I am aware of is to play in a (large) window, which works fine.

---

### Post by akurashy on 2005-11-10
what fix in where? :S

---

### Post by etc on 2005-11-10
Run bzflag in a window by running
bzflag --window

---

### Post by Pauleberber on 2005-11-28
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xcf
  Serial number of failed request:  122
  Current serial number in output stream:  124

und im Fenster läufts, nur wie mache ich das Fenster möglichst groß? Weil sobald ich das Spiel gestartet habe ist meine Maus dort gefangen. Gibt bestimmt nen Shortcut um sich aus einem Fenster wieder zu befreien oder?

---

### Post by alinuxfan on 2006-01-14
i can't read what you wrote but I am getting the same error...
any ideas anyone?

---

### Post by louisgag on 2006-01-15
did you try installing the latest version from source? I had problems too on 5.10, my bullets weren't seen nor felt by my ennemies!!! Until I went to the bzflag site, got the latest .tar.gz and ./configure make isntall...

:)

---

