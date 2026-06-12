---
title: "Reset the display-settings?"
date: 2011-01-23
forum: Desktop Environments
---

### Post by RobbanC on 2011-01-23
Hi there

I have an old box, running Ubuntu 10.10. Mostly to be able to use internet and listen to music in my workshop...

Anyway. In the beginning this computer worked just fine. My Acer AL1912 was detected properly and screenresolution was automatically set to 1280x1024. When looking in system=settings=screens the monitor was detected as a Acer 1912. Nice!

For some reason I brought the computer over to another place and that other monitor (an Eizo) was also properly detected. Resolution changed automatically to 1912x1280.

Now, when I have moved the computer back, all monitor settings are completely lost and I can't seem to be able to change them. I am stuck on 1024x768 and the monitor is detected as "unknown". I have tried to change the values for resolutions in monitor.xml but the values revert to 1024x768 (which look quite fuzzy on my screen...)

So my short question is: Is there anyway to completely restore the monitor-/screen settings in Ubuntu 10.10 so it will autodetect my monitor properly again?

Thanks in advance!

---

### Post by Krytarik on 2011-01-23
I'm afraid, you have to set up your monitor using this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

But I did a short web search on "autodetect" and found this guide, it makes sense generaly, you may try it first, please give feedback on this:
[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

In either case, backup the file "/etc/X11/xorg.conf" before, if there is one.

---

### Post by RobbanC on 2011-01-29
Thanks alot, Krytarik

Unfortunately, none of the how-to.s in the links worked. :(

In the first, the wiki, I can do [FONT="Courier New"]--addmode[/FONT] and [FONT="Courier New"]--newmode[/FONT], but when I "apply" the settings with [FONT="Courier New"]--mode[/FONT], my screen flickers a bit and then becomes black. Also the computer stops responding completely. I had to pull the powercord here...

The command [FONT="Courier New"]sudo dpkg-reconfigure xserver-xorg[/FONT] simply does exacly nothing on my box. My prompt just comes back after a second or so.

I am quite curious were my kind-of default settings comes from. I try to delete and/or change [FONT="Courier New"]~/.config/monitors.xml[/FONT] but it keeps coming back with these stupid default values. I also don't have any [FONT="Courier New"]xorg.conf[/FONT] to play with.

I'm leaning towards to swipe the whole disk and do a fresh install. Somebody stop me! :twisted:

It just bothers me that the screen settings are so complicated...:confused:

---

### Post by Krytarik on 2011-01-29
In fact, the xserver tries to autodetect your monitor and its specs, if there is no xorg.conf. If it fails doing so, you end up like this. And it may not help at all just to re-install.

Try to set up a xorg.conf by following the guide I posted.

To get the correct monitor specs, see this current conversation:
[http://ubuntuforums.org/showthread.php?p=10407731#post10407731](http://ubuntuforums.org/showthread.php?p=10407731#post10407731)

---

### Post by RobbanC on 2011-02-06
Finally some time to fiddle with this...

Krytarik! Thanks!!

I copied most of the rows in the xorg.conf that you had put in the post you linked to. Now it works! For some reason I can also select a whole bunch of different resolutions from within system->settings->monitors. Anyway, my screen is now both bigger and sharp. 

My /etc/X11/xorg.conf now looks like this:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       30.0 - 107.0          # you have to enter your specific values here
    VertRefresh     48.0 - 120.0         # see guides below
    Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync Option
    "PreferredMode" "1280x1024_60.00"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "ati"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes    "1280x1024"       # set your preferred mode(s) here
    EndSubSection
EndSection

```

Thanks agin! ):P

(Still can't figure out why my monitor was automatically detected as an "Acer AL1912" before, but not anymore. That nifty feature disappeared in an apt-get upgrade I did a few months ago and after that, the screen was messed up. But nevermind...)

---

### Post by Krytarik on 2011-02-06
Glad that works now. However, I really advise to set your specific monitor specs in xorg.conf (those are mine), and your desired resolution/refresh rate (if you are not happy with those in place).

And for the autodetection thing, my monitor has been detected as Sony CPD-4401, but it actually is an Elsa Ecomo 530, but the specs has been detected correctly however, and that's all that counts.

---

### Post by johnycage on 2011-06-26
I'm having same problems. & no updates nor xorg.conf file is solving it. 

I have to create the file and copy the content you mentioned, still it's not working. 
Ubuntu version 11.04 updated fully. :(

---

