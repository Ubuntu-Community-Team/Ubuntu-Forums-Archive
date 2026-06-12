---
title: "Global Dark"
date: 2018-05-12
forum: Desktop Environments
---

### Post by pfd272 on 2018-05-12
Is there a way to get the global dark theme option in  18.04?

---

### Post by kazakore on 2018-05-13
What do you mean by Global Dark Theme?

What version of Ubuntu are you using (Ie which Desktop Environment)?

A quick Googling seems to imply doing exactly what I discovered yesterday, although I found it only works for GTK3+ applications and obviously you need to select a theme that has light/dark options built it. Then maybe adjust the GTK2 settings manually. Still stuck on how to get these to apply to Qt apps though....

> 

[LIST]
[*]Manually: create (open if already present) the following file: 
~/.config/gtk-3.0/settings.ini
edit like this:
[Settings]
gtk-application-prefer-dark-theme=1
[/LIST]



But if you're using mainly QT apps (or DE that is QT based) then this may not apply at all.

---

### Post by PaulW2U on 2018-05-13
> **pfd272 said:**
> Is there a way to get the global dark theme option in  18.04?
> **kazakore said:**
> What version of Ubuntu are you using (Ie which Desktop Environment)?
Over the years that I have contributed to Ubuntu I have seen many users post here (and also report bugs) assuming that others will know that they are using the latest release of Ubuntu rather than one of the flavours or an older Ubuntu release.

Assuming that pfd272 is using **Ubuntu 18.04** then he will need to install Tweaks. In a terminal: ```
sudo apt install gnome-tweaks
``` and then when Tweaks is started "Appearance" will be selected. Change "Themes | Applications" to "Adwaita-dark".

@pfd272, does that give you the look that you are wanting? If not, please post back with the flavour and version of Ubuntu that you are using.

---

### Post by kazakore on 2018-05-13
Also see my post here for getting Qt5 apps also following the GTK theme settings.

[https://ubuntuforums.org/showthread.php?t=2391601&p=13766258#post13766258](https://ubuntuforums.org/showthread.php?t=2391601&p=13766258#post13766258)

(EDIT although maybe the vanilla branch does something similar automatically, I don't know. I run Studio and this is what I had to do.)

---

