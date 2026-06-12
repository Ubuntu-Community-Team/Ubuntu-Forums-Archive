---
title: "Unfailable keybindings in fullscreen mode"
date: 2006-12-03
forum: Desktop Environments
---

### Post by taiyo on 2006-12-03
Hello everyone!

I did a quick search on the forums but nothing appropriate came up, I have several questions anyhow:

I am using Xubuntu 6.10 with Beryl and latest nVidia drivers (no AI/XGL) BUT **gnome-settings-daemon** because of my multimedia keyboard.


1.) When using a program in fullscreen (particulary games) they seem to disable all keybindings/shortcuts except switching to a terminal... I would like my multimedia keys to "get through" so I can browse through my music while gaming. Alt+Tab would also come in handy. Where can I configure these special bindings?

2.) On my old Edgy machine (recently built a new pc) I managed to get vga=791 (terminal resolution = 1024x768) accepted, but now it does not seem to work. Where do I have to configure this?

3.) How can I change the terminal font?

I appreciate any kind of help

regards
Taiyo

---

### Post by Jakobo.C on 2006-12-03
At least I can answer your second question ...

> **taiyo said:**
> 

2.) On my old Edgy machine (recently built a new pc) I managed to get vga=791 (terminal resolution = 1024x768) accepted, but now it does not seem to work. Where do I have to configure this?


You have to edit /boot/grub/menu.lst - like in the example

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash [COLOR="Lime"]vga=794[/COLOR]
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

---

### Post by syrleb on 2006-12-03
go to terminal, click on edit, go to current profile and change font in there

---

### Post by taiyo on 2006-12-04
Thank's for the answers so far.

Jakobo C. : Thanks, I thought I had done that already but appearantly I did not ;D.

syrelb: I need to clarify myself here: I am talking about the tty terminal fonts, not the various X embedded ones.

Anyhow, the first question is the one which interests me most :)

---

### Post by taiyo on 2006-12-11
Hi again!

Sorry for bumping this, but noone really seems to have an answer to my first question:

1.) When using a program in fullscreen (particulary games) they seem to disable all keybindings/shortcuts except switching to a terminal... I would like my multimedia keys to "get through" so I can browse through my music while gaming. Alt+Tab would also come in handy. Where can I configure these special bindings?

But I think many people would be interested in how this can be done as it would be very usefull when using fullscreen accelerated programs. Right now it is impossible to switch out of them, at least for me.

Please help!

---

