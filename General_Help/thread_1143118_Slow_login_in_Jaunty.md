---
title: "Slow login in Jaunty"
date: 2009-04-29
forum: General Help
---

### Post by trpnblies7 on 2009-04-29
I had this same problem with Intrepid, and it doesn't seem to have changed in Jaunty. After the inital boot and usplash phases are complete, my cursor will appear on the desktop, but nothing happens for about 20 seconds. After that time, I'll finally hear the login sound and everything will load.

The hangup seems to be happening around here, where I'm getting this atk-bridge-WARNING:

```
Apr 29 16:38:48 brian-desktop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1d_7d_0c_39_3b
Apr 29 16:38:58 brian-desktop x-session-manager[3144]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup. 
Apr 29 16:38:58 brian-desktop x-session-manager[3144]: atk-bridge-WARNING: IOR not set. 
Apr 29 16:38:58 brian-desktop x-session-manager[3144]: atk-bridge-WARNING: Could not locate registry 
Apr 29 16:39:00 brian-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
```

I tried disabling the AT SPI Registry Wrapper under Startup Applications, but it didn't change anything (those warnings appeared before I had disabled it, too). Any ideas on how to fix this or what might be causing it? I've attached my bootchart, daemon.log, and part of my syslog for reference.

Thanks!

---

### Post by trpnblies7 on 2009-04-29
Anyone?

---

### Post by trpnblies7 on 2009-04-30
Any fix for this?

---

### Post by Crowchild on 2009-04-30
Same problem here.

---

### Post by trpnblies7 on 2009-04-30
At least I'm not the only one

---

### Post by trpnblies7 on 2009-05-01
Still nothing?

---

### Post by sam_delta on 2009-05-01
same, its taking too long to login,,, didnt happened to me i n 8.10 as far as i remember

sam

---

### Post by lensman3 on 2009-05-01
Your ethernet/network is not running.  Either the ethernet card is not being setup, or an IP number is not assigned (probably this one). 

On my system the Ethernet driver is initialized OK and the network stack is started, BUT no IP assigned.  If I start the network by hand at the text screen (run-level 3), and then start X11 using startx everything runs fast.  If I don't start the network using ifup, then it can hang for a couple of minutes.  

Hope this helps.

---

### Post by trpnblies7 on 2009-05-03
I use a wireless adapter, which doesn't connect to my network until after my desktop loads (which is after the hangup). Is there a way to have this occur earlier so I don't get this hangup?

---

### Post by sam_delta on 2009-05-03
well, i notice a lot of disk activity douring this hang time, so im not sure it has anything to do with the connection

Sam

---

### Post by trpnblies7 on 2009-05-03
When this happened in Intrepid, it turned out that Compiz was the problem. If I disabled Compiz on startup, there was no hang time. In Jaunty, though, disabling Compiz on startup doesn't make a difference, so I think it might be something else now.

---

### Post by trpnblies7 on 2009-05-05
Anyone else have an idea?

---

### Post by trpnblies7 on 2009-05-07
I was able to get rid of the atk-bridge-WARNING by setting /desktop/gnome/interface/accessibility to false. I'm still having the hang up on login, though, which is seeming to be network related. Any thoughts?

---

### Post by peekster on 2009-05-14
I have the same problem. Either 8.10 or 9.04.
My laptop powers up. I get to login ... then takes very long to give me a workable desktop where i can launch apps etc.

It goes a little faster with my laptop disconnected from any network ( wired or wireless ) but there isnt much progress.

It goes a little like this after the login:
Short burst of memory/disk usage 
2 minutes of idle memory/disk usage
Full use of memory/disk usage for about 1,5 minutes

Then its fully usable.

Hope somebody has a clue and/or solution.

---

### Post by fuzzyworbles on 2009-05-29
Same problem. from post to GDM takes 25 seconds, and from GDM to a useable UI takes 45 seconds. It makes no difference if I'm connect to a network or not. this is on an athlon x2 w/ 2gigs. I'll switch over to a virutal term and check running processes and report back.

i'd like to note, however, that a freshly created account starts in 5 seconds flat. I'm starting to think that there are some residual config files from older applications as i've upgraded through the years and have always kept the same /home partition.

---

