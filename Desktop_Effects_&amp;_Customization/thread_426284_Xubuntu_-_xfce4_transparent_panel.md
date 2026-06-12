---
title: "Xubuntu - xfce4 transparent panel"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by jcornuz on 2007-04-28
Hi there !

There was a patch lying around (see blog by Jasper Huijsmans [here]("http://blog.xfce.org/?p=177")) that turns the xfce4 panel into a "real" transparent panel with opaque icons. It is not perfect, but looks kinda cool, so I salvaged a xfce4-panel deb which incorporates the patch. 

Maybe other are interested to have a go...

_To install_: grab the xfce4-panel file and install with gdebi.
_To remove_: clicking on update manager will reinstall the default version.

I also attached the obligatory screenshot...

Take care,

Joël

---

### Post by whayong on 2007-05-02
What kind of hardware is necesarry to run this?  I tried to set transparent windows on Xubuntu Feisty last night and my PIII M didn't like it and didn't want to boot anymore.  I have a PIII 800M 386 MB RAM, video card is shared 16MB.

---

### Post by mrazster on 2007-05-02
Tried to install it with gdebi....and it borked my X...total freeze.
Restarted and no panel....couldn't reisntall I got an error message about synaptic or updatemanager...hade to run:
 ```
sudo dpkg --configure -a
```

Then reinstalled the "original" panel......all is fine now...put I can't get your panel isntalled.

---

### Post by n2j3 on 2007-05-31
Hmm.. just installed the .deb you attached but for some reason the System Tray plugin does not seem to work properly. 
In bitmap,
[[IMG]http://img353.imageshack.us/img353/8350/200706010346191024x768skn1.th.png[/IMG]](http://img353.imageshack.us/img353/8350/200706010346191024x768skn1.png)

(The beryl icon on the left and the two "cog-like" icons should not be there!) 

Any ideas?

---

