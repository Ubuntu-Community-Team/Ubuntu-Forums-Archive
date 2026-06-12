---
title: "Not the typical 100% CPU usage"
date: 2009-04-28
forum: General Help
---

### Post by acastiello on 2009-04-28
Hi out there!

I'm relatively new to Linux and Ubuntu but not for computers. I installed Ubuntu 8.10 a few months ago and then updated to 9.04 (via the update manager). "Something" is eating the CPU and I say something because the system monitor does not show any process using such 100% but the CPU is indeed. top also shows no culprit:
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2921 root      20   0  109m  45m  11m R 18.6  7.7   5:05.72 Xorg               
 3856 alvaro    20   0 32000  14m  10m R 14.3  2.4   3:22.15 gnome-system-mo    
 3496 alvaro    20   0 26988 3156 2388 S  4.0  0.5   0:51.55 x-session-manag    
13277 alvaro    20   0     0    0    0 R  4.0  0.0   0:00.12 vino-server        
 3616 alvaro    20   0  8124 3224 1928 S  3.0  0.5   0:44.27 gconfd-2           
 3608 alvaro    20   0  5860 3832  624 S  2.7  0.6   1:06.39 dbus-daemon        
 3675 alvaro    20   0 30688  13m  10m S  1.7  2.3   0:10.66 vino-server        
 3682 alvaro    20   0 28340 5364 4620 S  1.3  0.9   0:14.43 python             
 3645 alvaro    20   0 30372 3444 2580 S  1.0  0.6   0:17.48 gnome-settings-    
 3808 alvaro    20   0 17176 3976 3176 S  1.0  0.7   0:15.16 gnome-screensav    
 3692 alvaro    20   0 25812 2940 2080 S  0.7  0.5   0:05.74 gnome-power-man    
 3757 alvaro    20   0 23320 5264 3256 S  0.7  0.9   0:27.05 indicator-apple    
13207 alvaro    20   0  2448 1184  912 R  0.7  0.2   0:00.11 top                
 2853 root      20   0  5180 1184 1096 S  0.3  0.2   0:00.19 hald-addon-stor    
 3651 alvaro    20   0 21296 8740 6544 S  0.3  1.4   0:09.93 metacity           
 3652 alvaro    20   0 43612  11m 8096 S  0.3  1.9   0:25.60 gnome-panel        
 3660 alvaro    39  19 36964 9188 3540 S  0.3  1.5   0:08.02 trackerd  

I looked everywhere and the classic culprits Xorg and firefox doesn't seem to be the ones here. My machine is a relative old one: P4 1.8 GHz with 512 MB (128 added yesterday) and ran smoothly until updated. I don't know if I'm missunderstanding top, but if I sum the CPU usages they don't come up with the 100%. Gee!, maybe not even 30%. Any ideas?

Regards,
Alvaro Castiello

---

### Post by acastiello on 2009-04-28
Oh!, forgot to tell: CPU usage remains 100% most of the time "dropping" to 98 or 99 shortly

---

### Post by soro2005 on 2009-04-28
Your graphics card may not be configured correctly. For a start, you could try to make sure that you are using the correct driver (System --> Administration --> Hardware Drivers)

---

### Post by acastiello on 2009-04-28
> **soro2005 said:**
> Your graphics card may not be configured correctly. For a start, you could try to make sure that you are using the correct driver (System --> Administration --> Hardware Drivers)

Hi Soro,

I have no single driver installed and it was running fine before the updating. Anyway, I tried the solutions found for xorg.conf with no success, but I recently discovered something: when I shutdown the machine, and "unkwnown" process is nonresponsive. I discovered that such process is the update-notifier. Killing it restores the machine to normal operation, but I guess this is just an easy (and faked) way to solve the issue. Maybe something deeper is happening. Any idea?

regards,
Alvaro Castiello

---

### Post by acastiello on 2009-04-28
> **soro2005 said:**
> Your graphics card may not be configured correctly. For a start, you could try to make sure that you are using the correct driver (System --> Administration --> Hardware Drivers)

...and by the way Soro, how can I configure a driver for my card (if there is any)?, how do I look for it?

Thanks in advance,
Alvaro Castiello

---

### Post by soro2005 on 2009-04-28
It depends on what graphics card you have. Just saying, you may start by checking whether it looks fine in the restricted drivers interface. If there's nothing to be seen there, then you could provide the relevant info. If you don't know and it's not written across the case, then you could open a terminal window, enter
```
lspci
```
and post the output here.

I suspect it's the graphics driver b/c in your top, it says that Xorg is consuming some processing power. Xorg is the graphics server. You say it's not, but according to what you've posted above, it is. If not the system monitor, but I assume you have the same problem when you close the system monitor window.

*Edit*
Oh, wait. The update notifier is the problem. Just seeing that you'd posted two posts. You could try:
```
sudo apt-get install --reinstall update-notifier
```
Or you can try whether the problem does not occur if you prevent it from starting with the gnome session. In System -- Preferences -- Startup Applications. It's just that friggin notification which doesn't ever notify of anything anyway since the new notification system.

Also, open synaptic and make sure that you can reload the sources list, etc.

---

### Post by acastiello on 2009-04-28
First of all, thank you for your time and patience

Here is the situation:
a) the update notifier has nothing to do. It seems that killing it in a one session restored the machine, but it has no effect in further ones
b) My xorg config file is very simple:
ection "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
c) It all started when upgrading from 8.10 to 9.04
d) If I boot and test with the 9.04 CD everything runs fine, with about 30-40% cpu usage (xorg still may have some impact)
e) When booted, the machine shows nearly 0% cpu usage and it begins to raise to 100%. It reaches it in about 30 seconds. Once reached, it never drops below 99%. Even clicking in a menu is painfully slow :confused:
f) My video card is "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"

I don't know if it has something to do the RAM added: I added 128 MB to the existing 512. The swap partition is 1.3 GB

Again, thank you
Alvaro Castiello

---

### Post by soro2005 on 2009-04-28
But if killing the update notifier stops the racing, and the next time you start your Gnome session it starts racing again until you kill the update notifier again, then that means that what is racing is the update notifier or some process initiated by it. Or am I getting something wrong here?

The RAM doesn't have to do with it. If anything, a *lack* of RAM would lead to a lot of thrashing on the *hard drive*. There's no way that the added RAM leads to a high CPU usage. The swap is enough. I doubt your machine uses it at all.

Your Xorg is ok, and it's not really used anymore anyway as far as I understand. Your graphics card is supported by the driver that comes with the distribution. I don't know whether there's also a proprietary one, but I think you should be fine there as well.

30-40% CPU load is a lot. I consider that racing. But I also have a rather potent little bugger sitting here. In any case, 100% is a different story.

Let's assume it has to do with the update notifier. I'm not finding any bugs in launchpad. Perhaps there's something fishy going on related to system updates on your machine.

Did the distro upgrade go smoothly? Or did it abort? What happens if you enter
```
sudo apt-get update && sudo apt-get dist-upgrade
```
into a terminal? Of course after you've shot down the misbehaving app.

Instead of killing the update-notifier, can you kill gnome-panel? What happens?

Do you have tracker installed? Any related errors? I think some people, including me, had some race condition related to tracker after upgrading to Jaunty.

*Edit*
And by the way: To kill the update notifier, open a terminal and enter
```
killall update-notifier
```
if it still races
```
killall -9 update-notifier
```
If that stops it, then you know who's to blame. Just in case.

---

### Post by acastiello on 2009-04-29
> **soro2005 said:**
> But if killing the update notifier stops the racing, and the next time you start your Gnome session it starts racing again until you kill the update notifier again, then that means that what is racing is the update notifier or some process initiated by it. Or am I getting something wrong here?

Soro, my guess is that the update notifier has nothing to do with it. I killed once and the cpu dropped, but just once. I been unable to drop the cpu again by any mean. So, killing update notifier and getting the cpu dropped was as we say in mexico, a "chiripa"

[QUOTE=Let's assume it has to do with the update notifier. I'm not finding any bugs in launchpad. Perhaps there's something fishy going on related to system updates on your machine.[/QUOTE]

update notifier is sleeping (even snoring) all the time

[/QUOTE]Did the distro upgrade go smoothly? Or did it abort? What happens if you enter
```
sudo apt-get update && sudo apt-get dist-upgrade
```
into a terminal? Of course after you've shot down the misbehaving app.[/QUOTE]

Very interesting question Soro. The update did not wen smoothly. It hang waiting for a file or kind of, but although the machine was responsive, the update process was waiting for something. I cancelled it and later, when retried, it showed that a "partial update was first necessary" which I did. Checking the status says that the machine is completely update. I ran:

sudo apt-get update:

and began downloadin files and flagged a couple of errors:
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible) -> could not block * (11 Resource temporarily unavailable)
E: Imposible bloquear el directorio de administración (/var/lib/dpkg/), ¿está otro proceso usándolo? -> Unable to block the administration directory, is other process using it?

sudo apt-get dist-upgrade flags same error

I "sudoed" /var/lib/dpkg/ and renamed the old lock file and ran the commands again. They ran fine, I rebooted and the cpu remained at 100% :(


[QUOTE=Instead of killing the update-notifier, can you kill gnome-panel? What happens?[/QUOTE]

gnome-panel was sleeping. Killing it showed no change in cpu and inmediatly was relaunched

[QUOTE=Do you have tracker installed? Any related errors? I think some people, including me, had some race condition related to tracker after upgrading to Jaunty.[/QUOTE]

I have it installed, but although it appears (trackerd and tracker-applet both sleeping) in the system monitor, stopping (not killing) shows no effect in cpu usage

*Edit*
And by the way: To kill the update notifier, open a terminal and enter
```
killall update-notifier
```
if it still races
```
killall -9 update-notifier
```
If that stops it, then you know who's to blame. Just in case.[/QUOTE]

No results :(. The behaviour remains the same: fater boot, the cpu raises from practically 0% to 100% in about 20 seconds and stays there. If I use the CD to test, the cpu load is about 40%

Thanks you again. You're and Ubuntu old wolf
Alvaro Castiello

---

### Post by acastiello on 2009-04-29
One detail Soro (maybe I will need a fresh reinstall), after running
sudo apt-get update
sudo apt-get dist-upgrade
when I remote connect (I use ultravnc from many PCs) it causes ultravnc to hang in windows. Before that, ultravnc could be connected for days :(

If I reinstall from the CD will it install leaving what is already installed or it will start from scratch?

Regards,
Alvaro Castiello

---

### Post by soro2005 on 2009-04-29
Hmmmmm. Can you post a screen of your "top" again, this time without opening the gnome-system-monitor? Can't be that difficult to find out what exactly is causing the cpu load.

Another likely culprit is pulseaudio. Perhaps you could try killing that one as well and report back what happens. For good measure, kill esd as well. Should not even be installed, but if you have upgraded since gutsy or hardy, it might be there as a residue and interfere with pulse.

With regard to the upgrade, do the following: *Before* loging into your gnome session, hit <alt> + <ctr> + <f3> all at the same time, log into a terminal, and alternate sudo apt-get update and sudo apt-get dist-upgrade until you're sure that there's nothing more to be upgraded. This is if you have a wired connection, if you're on wireless, you may have to log into gnome to get the connection, but then log out again.

If you have your home directory on a separate partition, then you can normally salvage your configurations and install the binary afresh. The problem: one of the configuration files might precisely be what causes the hang up.

But I think that this is way too early to recommend a fresh install. I suspect that the problem is quite trivial once we've pinned it down.

Also: Try to create a new user, and log in as that user. Same problem?

I hope that you and your people are safe!

---

### Post by NFblaze on 2009-04-29
Have you installed any restricted drivers for your graphics card.

I've had problems with graphics 3 times...

8.04 wouldnt recognize my correct graphic settings and would display at a lower resolution than normal.... tho i never had any cpu problems...so try your computer at a lower resolution to see if it gets rid of it.

8.10 after upgrading the cpu would lock up at 100% and the OS would crawl by.... but after I updated and downloaded the drivers for my card, and enabled it; it instantly cleared up.

9.04 upgrade did the exact same thing, because for some retarded reason the installer removes the drivers and then doesent replace them... so I had another system crawl and cpu usage. Though, again I had to download the restricted drivers and enable them...and the CPU instantly was done.

Tho yea..why the hell does it remove the graphic drivers and then not re-install them I wish i knew....especially if you dont have an internet connection to redownload them every upgrade.

---

### Post by soro2005 on 2009-04-29
To my knowledge, there is no restricted driver for his graphics card.

But try
```
sudo dpkg --configure -a
```
again ideally from outside the Gnome session (log out, <alt> + <ctr> + <f3>).

---

### Post by acastiello on 2009-04-30
> **soro2005 said:**
> Hmmmmm. Can you post a screen of your "top" again, this time without opening the gnome-system-monitor? Can't be that difficult to find out what exactly is causing the cpu load.

Here is a top of the problematic user (me, no monitor):
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9187 alvaro    20   0  4112 2360  652 S  6.2  0.4   0:07.46 dbus-daemon        
 9093 root      20   0 64952  20m 8024 S  5.6  3.5   0:23.56 Xorg               
 9128 alvaro    20   0 26980 7524 5892 S  3.8  1.2   0:05.77 x-session-manag    
 9196 alvaro    20   0  8168 4780 2256 R  3.6  0.8   0:05.38 gconfd-2           
10059 alvaro    20   0 23080 7744 6220 R  2.2  1.3   0:00.11 vino-server        
 9225 alvaro    20   0 30372 9776 6892 S  1.6  1.6   0:02.90 gnome-settings-    
 9252 alvaro    20   0 33884  13m 9800 S  1.4  2.3   0:02.47 gnome-terminal     
 9258 alvaro    20   0 28336  14m 8240 S  1.4  2.4   0:02.04 python             
 9398 alvaro    20   0 17048 2664 1420 S  1.4  0.4   0:02.52 gnome-screensav    
 9311 alvaro    39  19 36340  31m 2716 R  1.2  5.4   0:01.92 apt-check          
 9242 alvaro    20   0 23372  11m 8364 S  1.0  1.9   0:01.34 nm-applet          
 9340 alvaro    20   0 23180 9568 7648 S  1.0  1.6   0:02.68 indicator-apple    
 2729 root      20   0  5204 1976 1744 S  0.8  0.3   0:01.79 hald-addon-inpu    
 9280 alvaro    39  19 28724  11m 4992 S  0.8  1.9   0:01.01 tracker-indexer    
 9232 alvaro    20   0 60292  26m  16m S  0.4  4.4   0:08.04 gnome-panel        
 9249 alvaro    20   0 19484 7404 6048 S  0.4  1.2   0:00.57 tracker-applet     
 9268 alvaro    20   0 25808 9348 6464 S  0.4  1.5   0:00.88 gnome-power-man    


and as you suggested, I create a new user. No problem with him: (also, no monitor)

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                   
 8528 root      20   0 63808  19m 7852 S  3.7  3.2   0:25.33 Xorg                      
 9015 prueba    20   0 34548  14m 9852 R  3.0  2.5   0:01.68 gnome-terminal            
 9036 prueba    20   0  2448 1184  912 R  0.7  0.2   0:00.32 top                       
 2788 root      20   0  5180 1804 1592 S  0.3  0.3   0:00.17 hald-addon-stor           
 8972 prueba    20   0 17020 2664 1412 S  0.3  0.4   0:00.83 gnome-screensav           
    1 root      20   0  3084 1952  632 S  0.0  0.3   0:01.72 init                      
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                  
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0               
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.28 ksoftirqd/0               
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 events/0                  
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                   
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                   
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0             
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0                 
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                    
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify              
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                    
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 ata/0                     
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                   
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd             
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.09 khubd                     
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                   
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                     
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                 


> **soro2005 said:**
> Another likely culprit is pulseaudio. Perhaps you could try killing that one as well and report back what happens. For good measure, kill esd as well. Should not even be installed, but if you have upgraded since gutsy or hardy, it might be there as a residue and interfere with pulse.

No effect killing pulseaudio and esd was not present. And BTW the audio is gone! (in all users):(

> **soro2005 said:**
> With regard to the upgrade, do the following: *Before* loging into your gnome session, hit <alt> + <ctr> + <f3> all at the same time, log into a terminal, and alternate sudo apt-get update and sudo apt-get dist-upgrade until you're sure that there's nothing more to be upgraded. This is if you have a wired connection, if you're on wireless, you may have to log into gnome to get the connection, but then log out again.

Done. No updates are pending.

If you have your home directory on a separate partition, then you can normally salvage your configurations and install the binary afresh. The problem: one of the configuration files might precisely be what causes the hang up.

But I think that this is way too early to recommend a fresh install. I suspect that the problem is quite trivial once we've pinned it down.

> **soro2005 said:**
> Also: Try to create a new user, and log in as that user. Same problem?

No. The new user run with about 17-30% cpu load (maybe Xor still has something to do with it or the monitor itself)

> **soro2005 said:**
> I hope that you and your people are safe!

Thank you a lot my friend. They are indeed. More and more people here regards that although delicate, the goverment is exagerating and overreacting to the situation and something more is behind the problem. Again, we are taking precautions but with a ? floating over the capital

I noticed that everytime the monitor starts, the CPU raises from 90% to 100%, so the monitor itselfs is consuming a lot of CPU

---

### Post by acastiello on 2009-04-30
> **NFblaze said:**
> Have you installed any restricted drivers for your graphics card.

I've had problems with graphics 3 times...

8.04 wouldnt recognize my correct graphic settings and would display at a lower resolution than normal.... tho i never had any cpu problems...so try your computer at a lower resolution to see if it gets rid of it.

8.10 after upgrading the cpu would lock up at 100% and the OS would crawl by.... but after I updated and downloaded the drivers for my card, and enabled it; it instantly cleared up.

9.04 upgrade did the exact same thing, because for some retarded reason the installer removes the drivers and then doesent replace them... so I had another system crawl and cpu usage. Though, again I had to download the restricted drivers and enable them...and the CPU instantly was done.

Tho yea..why the hell does it remove the graphic drivers and then not re-install them I wish i knew....especially if you dont have an internet connection to redownload them every upgrade.

Hi NFblaze, what grpahic card do you have and where are the drivers stored (newbby question :)). I have a backup of the system before upgrading

Regards,
Alvaro Castiello

---

### Post by acastiello on 2009-04-30
> **soro2005 said:**
> To my knowledge, there is no restricted driver for his graphics card.

But try
```
sudo dpkg --configure -a
```
again ideally from outside the Gnome session (log out, <alt> + <ctr> + <f3>).

I did and "nothing" happened. I just typed the command and the command line returned to the.... (what is the Linux equivalent of the DOS prompt?)

Regards,
Alvaro Castiello

---

### Post by ladydeth666 on 2009-04-30
I am having the same issue as most of you.  I have a BFG 8500GTS that I reverted to a 173 driver from the newer 180.  The 180 driver caused it to get up to 74C in temp, and have random issues with the display.  I used jaunty's hardware driver gui to change to the 173, and uninstalled the 180 from with the clean up tool.

I dont believe the video is causing the problem.  Im using a dual core amd 5400+, and it pegs one cpu and then the other.  Last night was the first night the performance got so bad it effected the scrolling of firefox and a terminal window.  I shut off all the fluff (compiz, bluetooth, cups, etc) with no change.  I closed firefox, no change.  Rebooted, no change.  The memory (4g reporting 3.2g) and page file (6g) are very low, only going up when a program is opened, and dropping back down.  Gnome-manager was the only process in the gui that was using the cpu, showing a steady 6%.

There was a pulseaudio update within the last couple of days, and Ive had issues with it before.

Another user posted that he was having issues with firefox and java.  He said the processes stayed pegged at 99% cpu usage even after closing firefox.  The processes would go away with the kill command, but would come back when firefox was restarted.

Any ideas?

---

### Post by acastiello on 2009-04-30
> **ladydeth666 said:**
> I am having the same issue as most of you.  I have a BFG 8500GTS that I reverted to a 173 driver from the newer 180.  The 180 driver caused it to get up to 74C in temp, and have random issues with the display.  I used jaunty's hardware driver gui to change to the 173, and uninstalled the 180 from with the clean up tool.

I dont believe the video is causing the problem.  Im using a dual core amd 5400+, and it pegs one cpu and then the other.  Last night was the first night the performance got so bad it effected the scrolling of firefox and a terminal window.  I shut off all the fluff (compiz, bluetooth, cups, etc) with no change.  I closed firefox, no change.  Rebooted, no change.  The memory (4g reporting 3.2g) and page file (6g) are very low, only going up when a program is opened, and dropping back down.  Gnome-manager was the only process in the gui that was using the cpu, showing a steady 6%.

There was a pulseaudio update within the last couple of days, and Ive had issues with it before.

Another user posted that he was having issues with firefox and java.  He said the processes stayed pegged at 99% cpu usage even after closing firefox.  The processes would go away with the kill command, but would come back when firefox was restarted.

Any ideas?

Hi ladydeth666, did your audio did also dissapear?

Regards,
Alvaro Castiello

---

### Post by acastiello on 2009-04-30
BTW Soro. I no longer check with the monitor but with top. I learned that when the screen is relatively static, Xorg uses little cpu. As soon as I display anything (a single simple window) it raises considerably. Maybe a configuration is required

Regards,
Alvaro

---

### Post by acastiello on 2009-04-30
Sound's back. The sound applet showed the PCM volume disabled. I enabled it but it did not work. I raised all the volume and could barely hear a CD. I lowered and raised it again, and voila!. Sound came back.  Here is the current status and collection of weird things:

a) The desktop apparence changed. I killed update notifier and the desktop went back to its normal appearence
b) top:
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
 4446 root      20   0  113m  70m  13m S 11.9 11.9   2:00.11 Xorg                
 4708 alvaro    20   0 34444  14m 9928 S  5.6  2.4   0:05.69 gnome-terminal      
 4646 alvaro    20   0  3236 1488  652 S  4.0  0.2   0:42.16 dbus-daemon         
 4481 alvaro    20   0 26988 7552 5920 S  3.3  1.2   0:41.60 x-session-manag     
 4716 alvaro    20   0 30940  16m  13m S  3.3  2.8   0:04.46 vino-server         
 4654 alvaro    20   0  8108 4844 2268 S  3.0  0.8   0:31.67 gconfd-2            
 4812 alvaro    20   0 23344 9824 7776 S  1.7  1.6   0:14.06 indicator-apple     
10262 alvaro    20   0 22636 5528 4308 R  1.7  0.9   0:00.05 vino-server         
 4709 alvaro    20   0  282m 142m  23m S  1.3 24.1   1:39.73 firefox             
 4721 alvaro    20   0 28352  14m 8304 S  1.3  2.4   0:16.16 python              
 4690 alvaro    20   0 44632  26m  15m S  1.0  4.5   0:20.47 gnome-panel         
 4717 alvaro    20   0  229m  42m  22m S  1.0  7.2   0:20.20 rhythmbox           
 5997 alvaro    20   0 30332 9756 6876 S  1.0  1.6   0:09.64 gnome-settings-     
 6060 alvaro    20   0 17176 5428 4116 S  1.0  0.9   0:05.51 gnome-screensav     
 4703 alvaro    20   0 25004  12m 9072 S  0.7  2.1   0:04.41 nm-applet           
 4727 alvaro    20   0 25844 9688 6776 S  0.7  1.6   0:04.17 gnome-power-man     
   14 root      15  -5     0    0    0 S  0.3  0.0   0:00.30 ata/0               
 2796 root      20   0  5180 1804 1592 S  0.3  0.3   0:00.78 hald-addon-stor     
c) Almost everytime i reboot/close session, two nonresponsive process appear: update notifier and an unknow onw
d) the monitor show a nonkillable process with no name. Sometimes it shows two of them both with the same unkillable,no name feaure.
e) found a page about the SIS controller, my xorg.conf is now:

Section "Device"
	Identifier	"Configured Video Device"

	# Now for the real thing:
        Driver "sis"

	# EnableSiSCtrl must be set to use SiSCtrl
        Option "EnableSiSCtrl" "yes"

	# [sisctrl] Enable/disable Gamma correction for CRT1
	Option "CRT1Gamma" "on"
	# [sisctrl] Xv (video overlay) related options
	Option "XvDefaultContrast" "2"
	Option "XvDefaultBrightness" "10"
	Option "XvDefaultHue" "0"
	Option "XvDefaultSaturation" "0"
	Option "XvDefaultDisableGfxLR" "no"
	Option "XvGamma" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	# Gamma correction 
	Gamma 1.000 1.000 1.000

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

f) If I log with a different user and/or the install CD the cpu hits at most 40%

Regards,
Alvaro

---

### Post by soro2005 on 2009-04-30
If you kill pulseaudio, then the sound is gone. That's expected behavior :-D Should come back the next time you log in, though.

The system monitor application indeed consumes a lot of cpu. This is because of the way it draws the graphs, and it was a big issue back when they first came up with the flashy graphs. I thought it had gotten better, but it's still consuming a little.

If I understand you right, a fresh user is better on the CPU? About the same as the Live CD?

In that last reading of top, you have a lot running. That makes it a little difficult to isolate the issue. There's firefox, rythmbox, etc. They may individually cause a spike in CPU usage.

It looks to me like one or some of the applets on your gnome panel might be hanging. The following will, I believe, reset your gnome panel to the state in which it is shipped:
```
gconftool-2 --recursive-unset /apps/panel
```
Log out and log in again, and let me know whether it helped.

-----------------Added the following---------------------

dpkg --configure is to finish installations which may have been aborted in a bad state. If it returns nothing, then that's a good sign. And the DOS prompt is just the prompt. :-D

Who'd be stirring the panic? It costs a lot of money, even if the government can use it to do the super hero.

---

### Post by ladydeth666 on 2009-04-30
My system sound never disappeared, but I am accustomed to losing sound while playing World Warcraft in Wine.  9.04 had fixed that problem, allowing me sound in Firefox, Banshee and WoW/Wine.  
I dont want to blame pulse audio, but ever since that patch I am back to one program having priority on sound, and my system's performance has decreased significantly.  If Im running WoW, I can open FF and not lose sound.  If I play any sound (even the cheesy gmail chat sound), WoW loses sound to FF.  
Im using Alsa to control all sounds, and since I dont remember changing any configs, maybe its default?  With all previous Ubuntu versions (7.10, 8.04, 8.10) I have had to comment out the usb sound in the alsa config, because my onboard sound is usb controlled instead of pci.

Im running the 9.04 beta upgraded to yesterday on a ASUS M2N-E sli mobo with an AMD 5400+.

Now that Ive typed all this up, wasnt there a recent update to ALSA also?

When I get home, I will try the new user, and see how it goes.

---

### Post by soro2005 on 2009-04-30
@ladydeth: You have an Nvidia video card and a problem with your audio setup. The original poster has a SiS video card and, as far as we have seen so far, no problem with the audio setup. Your problem is not the same as acastiello's, and if you want quality assistance, then you better post your own thread. In any case, my recommendations are for the original poster and will not help you.

---

### Post by acastiello on 2009-04-30
> **soro2005 said:**
> If you kill pulseaudio, then the sound is gone. That's expected behavior :-D Should come back the next time you log in, though.

Sound was gone with or without pulseaudio for both me and the new user. But fortunately it came back :) using the sound control panel

> **soro2005 said:**
> If I understand you right, a fresh user is better on the CPU? About the same as the Live CD?

Exactly

> **soro2005 said:**
> In that last reading of top, you have a lot running. That makes it a little difficult to isolate the issue. There's firefox, rythmbox, etc. They may individually cause a spike in CPU usage.

Oh! I was testing the sound with that and forgot to close firefox and rythmbox, but most of my tests are done with nothing more thant the terminal with top

> **soro2005 said:**
> It looks to me like one or some of the applets on your gnome panel might be hanging. The following will, I believe, reset your gnome panel to the state in which it is shipped:
```
gconftool-2 --recursive-unset /apps/panel
```
Log out and log in again, and let me know whether it helped.

same :(. The panel reseted but the cpu remains the same


-----------------Added the following---------------------

> **soro2005 said:**
> dpkg --configure is to finish installations which may have been aborted in a bad state. If it returns nothing, then that's a good sign. And the DOS prompt is just the prompt. :-D

:D

> **soro2005 said:**
> Who'd be stirring the panic? It costs a lot of money, even if the government can use it to do the super hero.

You are absolutely right!, we have too much "influenza" and very little money right now :(

Something draws my attention. Take a look to my last top:
alvaro@amara:~$ top -u alvaro

top - 18:58:03 up  1:00,  2 users,  load average: 4.74, 4.12, 4.22
Tasks: 125 total,   3 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s): **64.6%us**, 32.8%sy,  2.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:    606160k total,   413776k used,   192384k free,    25144k buffers
Swap:  1405648k total,    16812k used,  1388836k free,   197828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2858 root      20   0 98344  51m  12m S  9.9  8.7   3:34.81 Xorg               
 3451 alvaro    20   0 30936  16m  13m S  5.0  2.8   0:08.33 vino-server        
 3404 alvaro    20   0  5332 3508  656 S  4.0  0.6   3:01.29 dbus-daemon        
 3291 alvaro    20   0 26952 7496 5900 S  3.6  1.2   2:16.94 x-session-manag    
 3412 alvaro    20   0  8160 4896 2268 S  2.7  0.8   1:52.00 gconfd-2           
 3476 alvaro    20   0 28340  14m 8276 S  2.3  2.4   0:48.16 python             
27244 alvaro    20   0 22936 6916 5460 R  2.3  1.1   0:00.07 vino-server        
 3429 alvaro    20   0 30372 9772 6892 S  2.0  1.6   0:38.90 gnome-settings-    
 3467 alvaro    20   0 34084  14m 9944 S  1.7  2.4   0:27.19 gnome-terminal     
 3448 alvaro    20   0 40740  21m  15m S  1.3  3.7   0:28.70 gnome-panel        
 3544 alvaro    39  19 33688  15m 6708 R  1.3  2.6   0:32.26 tracker-indexer    
 3612 alvaro    20   0 17180 5540 4156 S  1.0  0.9   0:20.80 gnome-screensav    
 3457 alvaro    39  19 54168  11m 5060 S  0.7  1.9   0:13.42 trackerd           
 3459 alvaro    20   0 23372  11m 8392 S  0.7  2.0   0:06.49 nm-applet          
 3478 alvaro    20   0 19612 7448 6076 S  0.7  1.2   0:10.98 tracker-applet     
 3488 alvaro    20   0 25808 9384 6492 S  0.7  1.5   0:14.60 gnome-power-man    
 3551 alvaro    20   0 27376  13m   9m S  0.7  2.3   0:09.71 fast-user-switc    
 3557 alvaro    20   0 23700 9.9m 7636 S  0.7  1.7   1:03.59 indicator-apple    
 2797 root      20   0  5180 1676 1588 S  0.3  0.3   0:00.45 hald-addon-stor    
 3454 alvaro    20   0 20364 9572 7180 S  0.3  1.6   0:05.00 bluetooth-apple    
 3483 alvaro    20   0 22744  11m 8228 S  0.3  2.0   0:05.90 notify-osd         
11716 alvaro    20   0  2448 1192  912 R  0.3  0.2   0:08.02 top                
    1 root      20   0  3084  616  564 S  0.0  0.1   0:01.71 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.94 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.80 ata/0              
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      


If you sum the cpu load off all process shown in top, they are not even close to the **64.6%us** consumed. Is another hidden process consumig cpu time or I am misunderstanding (newbie) top results?

Regards,
Alvaro Castiello

---

### Post by soro2005 on 2009-04-30
What I find remarkable is that you never have one single process getting even over 10%, but there's all that gnome panel stuff that should be essentially sleeping. D-bus daemon is always in the mix, but that can be a lot of things. In your current top, you have two vinos. You've also said your remote desktop hung. Perhaps the server is started twice. Can you kill vino and see whether that does anything?
```
killall vino-server
```
Then, if that doesn't do anything, just for the sake it kill also the gconf daemon
```
killall gconfd-2
```
Save your work before you do this as this might cause some distress. Should recover the next time you start a session.

---

### Post by r+9 on 2009-05-01
I've just caught up, I've been bashing my head against this issue for almost a week.

That last cmd

killall gconfd-2

had an effect on the top and ...  To make things quick I was having all the same CPU issues with some mystery "thing" taking up all the CPU.

What drives me nuts is my wife upgraded before me and had 0-problems.

One question, my previous install was Linux Mint and I was heavy into the compiz-fusion stuff.  I keep a separate /home, could there be something in the config files that is causing this?

---

### Post by r+9 on 2009-05-01
egads... to answer my own question.

/.gconf that nice little directory that seems to keep all my ultra-cool settings was misbehaving, CPU down to normal after a reset.

I'm going to selectively restore my old .gconf until the problem comes back so maybe I can have a more specific answer.

---

### Post by r+9 on 2009-05-01
Alrighty, for me, the stinker was the .XML file in .gconf under this directory:

~/.gconf/desktop/gnome/%gconf.xml

soon as I deleted that bugger the lag (and most of my settings) cleared up.
This turned out to be a temporary fix, next relog the CPU pig was back.

---

### Post by ladydeth666 on 2009-05-01
> @ladydeth: You have an Nvidia video card and a problem with your audio setup. The original poster has a SiS video card and, as far as we have seen so far, no problem with the audio setup. Your problem is not the same as acastiello's, and if you want quality assistance, then you better post your own thread. In any case, my recommendations are for the original poster and will not help you.

My problem is a maxed out dual core amd 5400, I was just responding to the sound question.  Wine is my sound problem :)
Killing pulseaudio didnt seem to have any affect, altho I was hoping it would.

I removed and reinstalled the update-notifier, seems to be helping a small bit. 

The only thing using cpu is the gnome manager, sitting at ~30%.  

> Alrighty, for me, the stinker was the .XML file in .gconf under this directory:

~/.gconf/desktop/gnome/%gconf.xml

soon as I deleted that bugger the lag (and most of my settings) cleared up.
This turned out to be a temporary fix, next relog the CPU pig was back.

Looks like gnome is the culprit.  I'll back the file up when I get home, and see if I get the same result.

---

### Post by acastiello on 2009-05-01
> **soro2005 said:**
> What I find remarkable is that you never have one single process getting even over 10%, but there's all that gnome panel stuff that should be essentially sleeping. D-bus daemon is always in the mix, but that can be a lot of things. In your current top, you have two vinos. You've also said your remote desktop hung. Perhaps the server is started twice. Can you kill vino and see whether that does anything?
```
killall vino-server
```

Soro, you have the eye of a hawk and I'm suffering the oxygen poissoning tunneling sight :D. I was so focused in finding a culprit  that didn't notice that vino server was running twice even when I killed it a few days ago and the the cpu dropped to 30%. So the current situation is:

a) if I **killall vino-server** the cpu drops to 30% even in the monitor
b) When entering Remote desktop preferences and enabling it again, **two** instances of vino-server are launched and cpu hits 100%
c) Despite that, only one instance appears in monitor, top shows both
d) Sometimes even three instances show
e) In the "clean" user, although it also has the remove desktop enabled, only one instance of vino-server launches and the cpu remains at a healthy 17%


The investigation is almost over skipper :D
Alvaro Castiello

BTW when you asked to reset my desktop, where is the configuration file stored for such?

---

### Post by Greahm on 2009-05-01
SORO2005, thanks!  I too had just installed the new Ubuntu version and was having the same CPU usage problem.  The tracking/notifying seemed to be a problem for my system also.  Thank you for providing the fix!
Greahm

---

### Post by soro2005 on 2009-05-01
> **acastiello said:**
> Soro, you have the eye of a hawk and I'm suffering the oxygen poissoning tunneling sight :D. I was so focused in finding a culprit  that didn't notice that vino server was running twice even when I killed it a few days ago and the the cpu dropped to 30%.
So the question is how to fix the vino server. [This](https://bugs.launchpad.net/vino/+bug/340515) seems to be the relevant bug. The bottom line: If the vino-server starts with the gnome session, it may be spiking CPU. You may have to start it differently for the time being.

> **acastiello said:**
> BTW when you asked to reset my desktop, where is the configuration file stored for such?

The configuration files for the gnome session are in /home/user-name/.gconf In theory, you can throw that entire directory away as some here suggest, but you will lose a lot of other configurations as well. You can open a graphical interface to edit the configuration files by hittling <alt> + <f2> and typing gconf-editor, or you can play with them from the command line with gconftool-2

---

### Post by ladydeth666 on 2009-05-01
Thank you so much, Soro.  Testing the bug suggestions soon.

---

### Post by acastiello on 2009-05-01
> **Greahm said:**
> SORO2005, thanks!  I too had just installed the new Ubuntu version and was having the same CPU usage problem.  The tracking/notifying seemed to be a problem for my system also.  Thank you for providing the fix!
Greahm

Greham, did you find where vino-server was dplicate launching?

Regards,
Alvaro Castielo

---

### Post by acastiello on 2009-05-01
> **soro2005 said:**
> So the question is how to fix the vino server. [This](https://bugs.launchpad.net/vino/+bug/340515) seems to be the relevant bug. The bottom line: If the vino-server starts with the gnome session, it may be spiking CPU. You may have to start it differently for the time being.

As you state the culprit has been found at least for me, but maybe is not a vino-servwer issue but a user one. When I log in, two vino instances are launched (from where or why?) raising cpu to 100%. After killing them, a **third** instance is launched (again, from where or why?) that runs fine and no longer harms the cpu usage. This happens only with my user. The fresh one has no such problem. This is a top after the third instance is launched (and taken using the machine remotely):

top - 16:16:22 up 22:18,  2 users,  load average: 0.06, 0.06, 0.18
Tasks: 118 total,   2 running, 116 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.6%us,  3.0%sy,  0.0%ni, 84.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    606160k total,   418332k used,   187828k free,    37204k buffers
Swap:  1405648k total,    14816k used,  1390832k free,   207700k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8919 alvaro    20   0 34088  14m 9812 R  6.3  2.4   0:04.67 gnome-terminal     
 8717 root      20   0 69256  24m  13m S  5.0  4.1   0:28.45 Xorg               
 9331 alvaro    20   0 30816  16m  13m S  2.3  2.8   0:07.64 vino-server        
 9074 alvaro    20   0 17180 5384 4076 S  1.3  0.9   0:01.07 gnome-screensav    
 8898 alvaro    20   0 21308  11m 8576 S  0.7  1.9   0:01.21 metacity           
 9332 alvaro    20   0  2448 1176  912 R  0.7  0.2   0:04.29 top                
 8922 alvaro    20   0 98188  34m  19m S  0.3  5.8   0:05.14 rhythmbox          
    1 root      20   0  3084  616  564 S  0.0  0.1   0:01.78 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:06.03 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.83 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.99 kblockd/0          



> **soro2005 said:**
> The configuration files for the gnome session are in /home/user-name/.gconf In theory, you can throw that entire directory away as some here suggest, but you will lose a lot of other configurations as well. You can open a graphical interface to edit the configuration files by hittling <alt> + <f2> and typing gconf-editor, or you can play with them from the command line with gconftool-2

thanks :D

---

### Post by soro2005 on 2009-05-01
This is what the bug states. If you start the vino server with the gnome session, it spawns instances of vino server which cause the hang up. If you kill the vino server and then start it manually by typing
```
/usr/lib/vino/vino-server &
```
into a terminal, the server should run but not spawn additional instances. To prevent it from autostarting with the gnome session, disable "Allow other users to view this desktop" in System --> Preferences --> Remote Desktop.

If this is so and you need the remote desktop (which seems to be the case), then perhaps you can manually add an entry pointing to /usr/lib/vino/vino-server in System --> Preferences --> Startup Programs.

Your other user may not have the problem because the remote desktop is not enabled for that user?

---

### Post by acastiello on 2009-05-01
> **soro2005 said:**
> This is what the bug states. If you start the vino server with the gnome session, it spawns instances of vino server which cause the hang up. If you kill the vino server and then start it manually by typing
```
/usr/lib/vino/vino-server &
```
into a terminal, the server should run but not spawn additional instances. To prevent it from autostarting with the gnome session, disable "Allow other users to view this desktop" in System --> Preferences --> Remote Desktop.

If this is so and you need the remote desktop (which seems to be the case), then perhaps you can manually add an entry pointing to /usr/lib/vino/vino-server in System --> Preferences --> Startup Programs.

Your other user may not have the problem because the remote desktop is not enabled for that user?

The bug "works" as stated in the post, but only for me. The fresh user has indeed the remote desktop enabled and does not have any problem but...these fresh user was created under 9.04 when you asked me to and my user comes from 8.10. Could it mean something?. Reading the post about the bug, it seems that people that upgraded have the same problem, but not new 9.04 users

Regards,
Alvaro Castiello

P.D. If your time allows, could you guide through other issue?. Is not big deal this time :D. Is a doubt about hibernating and wake on lan. I'll post the thread "Wake on LAN and hibernation don't mix"

---

### Post by soro2005 on 2009-05-01
I don't think it's technically possible to have wake on lan on hibernation. Hibernation is like switching the machine off. Wake on lan would assume that it's not entirely powered off. On "suspend" perhaps, or in some low power mode. That's my sense of it.

*Edit: Ok, I didn't know that. There are machines that wake up from power off. I don't have any idea about to trouble shoot that, though.*


Now for the vino server: That's very possible that it only occurs on upgrade. Perhaps, you could just disable the remote desktop entry in the Startup Applications? Also regenerate the settings for the vino server with
```
gconftool-2 --recursive-unset /desktop/remote-access
```
Then log out and log in again, and re-enable remote access. I don't have any idea where else the vino server stores it's settings. I don't use it.

---

### Post by acastiello on 2009-05-07
> **soro2005 said:**
> I don't think it's technically possible to have wake on lan on hibernation. Hibernation is like switching the machine off. Wake on lan would assume that it's not entirely powered off. On "suspend" perhaps, or in some low power mode. That's my sense of it.

*Edit: Ok, I didn't know that. There are machines that wake up from power off. I don't have any idea about to trouble shoot that, though.*

Sorry for the delayed answer Soro. The city is awakening from the virus attack and things are going really nuts here. As I told I will start another thread, but just for a quick comment, my machine is able to WOL when shutted down, but not when hibernated. Hate to say this, but the "other" :D operating system can do it from both power off or hibernation, and since waking on lan a pc resides both in bios and software, my guess is that I'm missing something to configure


> **soro2005 said:**
> Now for the vino server: That's very possible that it only occurs on upgrade. Perhaps, you could just disable the remote desktop entry in the Startup Applications? Also regenerate the settings for the vino server with
```
gconftool-2 --recursive-unset /desktop/remote-access
```
Then log out and log in again, and re-enable remote access. I don't have any idea where else the vino server stores it's settings. I don't use it.

I logged out and in following your instructions but the problem remains. The "solution" is to log in, killall vinoserver, wait a little and then again killall vinoserver since many instances appear after logging. Once the massacre  is over, a new fresh single instance of vinoserver "appears" :confused: and everything runs fine. Since I use hibernation, I only need to do this if I reboot or logout. So, for the time being, thank you again for your valuable help and time. I'll see you around in other threads

Best regards,
Alvaro Castiello

---

