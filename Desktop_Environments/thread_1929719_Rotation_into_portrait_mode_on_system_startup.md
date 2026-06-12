---
title: "Rotation into portrait mode on system startup"
date: 2012-02-22
forum: Desktop Environments
---

### Post by nicks27 on 2012-02-22
I have a problem with two conflicting lines in /etc/X11/xorg.conf.

In the "Device" section I need the line:
```
Option "Rotate" "Left"
```so that my screen is oriented in portrait mode on system startup. 

But in the "Screen" section I need the line:
```
Option "RandRRotation" "True"
```so I can avoid the error:
```
Xlib:  extension "RANDR" missing on display ":0.0"
```However when both the above lines are in my xorg.conf, I get the following error in  /var/log/Xorg.0.log:
```
[    18.828] (**) NVIDIA(0): Option "RandRRotation" "True"
[    20.024] (WW) NVIDIA(0): RandR rotation is not compatible with the Rotate option.
[    20.024] (II) NVIDIA(0): The RandR extension is not compatible with the Rotate option. 
[    20.024] (II) NVIDIA(0):     Disabling RandR.
[    20.255] (--) RandR disabled
```I have to eliminate the  Option "Rotate" "Left"  line to resolve this, but now my system doesn't boot up in portrait mode.

Is there any way I can resolve this problem so the system boots up in portrait mode and I don't get the errors?

I'm using the NVidia driver version 280.13 driver (*nvidia-current, nvidia-current-updates, nvidia-settings, *and *nvidia-settings-updates* packages). and the hardware is an nVidia Corporation G73 [GeForce 7300 GT] (rev a1). It's just a single display setup. I'm running an up-to-date Xubuntu 11.10 with kernel 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 athlon i386 GNU/Linux.

---

### Post by nicks27 on 2012-03-04
I have partially resolved this by creating a new file:
[INDENT][FONT=Courier New]/etc/X11/Xsession.d/45custom_xrandr-settings[/FONT]
[/INDENT]containing the command:
[INDENT][FONT=Courier New]xrandr -o "left"[/FONT]
[/INDENT]The display now automatically rotates into portrait mode but only *after* I've logged in. It would be preferable to have the login screen displayed in portrait mode too, but where does the xrandr command need to go to achieve this?

---

