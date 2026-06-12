---
title: "Fast User Switching problem"
date: 2007-05-01
forum: Desktop Environments
---

### Post by db9s on 2007-05-01
I have 2 user accounts. And I cannot seem to be able to switch between them. When I try switching it says:

[Dialog title] You do not seem to be logged in on the console
[Message] Staring a new login only works correctly on the console

I click okay, and I get another error that says

[Dialog title] Error while running command
[Message] (gdmflexiserver:29324): Gtk-WARNING **: Ignoring the separator setting

And no switching actually happens. Does anyone know what's up with this?

---

### Post by amohanty on 2007-05-01
Can you post the output of the following:

cat /var/log/Xorg.0.log | grep EE

AM

---

### Post by db9s on 2007-05-01
This is what i get

```

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom


```

weird thing is that this fast-user switching problem only happens.

I also ended up screwing things up even more and don't know how to undo it. 
I ran "sudo telinit 3"
now my typing in "runlevel" shows:
```
 2 3 
```
Does anyone know how to undo this?

Your help is appreciated

---

### Post by amohanty on 2007-05-01
Couple of things, it seems that a bug like this was seen with Edubuntu
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/37253](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/37253)

Are you running a default Ubuntu desktop install?

Secondly, Ubuntu only uses 2 runlevels, unlike redhat or Fedora. runlevel 2 is the full-blown multiuser gui mode. 

I am guessing you wanted to restart X, just try Ctrl+Alt+Backspace in X or startx at the command line.

Also do you have an ATI card?
If so are you using fglrx or the default ATI driver?

AM

---

### Post by db9s on 2007-05-01
I am using an ATI card with fglrx. (is there something about them I should be aware about?)
I also noticed this issue pops up with Beryl.
I'm also a bit concerned about the runlevel command, after restarting and entering command "runlevel" I get 
```
N 2
```

Are those the default values for run level.

---

### Post by Mr. Picklesworth on 2007-05-21
Same situation as db9s here on a fresh Feisty install.
Is there any more information at this point?

---

