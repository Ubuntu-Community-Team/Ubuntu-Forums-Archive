---
title: "nautilus causing wireless trouble?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by DFreeze on 2005-07-04
Hello
 
If you've checked in the networking sub-forum you may have seen my [post](http://www.ubuntuforums.org/showthread.php?t=43328&highlight=%5Bwireless%5D) on wireless trouble. It's still in the process of being fixed. In my last post I was starting to suspect some other than my WiFi to cause the buggy connection (whether it be wireless or wired).

Here's the thing: my desktop is becoming irresponsive after a while when I start to use the system to some extent (few tabs in FireFox, email, etc.). The icons on my desktop sometimes dissappear, the icons in my taskbar are unaccessible, and /etc/init.d/gdm restart mostly doesnt work. I can login fine, but no GDM greeter after that, just a blank screen...

So could it be that something in my desktop is causing the trouble of network fallout, freezing icons? It's not the GDM thing, 'cause restarting that doesn't fix it. Can it be nautilus, or some other thing in /etc/init.d (don't know what that folder does yet). Just  to prove my point: right now I'm typing this using my wlan0... But tomorrow might be a whole different story. I mean: wireless didn't work the last time I shut the system down (or the 5 or 6 restarts before)... But today: no problems at all... 

Any of this sound familiar to you? Could you give me some hints?

---

### Post by tread on 2005-07-04
I doubt nautilus would cause problems .. but I don't *know* and therefore could be wrong.
Couple of things to check first:
1. Are you changing the wireless networks, so its working on one network and not on the other?
2. If point 1. is not relevant, then what sort of error do you get .. I mean what steps do you follow to connect to the network and which step fails?

---

### Post by DFreeze on 2005-07-05
Well, I'll try to make it into a sensible summation, so we might debug this...

I've had a lot of trouble even getting WiFi going. I could complete the steps that made other people get it done, except in my case nothing worked. 

I removed my ACX111 drivers as suggested by someone, and suddenly none of the connections worked anymore for a day or two (including reboots and full shutdowns).

Then WiFi worked the next day and I could access my mail and internet wirelessly. I didn't change anything, but it worked... But when I use the system too fanatically (I guess) by switching tabs, opening several terminals, GUI setup tools, FF-tabs, **and uploading stuff to my laptop **the desktop freaks out. (I can't get Samba or SWAT going, and Nautilus-share doesn't do anything too...well, one thing at a time).

I upload big files to the laptop (movie-files) to view later on. I have a network load window in my panel, and it suddenly drop from 90+% load to squat, and that's the end of the wireless connection. Period. This didn't happen to me when I could only use the wired NIC.No desktop functionality but at least it finished uploading my file...

I notice it first by clicking on one of my taskbar shortcut icons and seeing it being 'pressed' but not coming back to the 'unpressed' state (small difference but noticable).  The application bound to the shortcut isn't started. When I switch workspaces, my 'Computer', 'Home'  etc. icons are gone. I can't do anything useful with the desktop anymore and CTRL-ALT-F1, /etc/init.d/gdm restart is no good either. Only a full reboot gets the desktop back again (and sometimes the network).

I only noticed the possible connection between the two since the wireless is working to some extent. 

Can it be that something is messed up in my desktop; whatever program takes care of the icons and shortcuts? Or am I following a dead trail here?

Thanks for your ' brain-cycles' :) helping me figuring this out!

---

