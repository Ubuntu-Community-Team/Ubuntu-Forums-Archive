---
title: "After reboot/logout xubuntu desktop loaded with errors"
date: 2010-02-26
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-26
Hi,
i am running xubuntu 9.10 on dell mini 10v. Almost all the time i have dell connected with external display.
I have this script to run at startup to connect automatically with external display, and to activate conky and cairo dock:

```
#!/bin/sh
xrandr --output LVDS1 --off --output VGA1 --mode 1366x768 --pos 0x0 --rotate normal
killall conky  
killall cairo-dock
sleep 20 && conky &
sleep 5 && cairo-dock -c 
```

But if i logout/or reboot/start dell with the monitor plugged in, i got serious desktop errors-conky fonts are too big, openoffice menus are also too big.
So, i have to turn on computer unplugged from display, and then to activate that script. And then everything works just fine. Until logout/reboot...

Any idea how can i sort this out?

EDIT: i uploaded two pictures to see difference.

And one more thing-if i logout/reboot-xubuntu wants me to type my password for several times-sometimes can not even log in-it shows constantly log in window-so i need to reboot (although it is set up to login automatically-and normally i don´t have to type it)

---

### Post by vickoxy on 2010-02-26
For the login found help here:
[http://ubuntuforums.org/showthread.php?t=1307810](http://ubuntuforums.org/showthread.php?t=1307810)

ccambell wrote:
> Turns out all I needed to delete is this file:

~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml:popcorn:

FONT Issue: i just set up in xfce setup my own dpi size-after that i was able to correct the conky and openoffice fonts. Still have some issues with vlc and other qt apps-but that´s another story...

---

