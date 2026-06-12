---
title: "xfdesktop-settings runs cpu to 100%"
date: 2012-05-12
forum: Desktop Environments
---

### Post by knarlomatic on 2012-05-12
Just intalled xubuntu onto a hp V2000 laptop.  All was working well until I tried to install mac4lin (dumb move I know :redface:).  Used the uninstall process for mac4lin and all seems to be working OK except when I go into Settings-Settings Manager-Desktop.  Now CPU pegs to 100%, no window appears for 2-3 minutes, after which I get a window labelled "Display", but all controls are missing, the associated text does not appear, just an otherwise blank window.  I'm not proficient enough to find the error log for this.  This also seems to kill conky, and I can't get it restarted.

The process name for this is xfdesktop-settings, and when I run this in terminal I get the following repeated six times in the terminal window:


(xfdesktop-settings:17840): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed


Behavior is similar, CPU gets pegged and window takes 2-3 minutes to come up, but I now get a fully functioning window, with all controls and text shown.

Tried installing XFCE 4.10, hoping whatever was wrong would be overwritten, but alas no joy.  XFCE is great by the way, it fixed a no background problem I had in conky, and adds some great new features.

My system is a hp v2000 variant laptop which has 2gb of ram and a AMD Sempron 2800+, Which has run Ubuntu 9 and 10 well and was running stock Xubuntu 12.04 nicely until I tried mac4lin. And I am an advanced M$ user, who is trying to love the Ubuntu line but finding little annoyances like this a roadblock to acceptance.  Thank goodness there is a great community for support!

Any help is appreciated....thanks in advance! :smile:

---

### Post by Peripheral Visionary on 2012-05-12
It sounds like mac4lin left some settings or stuff behind. Did you "just uninstall" or *completely remove* (as in purge) mac4lin? 

Open Synaptic Package Manager, find mac4lin (if it's listed, even if it doesn't show up as installed), right-click it and select *completely remove, including configuration files*. Click Apply.

Or open a terminal and type

```
sudo apt-get purge mac4lin
```

Or run **computer janitor** or **bleachbit** (as root) to rid your 'puter of the leftover orphaned config files from mac4lin. That might fix it all up for you! Then let us know, okay?

---

### Post by knarlomatic on 2012-05-13
Hey thanks a lot for the quick and thorough answer.  As of the first writing I had only tried the uninstall that came with the mac4lin package I downloaded at their site

I tried all you suggested.

1. Synaptic did not show mac4lin at all

2. apt-get solution returned the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mac4lin

I expect it found no uninstall file to direct it to the mac4lin leftovers

3. tried both computer janitor and bleachbit, and neither seems to have had an effect.  Great utilities to have tho!

Actually, maybe they did.  All behavior is the same as my original post after doing the above (followed by a reboot) EXCEPT that when I go to Settings-Settings Manager-Desktop I now no longer get a blank window labelled "desktop", I get a fully functioning window.  Still pegs the CPU, and takes about 2-3 minutes to appear.

Wish we could decipher this error message:

(xfdesktop-settings:17840): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

This may just be something I have to live with.  It's really not important in the scheme of things.  But I hate letting the computer beat me!  My little brother always told me I had to be at least 5% smarter than what I was working on....:(

---

