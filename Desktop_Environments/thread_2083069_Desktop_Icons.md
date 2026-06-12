---
title: "Desktop Icons"
date: 2012-11-11
forum: Desktop Environments
---

### Post by Riffronan on 2012-11-11
How do I get the icons 'Computer, Home and Trash' off the desktop?  I thought there were settings in Ubuntu Tweak for that but I'm not seeing it.  I'm running Mate with compiz on 12.04 Ubuntu.  Thanks!

---

### Post by howefield on 2012-11-11
Not sure about Ubuntutweak, but MyUnity has that ability, should be installable from the Software Centre.

---

### Post by Frogs Hair on 2012-11-11
Install the Gnome Tweak Tool and make selections under desktop.

---

### Post by mcduck on 2012-11-11
...or if you want a solution that doesn't require installing any extra applications, just open a terminal and run the following commands:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
gsettings set org.gnome.nautilus.desktop home-icon-visible false
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```

---

### Post by Riffronan on 2012-11-12
I appreciate all the replies and I tried mcduck's but it didn't work.  I've installed mate-conf-editor and can't find the right keys...

---

### Post by Riffronan on 2012-11-12
did some digging..open mateconf-editor in terminal, then uncheck apps/caja/preferences/show_desktop

[http://www.securitronlinux.com/wp-content/uploads/2012/06/mate.jpeg](http://www.securitronlinux.com/wp-content/uploads/2012/06/mate.jpeg)

---

### Post by mcduck on 2012-11-12
> **Riffronan said:**
> I appreciate all the replies and I tried mcduck's but it didn't work.  I've installed mate-conf-editor and can't find the right keys...

Oh, good point, Mate doesn't use Nautilus any more as the file manager. Which is also why Ubuntu Tweak, MyUnity or Gnome Tweak Tool (or any other tool made for configuring Gnome & Unity) won't work either.

---

