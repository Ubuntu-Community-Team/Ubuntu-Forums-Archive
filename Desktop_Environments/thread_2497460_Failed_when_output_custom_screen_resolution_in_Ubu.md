---
title: "Failed when output custom screen resolution in Ubuntu 22.04.4 LTS"
date: 2024-05-06
forum: Desktop Environments
---

### Post by ginousi on 2024-05-06
Installed Ubuntu 22.04.4 LTS, and set a custom screen resolution by below command.

#sudo xrandr --newmode "1366x768"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsyn
#sudo xrandr --addmode eDP-1 "1366x768"
#sudo xrandr --output eDP-1 --mode "1366x768"

Will encounter Error message:

X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 139 (RANDR)
  Minor opcode of failed request: 7 (RRSetScreenSize)
  Serial number of failed request: 22
  Current serial number in output stream: 23

[https://i.imgur.com/kUbOglh.jpeg](https://i.imgur.com/kUbOglh.jpeg)


In before, in Ubuntu 20.04.3 LTS, use these commands to add a custom screen resolution,
no error.

 
Is it an known issue in Ubuntu 22.04.4 LTS?
or has method can fix it?


Thanks & Regards.
USIGino

---

### Post by MAFoElffen on 2024-05-07
What is the GPU and the display? This is on X11, not Wayland right?

---

### Post by ginousi on 2024-05-09
>> What is the GPU and the display?
GPU is Tiger Lake  Integrated Graphics 
Display 15.6" eDP LCD panel

>> This is on X11, not Wayland right? 
$ echo $XDG_SESSION_TYPE
wayland

---

### Post by MAFoElffen on 2024-05-11
'xrandr' only works with X11, not wayland.

If at the graphical login panel (GDM3), you use the Gear Icon in the lower right to change the desktop to "Ubuntu on Xorg"... Then those commands will work.

---

### Post by ginousi on 2024-05-23
Switch from the “Wayland” display server to Xorg (X11) in Ubuntu 22.04.4 LTS,
those xrandr commands work fine, thanks.

I have one more question is in "wayland", has method like 'xrandr' to set a custom screen resolution?

I try to use "wlr-randr" and "wdisplay" , both get an error that says compositor doesn't support wlr-output-management-unstable-v1.

---

