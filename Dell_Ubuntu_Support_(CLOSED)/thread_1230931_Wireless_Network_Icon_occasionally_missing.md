---
title: "Wireless Network Icon occasionally missing"
date: 2009-08-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by misterfuss on 2009-08-03
Hello,
I got my Dell Mini 9 with Ubuntu in February and had no prior Ubuntu experience.  Occasionally when I power up my computer, the wireless network icon is missing.  When I go to System > Administration > Network Manager or Network Settings, nothing happens.  I can't connect to a wireless network when I don't see the icon.

I have been restarting the computer when the icon is missing and usually the next time the computer starts, the icon has reappeared.  When the icon is visible, I can connect to wireless networks, but it is annoying to have to restart the computer to make this happen.

I am current on updates (or at least the Update Manager indicates that.)  Any suggestions to fix this problem would be appreciated.  Thanks.

---

### Post by mikewhatever on 2009-08-05
You either miss the notification area or the so called nm-applet when that happens. I don't know the reasons, nor how to fix it, but you most probably don't need to reboot. Try pressing alt+f2 and typing nm-applet. This should start the applet and let you connect.

---

### Post by ugm6hr on 2009-08-05
That was an intermittent problem I had with the Ubuntu version on the Mini 9 I suffered from too.

I installed 9.04, and have not had any problems since.

As mentioned, when it happens it is worth trying:
Alt+F2
**nm-applet --sm-disable**

Although, from memory, I think the problem wasn't that Network Manager didn't start, but that it didn't load the wifi driver correctly.

Honestly, I would advocate installing the 9.04 Netbook Remix.

---

### Post by misterfuss on 2009-08-09
Thanks for the suggestions.  I will try it when it happens again

---

### Post by traynor on 2009-10-31
I'm on an HP with Ubuntu 9.0.4. Running fine all the time.

Recently (last week or so) I've noticed the wifi connection disappears from the top notifications bar.

When I run nm-applet --sm-disable I get this:

:~$ nm-applet --sm-disable

** (nm-applet:20289): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

I'm using the wifi network right now to make this post - I just can't see the signal strength bars up there on the panel unless I reboot, but then they'll disappear again.

Any idea what's up here?

thanks

---

### Post by ugm6hr on 2009-10-31
Do any of the other system tray icons disappear as well?

I use 9.04 with Xfce, and have had no problems at all.

---

### Post by traynor on 2009-10-31
> **ugm6hr said:**
> Do any of the other system tray icons disappear as well?

I use 9.04 with Xfce, and have had no problems at all.

Only the wifi icon disappears. The volume icon remains, and so does the clock. There's just a blank space where the wifi icon used to be. Any idea?

---

### Post by ugm6hr on 2009-11-01
> **traynor said:**
> Only the wifi icon disappears. The volume icon remains, and so does the clock. There's just a blank space where the wifi icon used to be. Any idea?

Afraid not.

Sounds like a bug in nm-applet, but I've not encountered it,and have no idea what is happening.

---

### Post by lswartz on 2009-11-01
I thought I was the only one this was happening to. I just restart my Mini 9. The worst it ever was took 6 restarts but that has been 2 months ago. Normally it boots it up on the 2d time.

I'm looking hard at 9.10 as it installed flawlessly on my desktop & old laptop. My son put it on his Mini 10 yesterday & only needed to add the broadcom driver (& Ubuntu did that for him). I just haven't decide whether to get 9.10 or the netbook 9.10 remix.

---

### Post by ugm6hr on 2009-11-01
> **lswartz said:**
> I thought I was the only one this was happening to. 

Traynor's issue is slightly different.  An icon exists at login, but subsequently disappears.

Actually, in view of that, it is perhaps worthwhile starting a new thread...

---

### Post by misterfuss on 2009-11-02
> **misterfuss said:**
> Thanks for the suggestions.  I will try it when it happens again


I have typed **nm-applet --sm-disable** each time the icon has not appeared and it has solved the problem.  Thanks.

---

### Post by lswartz on 2009-11-02
That is good to know, I'll try the same thing the next time my wireless doesn't boot up. I hope it works for me too.

---

### Post by lswartz on 2009-11-03
> **misterfuss said:**
> I have typed **nm-applet --sm-disable** each time the icon has not appeared and it has solved the problem.  Thanks.

This worked for me tonight as well. Thanks. I found that I had to leave the terminal open as when I closed it, my wireless closed too.

---

### Post by ugm6hr on 2009-11-06
> **lswartz said:**
> This worked for me tonight as well. Thanks. I found that I had to leave the terminal open as when I closed it, my wireless closed too.

Use Alt+F2 and type it there.

Or try nohup command &:
```
nohup nm-applet --sm-disable &
exit
```

---

### Post by panzet on 2010-02-14
I tried to execute nm-applet (alt+F2, etc.), but there still is no network manager icon on my notification area.
I have internet connection, but... if I quit the notification area of my panel (where it's supposed to be the nm-applet), and put it again ("add to panel > notification area"), the applet appears!!.
Again, when i shut down and start my computer, the nm applet disappears again...
I hope it could helps... and I hope that you could understand my english...
I am running karmic (9.10) 64 bit on a sony laptop, not a netbook, but with the same problem...

---

### Post by traynor on 2010-02-15
Panzet - that is the exact same experience I have.

A lot of times the network manager icon is not present after booting up (sometimes there are 2 volume control icons instead).

So I right-click and remove from panel, then add to panel the notification area, and viola! There's the network manager icon.

Strange bug, but easy enough to workaround I suppose.

(I tried starding the nmapp exercise but it always said it was already running).

Someone should report this bug to Ubuntu...

---

### Post by ASHIE on 2010-03-10
[FONT="Arial"]I'm experiencing the same problem. It's only the network icon that disappears. sometimes it's blank, other times it duplicates my volume or bluetooth icons, but when I right click on it, nothing happens. when I delete the notification area and add it again then the icon appears, but only till I restart my PC. I use bluetooth internet connection with my mobile using bluetooth manager. I've edited my network connections to autostart my mobile broadband when I connect my phone. so when I connect via bluetooth, my network starts & the icon appears. I've worked around it, but it's an annoying bug. My UNR installation doesn't seem to have this problem though.[/FONT]

---

### Post by lz1dsb on 2010-03-12
Interesting I've run on the problem that [traynor]("http://ubuntuforums.org/member.php?u=80296") talks about. And indeed my connection is not interrupted, it's just the icon that is gone. But this happen only two or three times. I was able to mange though, stopping and starting the nm-applet from the cli...

Cheers, 
Boyan

---

### Post by caro on 2010-03-12
> **ASHIE said:**
> [FONT="Arial"]I'm experiencing the same problem. It's only the network icon that disappears. sometimes it's blank, other times it duplicates my volume or bluetooth icons, but when I right click on it, nothing happens. when I delete the notification area and add it again then the icon appears, but only till I restart my PC. I use bluetooth internet connection with my mobile using bluetooth manager. I've edited my network connections to autostart my mobile broadband when I connect my phone. so when I connect via bluetooth, my network starts & the icon appears. I've worked around it, but it's an annoying bug. My UNR installation doesn't seem to have this problem though.[/FONT]

I'm seeing the same thing.  For the past week or so, sometimes my wireless network icon is replaced by a second volume icon.  Everything else works and when I reboot or delete and re-add the notification area things usually return to normal.

---

### Post by edwardtilbury on 2010-03-24
I tried running the "steal systray icons" from the Cairo Dock program... That was a mistake...

My wireless icon appeared to the left , directly underneath the top menu bar! 

I could move it... 

Now a reboot later and it's missing again... I tried moving the main menu bar all around.. messing with the size etc... I wish I could undo the "steal icon" function, but there's no option for that in Cairo Dock... 

Any idea how to fix this?

---

### Post by fabounet on 2010-03-25
you can place the systray widget anywhere on your desktop, just drag it with ALT+mouse

---

### Post by ASHIE on 2010-03-31
It seems my missing network icon is no longer a problem. it seems that when I place items on the panel too close either side of the system tray my network icon disappears on startup. I've spaced things a lil further apart and so far it seems to be ok :)

---

### Post by ebodnaruk on 2011-02-20
I have this problem too, on Ubuntu 10.4 LTS.  I have a Dell Inspiron laptop.  The difference is that the icon with the signal strength (where I can choose which network I want to connect to) is NEVER there.  It still automatically connects to my home network, and previously used networks are still logged in the Network Manager section.  It just stinks that I can't connect to a network of my choice and I don't know if it will automatically connect to a new network if I go to a coffee shop or something.  Probably not.  

Wish someone knew how to fix this!

---

