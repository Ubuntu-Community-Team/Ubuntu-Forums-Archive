---
title: "Attempted customized Ubuntu with IceWM"
date: 2008-12-21
forum: Desktop Environments
---

### Post by RJARRRPCGP on 2008-12-21
When I follow the instructions from this web site: 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

With this:

```
sudo apt-get install xorg xterm gdm icewm menu
```

Then after I reboot and it loads, it fails to respond to the keyboard and mouse! Thus, cannot login! 

Thus, all I can do is Ctrl-Alt-Del ! 

That's the only thing it responded to! 

This is bizarre! 

Thus, I was forced to reformat and reinstall, then chose Gnome, just to get back completely online! 

Anyone else came across this problem when wanting a small Ubuntu?

---

### Post by RJARRRPCGP on 2008-12-23
I'm puzzled! It makes me think a dependency problem without apt-get even telling me about any! 

apt-get should have errored.

---

### Post by kerry_s on 2008-12-23
i'd say try again, when your doing a base build things happen.

you might want to give lenny a try to, just incase it's just a ubuntu problem. the instructions are pretty much the same.

[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

at package selection uncheck the desktop.
log in as root
apt-get install xorg gdm icewm menu synaptic
reboot (ctrl+alt+delete)

i left out xterm, cause it's part of xorg and will get installed anyway.

---

