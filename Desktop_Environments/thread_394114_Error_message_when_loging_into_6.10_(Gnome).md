---
title: "Error message when loging into 6.10 (Gnome)"
date: 2007-03-26
forum: Desktop Environments
---

### Post by McNabUx on 2007-03-26
Hi

I have been testing and changing alot around xorg, and ended ut with an keyboard error.
i got that fixed, but now i get an error message when i log on.

You can see the message at : [http://bildr.no/view/49263]("http://bildr.no/view/49263")

---

### Post by Khaled Khalil on 2007-03-26
oops, is this norwegian ? , i found some online translation tools but still can't write some characters, but obviously it is related to xorg also to keyboard
i can't help you technicaly, but if you would like to reconfigure /etc/X11/xorg.conf run this code ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` it will ask you some question, reply theme accurately and all should go fine.
if you don't want to take the risk to lose the current xorg.conf copy it to another name:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bac1
``` then return it back anytime you want:```
sudo cp /etc/X11/xorg.conf_bac1 /etc/X11/xorg.conf
```

//edit:
if you don't have another desktop installed you can run the commands from tty terminal (alt + ctrl + F[1-6]), then return back to gui by alt + ctrl +F7

---

### Post by McNabUx on 2007-03-27
Hi

Thanks for your replay, i will test it when i get back home from work.
Sorry about the error message beeing in norwegian, i dident think about that :)

---

### Post by McNabUx on 2007-03-28
If i do this i get setup for grafik driver and screen resolution.
After i setup this i get this error . 

thor@linux-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070328200718

---

### Post by Khaled Khalil on 2007-04-04
hi again, sorry for late
> 
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20070328200718
unfortunately, i am not very experienced and i am not sure what that means :confused: 
but as workaround can you post here your /etc/X11/xorg.conf file ? or at least the keyboard section
or change it, here is mine for comparison:
> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection
may be that help
as i said, i am not very experienced, don't trust me, and make backup for every thing.
i hope someone who can help come here soon

---

