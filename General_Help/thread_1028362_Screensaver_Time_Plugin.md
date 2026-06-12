---
title: "Screensaver Time Plugin?"
date: 2009-01-02
forum: General Help
---

### Post by RookieUbuntuUser58 on 2009-01-02
Is there a plug-or or download available that lets me display the time in the screensaver? Thanks in advance.

---

### Post by PhrankDaChickenGeek on 2009-01-02
> **boost3d23 said:**
> Is there a plug-or or download available that lets me display the time in the screensaver? Thanks in advance.

the GLText screensaver will do this.
You'll need to manually edit it, though...
```

$ sudo nano /usr/share/applications/screensavers/gltext.desktop

```

replace this line
```

Exec=gltext -root

```

with this:

```

Exec=gltext -root -text "%A%n%d %b %Y%n%l:%M:%S %p"

```

Ctrl+X and Y to save.

Make sure to set GLText as your screensaver in GNOME prefs.

---

### Post by cheapodonuts on 2011-07-19
Hey Phrank,
 This looks interesting. Do you know if this will work in Maverick?
Cheers, Pete.

---

