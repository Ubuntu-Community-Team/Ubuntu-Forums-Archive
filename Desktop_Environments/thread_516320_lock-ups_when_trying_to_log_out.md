---
title: "lock-ups when trying to log out"
date: 2007-08-03
forum: Desktop Environments
---

### Post by lav-chan on 2007-08-03
Hi!

I have a really annoying problem in Ubuntu 7.04. I just installed this on a lap-top like a day or two ago, and so far i've been having fun with it... but there is one persistent error.

First of all, let me preface this by saying that as of right now i'm the only one who uses Ubuntu on this computer. Also i used to have shut-down/restart buttons in my System > Quit dialogue, but somehow i did something to make those go away. I think possibly this happened because i was messing around with the Users & Groups control panel -- i actually messed up a bunch of permissions trying to play with root stuff and had to re-add my account to the adm and admin groups in etc/group using the LiveCD -- but i'm not positive.

I did a search on the forum and people were suggesting changing something in the System > Preferences > Sessions thing, but i don't have the option they're talking about.

So anyway... since i don't know how to make those buttons come back, i just figured i would go to 'log out' and use the actions menu on the log-in screen (which is still available). This works some of the time, but more often than not the entire computer locks up when i go to log out. It makes the log-out noise, and then i get a black screen... and then that's all. Can't do Ctrl+Alt+F* to switch to a different session or whatever, can't do Ctrl+Alt+Delete, all i can do is shut it off with the power button.

Since i never really had a reason to log out before, i don't know how long this has been happening. The log-in screen does work fine after first starting up, though, it's just not when logging out.

Of course i do know how to shut the computer off without using the button, so that isn't really a life-or-death problem, but at some point i will want to actually log out of GNOME without having to completely restart.

I checked /var/log/syslog, but i'm not especially a Linux expert, so i guess i don't know what i'm looking for. This is what i have around the time i had to shut down last:

```
Aug  3 00:17:38 pingpong kernel: [10614.016000] wlan0: starting scan
Aug  3 00:17:40 pingpong kernel: [10615.380000] wlan0: scan completed
Aug  3 00:17:45 pingpong kernel: [10620.908000] NTFS volume version 3.1.
Aug  3 00:17:54 pingpong dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug  3 00:18:02 pingpong dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug  3 00:18:17 pingpong dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug  3 00:18:24 pingpong dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug  3 00:18:25 pingpong dhclient: No DHCPOFFERS received.
Aug  3 00:18:25 pingpong dhclient: No working leases in persistent database - sleeping.
Aug  3 00:19:19 pingpong gconfd (kine-5438): Exiting
Aug  3 00:19:19 pingpong kernel: [10715.044000] [fglrx:firegl_release_helper] unlocking blit buffer for this file...
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] total      GART = 130023424
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] free       GART = 114032640
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] max single GART = 114032640
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] total      LFB  = 134217728
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] free       LFB  = 119828480
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] max single LFB  = 119828480
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] total      Inv  = 0
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] free       Inv  = 0
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] max single Inv  = 0
Aug  3 00:19:20 pingpong kernel: [10715.836000] [fglrx] total      TIM  = 0
Aug  3 00:20:25 pingpong syslogd 1.4.1#20ubuntu4: restart.
Aug  3 00:20:26 pingpong kernel: Inspecting /boot/System.map-2.6.20-16-generic
Aug  3 00:20:26 pingpong kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Aug  3 00:20:26 pingpong kernel: Symbols match kernel version 2.6.20.
Aug  3 00:20:26 pingpong kernel: No module symbols loaded - kernel modules not enabled. 
Aug  3 00:20:26 pingpong kernel: [    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
```

Obviously from that you can tell what kernel i'm using. The Ubuntu version is 7.04 with everything the update manager thing wanted me to install (except some GIMP upgrade, which i don't care about). The desktop thing is GNOME, with Beryl/XGL.

Any help would be super rad, thanks!

---

