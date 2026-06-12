---
title: "Network Manager Icon is Missing"
date: 2009-11-11
forum: Desktop Environments
---

### Post by footprint on 2009-11-11
I have a strange problem. 

The network icon is missing. If I remove the Notification Area from the panel and then add it again the icon is back. However, after a reboot it is missing again. Network Manager is running as shown by the fact that eth0, wlan0 and my mobile broadband dongle all work!

I hope someone has a solution. Thanks in advance.

---

### Post by Peter09 on 2009-11-12
I think its the indicator applet that you need to add to your start up.

Goto System->preferences->Startup Apps
and add an application with this spec.

```
sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py"
```

---

### Post by nigamp on 2009-11-12
Remove the Notification Area from the panel and then add it again..as u ve done b4 ... 
nct time the icon reappears ..rite click on it > select 'Lock to Panel' ....it ll remain der after reboot .... hpe dat helps... 


:KS

Ubuntu RULES !!!! :D

---

### Post by footprint on 2009-11-12
Thanks guys but it still vanishes after a restart. Think I'll try reinstalling a few packages around gnome.

- - - - - - - - - - - - 

Well! that didn't work so where do I go from here?

I don't realy want to resort to the M$ solution and reinstall, even though I have a separate /home partition.
It still takes quite a while putting all the extra programs back!

---

### Post by GoldNugget on 2009-11-14
I am having the same strange problem with the network manager icon on my eeepc 900. I have to remove the notification area and then replace it after every reboot. This is an odd bug that just started with Karmic. Its not that the notification area is not there, it just loads strangely with some icons duplicated (in my case, the sound icon) and others missing (network manager). 

I figure it will be fixed in some update soon and it is not a huge thing, but it is an annoying little bug.

---

### Post by footprint on 2009-11-16
In my case the problem appears to be solved.

I downloaded a new ISO image and reinstalled after backing up /home. Then copied back the backup to /home excluding the hidden files.

No problems since, guess my .iso was at fault.

---

### Post by SirWeazel on 2009-11-28
This issue occurs with me with multiple users. I have 2 user accounts, and whicheve account logs on first gets the network icon.

---

### Post by matt.cohenprice on 2009-12-19
this problem just started happening to me yesterday.

Have been running Karmic without many problems since it was released, and then yesterday, bam, no network manager icon. Sometimes there is a blank space where the icon should be, but yesterday I got a second battery icon instead. 

I checked startup applications and network manager is still there:
```
nm-applet --sm-disable
```

As others have suggested, removing and re-adding the notification area fixes the problem, at least for the current session. then, restart, same problem.

---

### Post by slamhound on 2009-12-19
Mine is intermittent.  Sometimes it shows up after boot, sometimes it doesn't. When it's not there, it's always replaced by some corrupted version of one of the other icons.  I can't detect any pattern.

---

### Post by erlguta on 2009-12-20
i have the same problem. Is there any solution?. Is any bug open in launchpad about this?

---

### Post by slamhound on 2009-12-21
Looks like this:  [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448?comments=all%27](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448?comments=all%27) 

Sounds like there are temporary workarounds, but I didn't see a solution.

---

### Post by blazyyo on 2010-01-03
I have similar problem. Using Ubuntu 9.10, with 3 user profiles.

NM icon shows for first user to login (and autoconnects to internet), NM icon does not show for other users. I tried removing/adding notification area icon, but it just shows a blank space in the taskbar.

---

### Post by Alejandro Nova on 2010-08-12
I've obtained good results with this:

$ sudo service network-manager stop
$ sudo service network-manager start

The Network Manager icon is there: it doesn't show anything, but it's there. These commands force the icon to update itself, and show on your Notification Area.

---

### Post by snydez on 2010-09-16
> **Alejandro Nova said:**
> I've obtained good results with this:

$ sudo service network-manager stop
$ sudo service network-manager start

The Network Manager icon is there: it doesn't show anything, but it's there. These commands force the icon to update itself, and show on your Notification Area.

well thanks for this.
it just need to disconnect it first then reconnect.

---

