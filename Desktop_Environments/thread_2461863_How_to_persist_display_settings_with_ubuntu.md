---
title: "How to persist display settings with ubuntu?"
date: 2021-05-08
forum: Desktop Environments
---

### Post by peternoordzij1 on 2021-05-08
How to persist display settings with ubuntu?

**Setup:**
**3 monitors**

**Ubuntu 20.04.2 LTS**

**Display manager: gdm3**

**Window system: X11**

**Config: xrandr**


Every time the system is booted, the monitor setup is a mess. 
I have been reading a lot, for example:

[[https://wiki.ubuntu.com/X/Config/Resolution#statically_setup_in_xorg.conf]](https://wiki.ubuntu.com/X/Config/Resolution#statically_setup_in_xorg.conf])[1]

What works is applying manually:

    ~/.xprofile

Which has xrandr commands, such as:

    xrandr -- output DisplayPort - 1 -- primary -- mode 1920x1080 -- pos 1920 x 1080 -- rotate normal

But nothing is applied on boot or persists on reboot.

I have tried many things:


adding to

    /etc/X11/Xsession.d/45custom_xrandr_setting
    /etc/X11/Xsession.options

nothing


    ~/.xprofile
    ~/.xinitrc
    ~/.config/monitors.xml
    ~/.screenlayout/view1.sh

nothing


    sudo vim /etc/gdm3
    /etc/X11/Xsession.d/45custom_xrandr_setting
    /etc/X11/Xsession.options

nothing



    /etc/X11/xorg.conf
    /etc/X11/xinit/xinitrc
    /etc/X11/Xsession.d
    /etc/X11/Xsession.d/99x11-common_start
    /etc/X11/Xsession.d/45custom_xrandr_setting
    /etc/X11/Xsession.options

nothing

Please help!


  [1]: [http://%20How%20to%20persist%20display%20settings%20with%20ubuntu?%20%20Setup:%203%20monitors%20Ubuntu%2020.04.2%20LTS%20Display%20manager:%20gdm3%20Window%20system:%20X11%20Config:%20xrandr%20%20%20Every%20time%20the%20system%20is%20booted,%20the%20monitor%20setup%20is%20a%20mess.%20%20I%20have%20been%20reading%20a%20lot,%20for%20example:%20%20https://wiki.ubuntu.com/X/Config/Resolution#statically_setup_in_xorg.conf%20%20What%20works%20is%20applying%20manually:%20%20~/.xprofile%20%20Which%20has%20xrandr%20commands,%20such%20as:%20%20xrandr%20--%20output%20DisplayPort%20-%201%20--%20primary%20--%20mode%201920x1080%20--%20pos%201920%20x%201080%20--%20rotate%20normal%20%20But%20nothing%20is%20applied%20on%20boot%20or%20persists%20on%20reboot.%20%20I%20have%20tried%20many%20things:%20%20%20adding%20to%20%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20%20nothing%20%20#%20BEGIN_SRC%20sh%20~/.xprofile%20~/.xinitrc%20~/.config/monitors.xml%20~/.screenlayout/view1.sh%20#%20END_SRC%20nothing%20%20#%20BEGIN_SRC%20sh%20sudo%20vim%20/etc/gdm3%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20#%20END_SRC%20%20nothing%20%20%20#%20BEGIN_SRC%20sh%20/etc/X11/xorg.conf%20/etc/X11/xinit/xinitrc%20/etc/X11/Xsession.d%20/etc/X11/Xsession.d/99x11-common_start%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20#%20END_SRC%20%20nothing%20%20Please%20help](http://%20How%20to%20persist%20display%20settings%20with%20ubuntu?%20%20Setup:%203%20monitors%20Ubuntu%2020.04.2%20LTS%20Display%20manager:%20gdm3%20Window%20system:%20X11%20Config:%20xrandr%20%20%20Every%20time%20the%20system%20is%20booted,%20the%20monitor%20setup%20is%20a%20mess.%20%20I%20have%20been%20reading%20a%20lot,%20for%20example:%20%20https://wiki.ubuntu.com/X/Config/Resolution#statically_setup_in_xorg.conf%20%20What%20works%20is%20applying%20manually:%20%20~/.xprofile%20%20Which%20has%20xrandr%20commands,%20such%20as:%20%20xrandr%20--%20output%20DisplayPort%20-%201%20--%20primary%20--%20mode%201920x1080%20--%20pos%201920%20x%201080%20--%20rotate%20normal%20%20But%20nothing%20is%20applied%20on%20boot%20or%20persists%20on%20reboot.%20%20I%20have%20tried%20many%20things:%20%20%20adding%20to%20%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20%20nothing%20%20#%20BEGIN_SRC%20sh%20~/.xprofile%20~/.xinitrc%20~/.config/monitors.xml%20~/.screenlayout/view1.sh%20#%20END_SRC%20nothing%20%20#%20BEGIN_SRC%20sh%20sudo%20vim%20/etc/gdm3%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20#%20END_SRC%20%20nothing%20%20%20#%20BEGIN_SRC%20sh%20/etc/X11/xorg.conf%20/etc/X11/xinit/xinitrc%20/etc/X11/Xsession.d%20/etc/X11/Xsession.d/99x11-common_start%20/etc/X11/Xsession.d/45custom_xrandr_setting%20/etc/X11/Xsession.options%20#%20END_SRC%20%20nothing%20%20Please%20help)!

---

### Post by him610 on 2021-05-08
xfce4-settings
[https://docs.xfce.org/xfce/xfce4-settings/4.14/display]("https://docs.xfce.org/xfce/xfce4-settings/4.14/display")

---

