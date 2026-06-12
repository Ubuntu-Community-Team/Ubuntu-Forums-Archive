---
title: "monitor powerdown/suspend not working in gnome"
date: 2006-09-11
forum: Desktop Environments
---

### Post by piroshki on 2006-09-11
I recently used FAI to install Dapper Drake on an HP dx5150 with a HP L1906 19" LCD.
After struggling with some SATA hard drive problems I finally got it up and running, but realised that the monitor suspend feature which works on my other Ubuntu boxes isn't working on this one.

It's not such a problem when I'm logged into gdm as the screensaver kicks in, but if I leave it sitting on the login window (which I need to be able do) then it's a recipe for burn-out.

I have at least the following power related packages installed:

```
dpkg -l|grep power
ii  acpid                                1.0.4-1ubuntu11                         Utilities for using ACPI power management
ii  gnome-power-manager                  2.14.3-0ubuntu11                        Power management policy frontend for GNOME
ii  powermanagement-interface            0.3.11                                  platform neutral powermanagement interface
ii  powermgmt-base                       1.23                                    Common utils and configs for power managemen
ii  powernowd                            0.97-1ubuntu1                           control cpu speed and voltage using 2.6 kern
```

```
dpkg -l|grep acpi
ii  acpi                                 0.09-1                                  displays information on ACPI devices
ii  acpi-support                         0.85                                    a collection of useful events for acpi
ii  acpid                                1.0.4-1ubuntu11                         Utilities for using ACPI power management
```

```
dpkg -l|grep apm
ii  apmd                                 3.2.2-3ubuntu2                          Utilities for Advanced Power Management (APM
ii  libapm1                              3.2.2-3ubuntu2                          Library for interacting with APM driver in k
ii  xserver-xorg-driver-apm              1.0.1.5-0ubuntu1                        X.Org X server -- APM display driver
```

I haven't messed with any of the init.d services which are loaded in each runlevel, but this system is a few packages short of a complete ubuntu-desktop image. Hopefully I'm just missing a package...

My xorg verions are as follows:
```
ii  xserver-xorg                         7.0.0-0ubuntu45                         the X.Org X server
ii  xserver-xorg-core                    1.0.2-0ubuntu10.4                       X.Org X server -- core server
ii  xserver-xorg-driver-all              7.0.0-0ubuntu45                         the X.Org X server -- output driver metapack
ii  xserver-xorg-driver-apm              1.0.1.5-0ubuntu1                        X.Org X server -- APM display driver
```

"xset -q" shows:
```
DPMS (Energy Star):
  Standby: 0	Suspend: 0	Off: 0
  DPMS is Enabled
  Monitor is On
```

even though the layout section of my xorg.conf contains:
```
        Option          "OffTime" "3"
        Option          "BlankTime"     "4"
        Option          "StandbyTime"   "5"
        Option          "SuspendTime"   "6"
```

and the screen section of my xorg.conf file contains:
```
Section "Monitor"
        Identifier      "HP L1906"
        Option          "DPMS"
EndSectio
```n

I have also tried:
```
	Option		"DPMS"	"true"
```

"xset dpms force off" does a whole lot of nothing.

I have the following settings in gnome-power-preferences:
"Put display to sleep when computer is inactive for:" 2 minutes
"Put computer to sleep when it is inactive for:" Never
"Sleep type when inactive:" Suspend
"Sleep button action:" Suspend


The following commands all manually power down the lcd but keystrokes, mouse movements and mouse clicks don't re-awaken it:
```
~# vbetool dpms off
~# vbetool dpms standby
~# vbetool dpms suspend
```

I have to run the following to bring the lcd back to life:
```
~# vbetool dpms on
```

Does anyone have an idea what's going wrong? Or can someone tell me what method ought to be working, so I know what to concentrate on?

Thanks

---

