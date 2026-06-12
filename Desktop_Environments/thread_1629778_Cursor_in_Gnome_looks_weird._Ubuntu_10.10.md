---
title: "Cursor in Gnome looks weird. Ubuntu 10.10"
date: 2010-11-24
forum: Desktop Environments
---

### Post by majster on 2010-11-24
Hi!

Since five days I having problem with cursor... it is looks weird and usually after reboot it is coming back to normal... the strange think is when i do "print Screen" it looks normal on picture (see attachments) 
I tried to disabled Visual Effects ( compiz ) with no luck.

My system configuration:
**Processor:** Intel Core 2 Duo CPU E7400 @ 2.79GHz (Total Cores: 2), **Motherboard:** ASUSTeK P5KPL-SE, **Chipset:** Intel 82G33/G31/P35/P31 + ICH7, **Memory:** 4027MB, **Disk:** 400GB Hitachi HDT72504, **Graphics:** ATI RV505 [Radeon X1550 64-bit]

Below i attached  print screen and photo of my monitor screen (how i see it )

---

### Post by majster on 2010-11-24
fresh install solved the problem :( 

I did reinstall as reboot the system didn't help any more.

---

### Post by joeoshawa on 2011-01-22
i have the same problem after a while my cursor goes nuts flickering and fading and it stays as one cursor or the other right now its stuck as the cursor for expanding a window so if anyone knows a solution to this please let us know its really irritating to have to constantly log out and in again when i am in the middle of something.

---

### Post by Krytarik on 2011-01-23
@joeoshawa: Although I don't have a real solution at hand, you could just "reload" your mouse instead of re-login, that should fix it also. I wrote the scripts below once for another reason (the mouse wheel of my last mouse sometimes wasn't detected at startup, if the batteries were low). The first one is for USB, the second one for PS2.
```
#!/bin/sh

output1=`gksudo "modprobe -v -r usbhid" | grep rmmod`
output2=`gksudo "modprobe -v usbhid" | grep insmod`

if [ -n "$output1" -a -n "$output2" ]; then
notify-send -i gnome-mouse "USB-HIDs reloaded"
else
notify-send -i error "Reload failed"
fi

exit 0
``````
#!/bin/sh

output1=`gksudo "modprobe -v -r psmouse" | grep rmmod`
output2=`gksudo "modprobe -v psmouse" | grep insmod`

if [ -n "$output1" -a -n "$output2" ]; then
notify-send -i gnome-mouse "PS2/Mouse reloaded"
else
notify-send -i error "Reload failed"
fi

exit 0
```

---

### Post by aaronLund on 2012-03-30
Happens much too often.

Drives me crazy.

The code above doesn't fix it.

It indeed 'reloads' my mouse but doesn't change the effed-up display of the cursor.

You'll probably have to do a "sudo apt-get install libnotify-bin" in order for the above script to work.  Seems to run just fine and I get a "USB-HIDs reloaded" message but my cursors display doesn't go back to normal.

---

