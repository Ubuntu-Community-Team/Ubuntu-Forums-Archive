---
title: "blank screen"
date: 2006-07-17
forum: Desktop Environments
---

### Post by xyuri on 2006-07-17
I have booted the ubuntu (desktop) cd on my desktop but after the loading section when gnome is surposed to start loading I just get a blank screen. I suspect this is something to do with my monitor or video card? Couple someone please help me I am a linux n00b and would like to try ubuntu outside of a vm.

My video card and monitor:

ATI X800 pro
Samsung SyncMaster 713n

Any help would be appreciated. Thanks :)

---

### Post by Ramses de Norre on 2006-07-17
This may solve it: (did so on my ati x600)
Go to a tty (ctrl-alt-F1)
log in
```
cd /etc/X11
sudo cp -p xorg.conf xorg.conf.bak
sudo vi xorg.conf
```
Scroll down to the driver section
press i to go into insert mode and change the driver (probably set to ati or radeon) to vesa (Driver "vesa").
Press esc, shift q, enter "wq!" and enter.
```
killall Xorg
sudo /etc/init.d/gdm start (or kdm)
```
When you're able to login, go to a terminal and do ```
sudo aptitude update && sudo aptitude install xorg-driver-fglrx
echo fglrx|sudo tee -a /etc/modules
```
Then edit /etc/X11/xorg.conf again and set fglrx as driver instead of vesa, press ctrl-alt-del to restart X and you're using the fglrx driver (3d accel).

If this doesn't work at all you can undo all changes by doing ```
sudo cp -p /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
And deleting the last line of /etc/modules (should contain fglrx)

---

### Post by xyuri on 2006-07-17
I have not installed ubuntu, this is booting straight from the cd. I think it actually crashes as the gui part so going to a terminal would be unlikely.

Acyually, thinking about it now, the same thing is happening if i do this on my other machine which is using the same monitor, but a GeForce 4.

Maybe booting in VGA? (I'm not trying this now ... have too much work to do atm).

---

