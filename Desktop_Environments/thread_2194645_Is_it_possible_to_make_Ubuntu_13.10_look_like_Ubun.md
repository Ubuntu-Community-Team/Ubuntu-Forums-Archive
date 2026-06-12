---
title: "Is it possible to make Ubuntu 13.10 look like Ubuntu 9.10?"
date: 2013-12-19
forum: Desktop Environments
---

### Post by Sega dude on 2013-12-19
I want to make my Ubuntu 13.10 install look like Ubuntu 9.10. Is it possible? I'm already using gnome as my default window manager. I want to make it look like 9.10 because it was my very first experience with linux and is nostalgic for me. I basicly want to make it look like the screenshot below. Any help would be greatly appreciated. 

[IMG]http://upload.wikimedia.org/wikipedia/commons/c/c8/Ubuntu_9.10.png[/IMG]

---

### Post by Frogs Hair on 2013-12-19
The wallpapers are in in synaptic , but I don't know of any Gnome 3.8 themes that resemble any of the Karmic default themes. 9.10 was my first Ubuntu.

```
sudo-apt-get install ubuntu-wallpapers-karmic  
```

[http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home)

Icons: [https://launchpad.net/humanity](https://launchpad.net/humanity)

---

### Post by Sega dude on 2013-12-20
> **Frogs Hair said:**
> The wallpapers are in in synaptic , but I don't know of any Gnome 3.8 themes that resemble any of the Karmic default themes. 9.10 was my first Ubuntu.

```
sudo-apt-get install ubuntu-wallpapers-karmic  
```

[http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home)

Icons: [https://launchpad.net/humanity](https://launchpad.net/humanity)

I installed ubuntu-wallpapers-karmic but didn't see them in the background screen in the system settings. Are they somewhere else?

---

### Post by SantaFe on 2013-12-20
I found a link here: [http://ubuntuforums.org/showthread.php?t=2192863](http://ubuntuforums.org/showthread.php?t=2192863) that mentions where you can get the Ubuntu Human theme.

---

### Post by Frogs Hair on 2013-12-20
Looks like they were removed from launch pad , double check synaptic because I haven't  tried to install them in 13.10 . The archive for the Ubuntu wallpapers extra package at the link seems to work, but I don't know about the .deb.  

[http://www.webupd8.org/2010/04/ubuntu-910-karmic-are-saved-in-lucid.html](http://www.webupd8.org/2010/04/ubuntu-910-karmic-are-saved-in-lucid.html)

---

### Post by Sega dude on 2013-12-20
> **SantaFe said:**
> I found a link here: [http://ubuntuforums.org/showthread.php?t=2192863](http://ubuntuforums.org/showthread.php?t=2192863) that mentions where you can get the Ubuntu Human theme.

I downloaded the human theme and applyed it with Tweak Tool. The only thing it changed was the look of the title bars, which I am happy about, but it didn't make the top and bottom bars white. (Was it supposed to?)

Edit: I applied the Radinace Gtk+ theme in tweak tool and it looks almost extactly like it should. I also used a command I found online to move the close, minimize and maximize buttons to the correct side. Here is the result.

[[IMG]http://imageshack.us/scaled/thumb/189/4ex8.png[/IMG]](http://imageshack.us/photo/my-images/189/4ex8.png/)

---

### Post by oldrocker99 on 2013-12-21
Beyond themes, I think what you're looking for is the GNOME 2.3 desktop. You are in luck. There is a modern, actively developed fork of GNOME 2.3, called MATE (pronounced MAH-tay, after the Argentinian caffeinated herb). It is my own personal go-to desktop:

[http://www.mate-desktop.org](http://www.mate-desktop.org)

Installing it for Ubuntu does require the use of a PPA. Here's how to install it:

[http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

I'm hoping that this will help you achieve that 9.10 experience! I first used MATE with Mint 13 (or so). I became irritated with Mint's little quirks, and went back to Kubuntu with MATE, and now I'm a happy GNU/Linux user.

---

### Post by grahammechanical on 2013-12-21
If we are using Ubuntu 13.10 with Unity we can install gnome-session-flashback. It is in the Software Centre. At log in we will get three options 1) Ubuntu 2) Gnome session (with Compiz) 3) Gnome session (with Metacity).

If we are using Ubuntu Gnome 13.10 or have installed Gnome Shell we get the Gnome 3 shell. That has an extension called Gnome Shell Classic that we can install through the Software Centre.

Neither Gnome Flashback, nor Gnome Classic are exactly like Gnome 2 panel. They are both an attempt using different code to give the look of Gnome 2 panel.

Regards

---

### Post by fantab on 2013-12-22
I installed XFCE when nostalgia bit me.... but I tried Cinnamon too.

---

### Post by cincibluer6 on 2013-12-22
Agree with the suggestion to use MATE. It's actively developed and pretty stable if I remember correctly. Cinnamon is also an interesting choice (and 2.0 is available via a repo.)

---

### Post by mcwall1064 on 2013-12-24
And that command is?

---

### Post by cincibluer6 on 2013-12-25
[http://wiki.mate-desktop.org/download#ubuntu](http://wiki.mate-desktop.org/download#ubuntu)

---

### Post by Sega dude on 2014-01-13
Sorry for the late reply, but MATE is exactly what I wanted. I love using Ubuntu even more now that's it's just how I remember it.

---

### Post by oldrocker99 on 2014-01-13
Glad to hear it, and you should know that MATE will be part of the 14.04 repositories, so no PPA will be needed. It remains my favorite desktop, and it's pretty lightweight, too.

---

