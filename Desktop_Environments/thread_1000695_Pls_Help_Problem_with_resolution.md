---
title: "Pls Help Problem with resolution"
date: 2008-12-03
forum: Desktop Environments
---

### Post by ivikas on 2008-12-03
Hello all,

          I need very urgent help and please be kind to give me a quick steps.Here is my problem.I am running ubuntu 8.04.1 with all updates installed on intel x86 machine with nvidia graphics card.I have a monitor of make "ViewSonic VA1703wb" and this requires a resolution of "1440x900" and 60 Hz reolution.I installed the driver for nvidia using restricted driver manager.I have also installed oracle-xe.Everything was working fine.

                    [COLOR="Red"]Now the problem is all of sudden the screen resolution have set to some 800x600 resolution and everything is appearing huge.I have no option to select 1440x900 from the screen resolution.How can i restore my screen resolution to 1440x900,if it is possible or should i have to re install hardy.
[/COLOR]

---

### Post by Zorael on 2008-12-03
Have you tried recreating your xorg.conf file?

```
$ cd /etc/X11
$ sudo mv xorg.conf xorg.backup0812
$ sudo dpkg-reconfigure -phigh xserver-xorg
$ sudo nvidia-xconfig -d 24 --add-argb-glx-visuals --randr-rotation
```

Omit last line if you don't want to reenable the proprietary nvidia driver. It will spout some error message about your xorg.conf being incomplete; ignore that.

Then log out to cleanly shut down running applications, and restart X with Ctrl+Alt+Backspace.

---

### Post by ivikas on 2008-12-03
Hello Zorael,

           >  $ cd /etc/X11
            $ sudo mv xorg.conf xorg.backup0812
            $ sudo dpkg-reconfigure -phigh xserver-xorg

I have done the above steps but it didn't work.in some post i read that we can set screen resolution by using "screens and graphics" tool.so i uninstalled nvidia,set up resolution 1024x768 which is good but the better resolution of 1440x900 is not getting.After this now i have reinstalled nvidia and so far so good.

                 One more question,can we set the resolution 1440x900 manually using commandline?Is there any tech Howto to get around this screen resolution problems?

---

