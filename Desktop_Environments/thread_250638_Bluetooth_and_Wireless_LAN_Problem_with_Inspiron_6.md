---
title: "Bluetooth and Wireless LAN Problem with Inspiron 6400"
date: 2006-09-04
forum: Desktop Environments
---

### Post by goood on 2006-09-04
I have a poroblem with my DELL Inspiron 6400. I have Windows XP and Kubuntu 6.06.1 installed. My problem is, that I'm not able to activate the Bluetooth und WIFI with FN + F2. It doesn't work under Windows, Linux and BIOS.
I tested the keys with the xev tool and the FN key works fine. Also the F2 key works fine but the combination doesn't work although FN works with all other keys (F1,F3,...).

I hope anyone can help me.

---

### Post by sadrak on 2006-09-26
great, i have the same problem, but under windows it works, on the fresh ubuntu 6.06.1 it works too, but now, after i turned it off with FN + F2, i cant turn it on under ubuntu :( all was working :( WPA-PSK and now i cant get the old working status :(

now in the dmesg after pressing FN + F2 there is a command like: 
atkbd.c: Unknown key pressed e008
atkbd.c: Use 'setkeycodes e00a < keycode>' to make it known.

at /usr/share/hotkey-setup/dell.hk (not shure, laptop is at home)

setkeycodes e008 $KEY_  # Wireless

the other codes habe $KEY_COOLNAMES ;)

at /etc/acpi/events/ there are some wireless-acer.sh oder something else for the acer.hk (at hotkey-setup) but nothing for dell :( i cant understand it after 3 days!

what must i do to aktivate my Wifi?!?!


UPDATE:

here is the same problem with solution *hope*:
[http://www.ubuntuforums.org/showthread.php?p=1545539](http://www.ubuntuforums.org/showthread.php?p=1545539)

---

### Post by shamalawy on 2007-07-02
well everyone, i just registred and this is my first post and i hope it's useful.

i had the same problem when i installed vista a few months ago, the dell bluetooth module tends to keep it's last state as a hardware piece regardless of what OS you're using.. so mainly i solved this by reinstalling vista ( ehmmm..) then installing the bluetooth driver again.. even though it didn't want to install because the FN+F2 key wan't turning on the BT module.. but i inforced it by installing the drivers from a local file but i can't remember it's name exactly but i was .BAT.. so here's the thing to make it short..  install the driver of the bluetooth on the last OS or STATE you were using before it totally stopped to work.. even my "inforcing" the driver setup as i did.. hopefully it'll work

LONG LIVE UBUNTU

---

### Post by goood on 2008-02-14
Finally I found the solution.

I just used the ndiswrapper solution because the "restricted drivers" in Kubuntu 7.10 didn't work.

---

