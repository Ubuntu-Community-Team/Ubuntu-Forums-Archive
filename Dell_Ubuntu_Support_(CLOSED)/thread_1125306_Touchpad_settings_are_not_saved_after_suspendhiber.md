---
title: "Touchpad settings are not saved after suspend/hibernate XPS m1530"
date: 2009-04-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tishko on 2009-04-14
Hello,

I am running ubuntu 8.10 64b on dell xps m1530 laptop. I have some issues with my touchpad settings. Here is a brief description of my problem.
1.After fresh install the touchpad was jumping arround.
2.After installing the available updates the touchpad was acting normally but really slow.
3. I installed gsynaptics
4. I added the following to the xorg.conf 

[COLOR="Blue"]Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
        Option "SHMConfig" "true"
EndSection[/COLOR]

5. In order to make the gsynaptics graphical environment to work, I enabled the SHMConfig by adding the following lines to 
/etc/hal/fdi/policy/shmconfig.fdi

[COLOR="Blue"]<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>[/COLOR]

6.Ok. those were standard procedures for fixing touchpad problems. However **after suspend or hibernation my touchpad settings are lost and the touchpad is again slow**. When I look at the gsynaptics graphical settings all the settings are reset. Note that **after reboot the settings are not lost.**

I tried adding the following lines to the synaptics section in xorg.conf
[COLOR="Blue"]
Option      "MinSpeed"   "0.70"  # speed factor 
Option      "MaxSpeed" "0.70"  # maximum speed factor 
Option      "AccelFactor" "0.70"    # acceleration factor[/COLOR]

but it did not make any difference.
I tried to run gsynaptics as root:

[COLOR="Blue"]gksudo gsynaptics[/COLOR]

Set the sliders to desired values and then close. It did not make any difference again.

Please, help me resolving this issue as it is really bugging me to set everytime the touchpad after suspend.**My xorg.conf is attached** for your review.

Thanx

Tishko

---

### Post by dspdude2000 on 2009-04-22
I have this same problem.  Wondering if there is either a way to make the configuration data in memory persistent across a suspend/resume or if there is a command that could be run on resume to reload the configuration data.

---

### Post by dspdude2000 on 2009-04-22
On another post, found this is a known bug.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/292861]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/292861")

But there doesn't appear to be a known solution.

---

