---
title: "How does one disable font anti-aliasing without the GUI?"
date: 2006-10-02
forum: Desktop Environments
---

### Post by PatrickMay16 on 2006-10-02
Hello.
I wasn't sure where to put this, sorry if this is the wrong subforum.

I have a slow old computer on which I have done a server install, then installed X, icewm, etc... 
Now, here's the problem. I read that disabling font anti-aliasing would speed things up a bit. But I have no idea how to disable font anti aliasing without the GNOME preferences GUI, and I don't have that installed because GNOME is far too heavy for this computer. 

So, the question is: what configuration file do I edit to disable font anti-aliasing, and what do I add to it/change in it so that font anti-aliasing is disabled?

I'd really appreciate some help here. Oh, and if anyone has any other tips that may cause noticable speed increase for this old machine (AMD K6-2 150MHz, 256MB RAM, 8GB hard disk) I'd be glad to hear them.

---

### Post by Fass on 2006-10-02
```
sudo dpkg-reconfigure fontconfig-config
```

That might do the trick.

---

### Post by croak77 on 2006-10-02
I think in /etc/fonts.conf or locally in ~/.fonts.conf.

---

