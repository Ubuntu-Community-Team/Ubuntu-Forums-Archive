---
title: "Use XRandR script to dynamically set monitor settings lightdm"
date: 2012-06-14
forum: Desktop Environments
---

### Post by camper365 on 2012-06-14
I have a laptop that I dock with an external monitor.  I keep the laptop display open, allowing me to use a dual monitor setup.  However, I often take my laptop on the go without my external monitor.  I've found that I can use XRandR to configure lightdm to set the appropriate monitor resolutions for the dual monitor setup, but when I take it out of the dock, this configuration causes lightdm to fail to start.  I can tell lightdm not to use XRandR to configure anything, and this works fine when it's out of the dock, but when it goes into the dock both monitors are clones and both have an incorrect resolution (1024x768 ).  Is there a way to conditionally execute the XRandR configuration based on whether the external monitor is present?
My laptop display is 1280x800 and my external is 1600x900.  I am running Xfce 4.8 and Ubuntu Studio 12.04.  I have a nVidia Quadro nvs 135m run off of the default nouveau and xorg that comes with a fully updated 12.04.  I am running the 3.2.0-23-lowlatency kernel.

---

### Post by camper365 on 2012-06-17
bump

---

### Post by gsker on 2012-10-31
I don't know how you got lightdm to do an xrandr configuration, but you could do what you want with a script.

Put 
XRANDRexternal="my customized xrandr command"
XRANDRnoexternal="my other xrandr command"
if xrandr | grep -q ' connected .*HDMI-0'
then
   ${XRANDRexternal}
else
   ${XRANDRnoexternal}
fi

in the display-setup-script

Tweak all that to match whatever xrandr spits out when your external monitor is connected/disconnected

[http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent](http://askubuntu.com/questions/63681/how-can-i-make-xrandr-customization-permanent)

Edit /etc/ligthdm/lightdm.conf

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
# for your login screen, e.g. LightDM (Ubuntu 11.10) or GDM (11.04 or earlier)
display-setup-script=/usr/share/mycustomloginvideo.sh
# for your desktop session
session-setup-script=/usr/share/mycustomdesktopvideo.sh

---

