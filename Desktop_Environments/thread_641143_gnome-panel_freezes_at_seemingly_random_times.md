---
title: "gnome-panel freezes at seemingly random times"
date: 2007-12-15
forum: Desktop Environments
---

### Post by ibnbattuta on 2007-12-15
Hi all, 

My gnome-panel freezes at seemingly random times. When this probablem kicks in, it seems the system goes into a gradual (dozens of minutes) decline. 

Frequently, but not always, the freeze may be cured with a simple 

$killall -HUP gnome-panel

but after a while that doesn't work anymore (the killall makes the gnome-panel go away and come back, but the panel doesn't come back properly - it is often smaller in size and blank). 

When this latter effect takes place I have other problems as well. Processes already running seems to work ok, but I cannot start new processes that require a window/widget. Furthermore, a 

$sudo -i 

just hangs and a similar  

$sudo reboot  

also just hangs. 

This even from a bash shell through ctrl-alt-f2 or similar. 

I see there are quite a number of posts (e.g. [http://ubuntuforums.org/archive/index.php/t-356398.html](http://ubuntuforums.org/archive/index.php/t-356398.html), [http://ubuntuforums.org/archive/index.php/t-52558.html](http://ubuntuforums.org/archive/index.php/t-52558.html), [http://ubuntuforums.org/showthread.php?t=635248](http://ubuntuforums.org/showthread.php?t=635248)) regarding gnome-panel freezes, but I find none that solves my problem. I find nothing in /var/log/messages that seems to indicate unusual things. 

I run a fully updated gutsy gibbon (2.6.22-14-generic kernel) on a dell inspiron d830 laptop with intel core 2 duo T7300 2GHz cpu and an nvidia Quadro NVS 140 graphics card. 

Does anyone have any good ideas? 

Is there a gnome/gnome-panel log somewhere I might check?

---

