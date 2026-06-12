---
title: "Gnome &amp; KDE 2gether?"
date: 2009-01-28
forum: Desktop Environments
---

### Post by The_Real_Anna on 2009-01-28
For some STUPID reason I decided to install KDE WITH my already perfectly working Gnome DE.

How do I uninstall all the KDE crap off of here?

I used to use KDE back in 2003 when I had MEPIS linux...

Sad memories...

---

### Post by XanTrax on 2009-01-28
Believe its just

```
sudo apt-get remove kubuntu-desktop
```

and select GNOME from the login screen.

---

### Post by snova on 2009-01-28
Removing the kubuntu-desktop package will do just that, remove kubuntu-desktop. There's nothing in it, as it's a metapackage.

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by Giant Speck on 2009-01-29
> **snova said:**
> Removing the kubuntu-desktop package will do just that, remove kubuntu-desktop. There's nothing in it, as it's a metapackage.

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

I agree with the above.  This will remove all traces of KDE and its associated programs.  You may also want to go into Synaptic and remove any Kubuntu or KDE-related repositories, if there happen to be any in there.

---

### Post by pritamps on 2009-01-29
You could also try

```
sudo apt-get remove kdelibs5
```

---

