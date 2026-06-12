---
title: "Dual Monitors - not save settings after restart"
date: 2010-08-29
forum: Desktop Environments
---

### Post by erngab on 2010-08-29
Kubuntu 10.4
DVI-0 SyncMaster931BF
DVI-1 BenQ G2220HDA

I set the monitors with Display Settings

[[IMG]http://a.imageshack.us/img843/3092/aftersettings1.png[/IMG]]("http://img843.imageshack.us/i/aftersettings1.png/")

[COLOR=#000000]Everything works fine until reboot[/COLOR]
I lose my settings and always returns to the initial state

[[IMG]http://a.imageshack.us/img844/5118/beforesettings.png[/IMG]]("http://img844.imageshack.us/i/beforesettings.png/")

[COLOR=#000000]How can I keep setting?
Thanks

[/COLOR]

---

### Post by erngab on 2010-08-29
I install ATI/AMD proprietary FGLRX graphics driver.
With Catalyst Control Centar I configured dual monitor and work after reboot (settings stay).
Now I can not turn on desktop effects.
They worked without ATI proprietary drivers.
?

When login from KDE to gnome in gnome with compiz effects work.
Dual monitor work.
[COLOR=#000000]Seems to be OK in gnome. KDE problem.[/COLOR]

---

### Post by erngab on 2010-08-29
I do not know how delete dis massage.

---

### Post by inobe on 2010-08-29
> **erngab said:**
> I install ATI/AMD proprietary FGLRX graphics driver.
With Catalyst Control Centar I configured dual monitor and work after reboot (settings stay).
Now I can not turn on desktop effects.
They worked without ATI proprietary drivers.
?

the driver is obviously buggy, ati drivers are known for this, maybe switching back to the opensource ati driver and opening display settings this way

```
gksu display-settings
```

in terminal, then applying to settings.

i am not sure if display settings is the correct name, you may need to verify this especially if the command doesn't work, however you need elevated privileges to make the settings stick and that's the purpose of the command.

---

### Post by erngab on 2010-08-30
[FONT=Verdana][SIZE=2]One part is solved without [/SIZE][/FONT]ATI/AMD proprietary FGLRX graphics driver
[FONT=Verdana][SIZE=2] [http://forum.kde.org/viewtopic.php?f=16&t=20494](http://forum.kde.org/viewtopic.php?f=16&t=20494)
[/SIZE][/FONT][SIZE=2]added lines to Xsetup[/SIZE][FONT=Verdana][SIZE=2] - /etc/kde4/kdm/Xsetup[/SIZE][/FONT] [SIZE=2]
[/SIZE][FONT=Verdana][SIZE=2][FONT=Sans Serif]xrandr --output DVI-0 --mode 1280x1024[/FONT][/SIZE][/FONT][SIZE=2]
[/SIZE]  [FONT=Verdana][SIZE=2][FONT=Sans Serif]xrandr --output DVI-1 --mode 1920x1080[/FONT][/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Verdana][SIZE=2][COLOR=#000000]Resolution of both monitors after restart is good !!![/COLOR][/SIZE][/FONT][SIZE=2]
[/SIZE] [SIZE=2]
[/SIZE] [FONT=Verdana][SIZE=2][COLOR=#000000]There are still one problem. [/COLOR]How can HDI-1 standing left from HDI-0 after reboot?[/SIZE][/FONT][SIZE=2]

[/SIZE]With "xrand --verbose" when HDI-1 is clone of HDI-0 I got:
 [FONT=Sans Serif]DVI-0 connected 1280x1024+0+0 (0x54) normal (normal left inverted right x axis y axis) 376mm x 301mm[/FONT]
  [FONT=Sans Serif]DVI-1 connected 1920x1080+0+0 (0x65) normal (normal left inverted right x axis y axis) 476mm x 268mm[/FONT]
[SIZE=2]
[/SIZE]With "xrand --verbose" when HDI-1 is left from HDI-0 I got:
[FONT=Sans Serif]DVI-0 connected 1280x1024+1920+0 (0x54) normal (normal left inverted right x axis y axis) 376mm x 301mm[/FONT]
  [FONT=Sans Serif]DVI-1 connected 1920x1080+0+0 (0x65) normal (normal left inverted right x axis y axis) 476mm x 268mm[/FONT]

what can I do with this?

---------------------------------------------------------------------------------------------------------------------
Solved
In /etc/kde4/kdm/Xsetup add a line: xrandr --output DVI-1 --left-of DVI-0 
Working after restart.

---

