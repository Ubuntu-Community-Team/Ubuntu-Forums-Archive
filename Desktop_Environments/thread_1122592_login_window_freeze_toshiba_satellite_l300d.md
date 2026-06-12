---
title: "login window freeze toshiba satellite l300d"
date: 2009-04-11
forum: Desktop Environments
---

### Post by jamesvar_70 on 2009-04-11
hi all,

i got installed ubuntu 8.10 intrepid about three months back and things were fine for about two months. i got kubuntu desktop installed and i had no problem for a week. about three weeks back i stumbled upon freezing on login window. there is no key board no touch pad and i could login as root in the recovery mode and i did lot of trouble shooting spending lot of time in ubuntu forums and googling. after two days struggles i gave up and reinstalled ubuntu 8.10.

this time i have decided not to go for kubuntu but yesterday again the same problem. the login window freezes i have again gone through the same painful experience. i have tried several things as suggested by many in different forums but nothing works.

i have done the following things

1. add `highres=off nohz=off irqpoll` at the end of the /grub.lst kernel boot menu
2. removed compiz*
3. removed fglrx, video-radeon 
4. reinstalled video-ati
as a last resort i got installed kubuntu-desktop
but no use

i can login as root and as user (Alt+F2) in the console.

my system configuration is

processor : amd turion x2 64 bit
memory : 3 gb
hard disk : 160 gb
video card : ati radeon 3100

i am using huawei mobile connect 3g modem

i dont want to go for another re-installation losing all my favorite packages installed

also i tried to install the latest ubuntu 9.04 by typing sudo update-manager -d` hoping to get my system back. but it fails in the console mode.

any help will be greatly appreciated.

thanks in advance

james

---

### Post by jamesvar_70 on 2009-04-12
i could get past my problems
i shall describe it for anyone facing similar problem

1. the actual problem started with dbus upgrade i believe ( i am not an expert only a user so it is based on my experience) 
2. i was trying to upgrade empathy to 2.26.0.1 it demands upgrading dbus and i upgraded it to dbus 1.2.12
3. it changed the /usr/local/var/run/dbus/system_bus_socket location and as a result hal did not load keyboard, touchpad and mouse pointer all gone missing
4. i figured it out from /var/log/xorg.log, it showed like cannot locate pointer device, cannot locate core keyboard device etc. if you restart hal-device it will show error like * Reloading system message bus config... Failed to open connection to system message bus: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed..

5. the solution is follow the steps in 
[http://ubuntuforums.org/showthread.php?t=619497&page=2](http://ubuntuforums.org/showthread.php?t=619497&page=2)

sudo ln -s /var/run/dbus/system_bus_socket /usr/local/var/run/dbus/system_bus_socket

now reload hal

restart

and your touchpad keyboard all will get their life back

i was struggling with this for last two three days though i have a vista alongside

now good luck if this help u in anyway

bye

:lolflag:

---

