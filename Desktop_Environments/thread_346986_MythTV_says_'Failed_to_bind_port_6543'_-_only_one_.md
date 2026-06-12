---
title: "MythTV says 'Failed to bind port 6543' - only one instance running"
date: 2007-01-26
forum: Desktop Environments
---

### Post by kerinin on 2007-01-26
MythTV has been giving me a lot of problems lately.  The current problem is that over time the backend will become unresponsive, and when i try to restart it, i get the following:

```
kerinin@simon:~$ sudo mythbackend
2007-01-26 13:19:47.744 Using runtime prefix = /usr
2007-01-26 13:19:47.771 New DB connection, total: 1
2007-01-26 13:19:47.775 Connected to database 'mythconverg' at host: localhost
2007-01-26 13:19:47.779 Current Schema Version: 1160
Starting up as the master server.
2007-01-26 13:19:47.782 mythbackend: MythBackend started as master server
2007-01-26 13:19:47.791 New DB connection, total: 2
2007-01-26 13:19:47.791 Connected to database 'mythconverg' at host: localhost
2007-01-26 13:19:47.792 EITHelper: localtime offset -6:00:00 
2007-01-26 13:19:47.883 New DB connection, total: 3
2007-01-26 13:19:47.884 Connected to database 'mythconverg' at host: localhost
2007-01-26 13:19:48.033 EITHelper: localtime offset -6:00:00 
2007-01-26 13:19:48.114 New DB scheduler connection
2007-01-26 13:19:48.115 Connected to database 'mythconverg' at host: localhost
2007-01-26 13:19:48.116 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2007-01-26 13:19:48.127 Main::HttpServer Create Error
2007-01-26 13:19:48.127 Main::Registering HttpStatus Extension
2007-01-26 13:19:48.131 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-01-26 13:19:48.131 Enabled verbose msgs:  important general
2007-01-26 13:19:48.132 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-01-26 13:19:48.132 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-01-26 13:19:48.142 Failed to bind port 6543. Exiting.
```

this makes me think that there's another process using that port, so i try running netstat, and here's what i get:

```
kerinin@simon:~$ netstat | grep 6543
tcp       30      0 192.168.1.4:6543        192.168.1.4:47185       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47184       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47187       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47186       CLOSE_WAIT 
tcp       88      0 192.168.1.4:6543        192.168.1.4:58197       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47188       CLOSE_WAIT 
tcp        1      0 192.168.1.4:6543        192.168.1.4:58198       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47181       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47183       CLOSE_WAIT 
tcp       30      0 192.168.1.4:6543        192.168.1.4:47182       CLOSE_WAIT 
tcp        1      0 192.168.1.4:6543        192.168.1.4:51696       CLOSE_WAIT 
tcp       42      0 192.168.1.4:6543        192.168.1.4:51695       CLOSE_WAIT 

```

I don't know much about ports, but this looks to me like something is using the port 6543.  The other strange thing is that there's a zombie mythbackend process which I can't kill, and I suspect that maybe that process is still using the ports.  Here's what the process looks like:

```
kerinin@simon:~$ ps -A | grep myth
 5188 ?        00:00:38 mythbackend <defunct>
```

Does anyone know how to fix this?  Any help is much appreciated - i really like mythtv, i just wish it would WORK.

---

### Post by SyvanX on 2007-01-26
It's definitely because you have a mythbackend process running.

Have you checked your mythbackend.log for any weirdness?

```
cat /var/log/mythtv/mythbackend.log
```

---

### Post by kerinin on 2007-01-27
I dug through the logs and found this - this is a pretty common error i see (the proto_version thing).  it looks like maybe this is a glitch in the ivtv driver?

```
2007-01-25 22:35:50.313 AFD: Opened codec 0x2aaaabf05a30, id(MPEG2VIDEO) type(Video)
2007-01-25 22:35:50.341 AFD: Opened codec 0x2aaaabf076d0, id(MP2) type(Audio)
2007-01-25 22:37:50.155 TVRec(1): Changing from WatchingLiveTV to None
2007-01-25 22:37:50.651 Finished recording The Colbert Report: channel 1059
2007-01-25 22:37:50.766 scheduler: Finished recording: The Colbert Report: channel 1059
2007-01-25 22:37:55.988 MainServer::HandleAnnounce Playback
2007-01-25 22:37:55.999 adding: simon as a client (events: 0)
2007-01-25 22:37:56.002 TVRec(1): Changing from None to WatchingLiveTV
2007-01-25 22:37:56.020 TVRec(1): HW Tuner: 1->1
2007-01-25 22:38:02.798 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2007-01-25 22:38:51.654 TVRec(1): Changing from WatchingLiveTV to None
2007-01-25 22:43:57.066 Using runtime prefix = /usr
2007-01-25 22:43:57.219 New DB connection, total: 1
2007-01-25 22:43:57.261 Connected to database 'mythconverg' at host: localhost
2007-01-25 22:43:57.291 Current Schema Version: 1160
Starting up as the master server.
2007-01-25 22:43:57.331 mythbackend: MythBackend started as master server
2007-01-25 22:43:57.411 New DB connection, total: 2
2007-01-25 22:43:57.470 Connected to database 'mythconverg' at host: localhost
2007-01-25 22:43:57.508 EITHelper: localtime offset -6:00:00
2007-01-25 22:43:57.550 New DB connection, total: 3
2007-01-25 22:43:57.551 Connected to database 'mythconverg' at host: localhost
2007-01-25 22:44:07.361 MythSocket(621ff0:7): readStringList: Error, timeout.
2007-01-25 22:44:07.368 Connection to backend server lost
2007-01-25 22:44:07.368 Connecting to backend server: 192.168.1.4:6543 (try 1 of 10)
2007-01-25 22:44:07.375 mythbackend: Running housekeeping thread
2007-01-25 22:44:14.377 MythSocket(2aaaadc8f420:7): readStringList: Error, timeout (quick).
2007-01-25 22:44:14.383 Unexpected response to MYTH_PROTO_VERSION:
2007-01-25 22:44:14.385 Reconnection to backend server failed
2007-01-25 22:44:26.538 Connecting to backend server: 192.168.1.4:6543 (try 1 of 10)
2007-01-25 22:44:33.544 MythSocket(2aaaadc99ce0:7): readStringList: Error, timeout (quick).
2007-01-25 22:44:33.545 Unexpected response to MYTH_PROTO_VERSION:
2007-01-25 22:44:44.768 Connecting to backend server: 192.168.1.4:6543 (try 1 of 10)
2007-01-25 22:44:47.425 EITHelper: localtime offset -6:00:00
2007-01-25 22:44:47.508 New DB scheduler connection
2007-01-25 22:44:47.517 Connected to database 'mythconverg' at host: localhost
2007-01-25 22:44:47.523 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2007-01-25 22:44:47.532 Main::HttpServer Create Error
2007-01-25 22:44:47.556 Main::Registering HttpStatus Extension
2007-01-25 22:44:47.587 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-01-25 22:44:47.596 Enabled verbose msgs:  important general
2007-01-25 22:44:47.622 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-01-25 22:44:47.634 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-01-25 22:44:47.638 Failed to bind port 6543. Exiting.
2007-01-25 22:44:51.771 MythSocket(2aaaadca4030:7): readStringList: Error, timeout (quick).
2007-01-25 22:44:51.803 Unexpected response to MYTH_PROTO_VERSION:
2007-01-25 22:45:02.990 Connecting to backend server: 192.168.1.4:6543 (try 1 of 10)
2007-01-25 22:45:10.242 MythSocket(2aaaadcae650:7): readStringList: Error, timeout (quick).
2007-01-25 22:45:10.243 Unexpected response to MYTH_PROTO_VERSION:
```

---

### Post by SyvanX on 2007-01-27
yeah, looks like it might be ivtv.  You should try to remove the ivtv module, then re-insert the module.  Since you can't kill mythbackend, it might not work, but it's worth a shot. *(if you're using the PVR-350 output, include ivtv_fb after ivtv below.)*

```
/etc/init.d/mythtv-backend stop

sudo rmmod ivtv
sudo modprobe ivtv

/etc/init.d/mythtv-backend start
```

---

### Post by superm1 on 2007-01-28
Also,

don't start mythbackend with

```
sudo mythbackend
```

This launches it with root permissions rather than "mythtv" Permissions.  Its both a security hole and inconvenient since logging won't occur in /var/log/mythtv/mythbackend.log when done this way.

---

### Post by kerinin on 2007-01-28
I know, it's just easier for debugging when you can see the output on the terminal.  I usually use init.d.

So i changed /boot/grub/menu.lst to boot with noapic and nosmp (found that somewhere, don't remember where), and i haven't had any problems so far (still waiting to see if it's fixed or just hasn't broken yet).  There have been some problems with conflicts between processor frequency scaling and the Hauppage 500 card.

anyway, fingers crossed...

---

### Post by superm1 on 2007-01-28
> **kerinin said:**
> I know, it's just easier for debugging when you can see the output on the terminal.  I usually use init.d.

So i changed /boot/grub/menu.lst to boot with noapic and nosmp (found that somewhere, don't remember where), and i haven't had any problems so far (still waiting to see if it's fixed or just hasn't broken yet).  There have been some problems with conflicts between processor frequency scaling and the Hauppage 500 card.

anyway, fingers crossed...
Oh you got me curious about issues with processor frequency scaling and the IVTV cards.  I just picked up a new amd64 proc and motherboard that supports powernow! and hence uses an ondemand frequency scaler.  What happens with the combo?

---

### Post by wiz561 on 2007-02-05
Just wondering, how you're coming along with your amd64 processor.  I've always had problems with "firmware unresponsive", and it seems like only one version of ivtv will work with it (0.4.6).  

I just upgraded because I got a new HD capture card, and the old kernel didn't recognize it.  I tried to compile v4l, and it recognized the card, but made ivtv crash.  

Arghhh...  Anyways, just wondering how it's going for you.

Also, I don't know how to turn off cpu scaling.  I think it's a kernel option when you confiugre/make your own kernel, but not 100% sure.

Good Luck!

---

### Post by kerinin on 2007-02-05
the noapic and nosmp thing seems to have fixed it.  I'm still having issues with sound, but i think that's related to my sound card.  otherwise everything has been going fine.

---

### Post by superm1 on 2007-02-05
> **wiz561 said:**
> Just wondering, how you're coming along with your amd64 processor.  I've always had problems with "firmware unresponsive", and it seems like only one version of ivtv will work with it (0.4.6).  

I just upgraded because I got a new HD capture card, and the old kernel didn't recognize it.  I tried to compile v4l, and it recognized the card, but made ivtv crash.  

Arghhh...  Anyways, just wondering how it's going for you.

Also, I don't know how to turn off cpu scaling.  I think it's a kernel option when you confiugre/make your own kernel, but not 100% sure.

Good Luck!
I'm having a hell of a time with mine.  Kernel seg faults often.  I turned off cpu frequency scaling yesterday though, and have been fine since.  *JINX*....
I removed powernowd to keep it from starting.

---

### Post by wiz561 on 2007-02-06
Interesting results.  I agree, removing NOAPIC and NOSMP does fix it, but then if you have a dual-core processor, you can't use the second core/cpu.  Not really an option for me.  

As far as turning off CPU Scaling, superm1, how did you end up doing it?  I ended up posting a message a week or two ago here...

[http://ubuntuforums.org/showthread.php?t=348969](http://ubuntuforums.org/showthread.php?t=348969)

One person said to do the following...

echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

But in order to do that, I had to install cpufreqd, and powernowd because that path did not exist.  I haven't tried it since, but I would be surprised if it fixes it.  

Also, I have a Kworld ATSC110 card and pvr150.  When I was running Dapper, when I installed the cvs of video4linux and ivtv, ivtv would crash.  I upgraded to Feisty because everything is already built for the kernel, but I still get those firmware unresponsive messages.  As mentioned above, I haven't tried it since I set the scaling_governor to "performance", but I would be surprised if that would fix it.

Thanks for your help!

---

### Post by superm1 on 2007-02-06
> **wiz561 said:**
> Interesting results.  I agree, removing NOAPIC and NOSMP does fix it, but then if you have a dual-core processor, you can't use the second core/cpu.  Not really an option for me.  

As far as turning off CPU Scaling, superm1, how did you end up doing it?  I ended up posting a message a week or two ago here...

[http://ubuntuforums.org/showthread.php?t=348969](http://ubuntuforums.org/showthread.php?t=348969)

One person said to do the following...

echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

But in order to do that, I had to install cpufreqd, and powernowd because that path did not exist.  I haven't tried it since, but I would be surprised if it fixes it.  

Also, I have a Kworld ATSC110 card and pvr150.  When I was running Dapper, when I installed the cvs of video4linux and ivtv, ivtv would crash.  I upgraded to Feisty because everything is already built for the kernel, but I still get those firmware unresponsive messages.  As mentioned above, I haven't tried it since I set the scaling_governor to "performance", but I would be surprised if that would fix it.

Thanks for your help!
I yes i should have described this.
I installed sysv-rc-conf.
```
sudo apt-get install sysv-rc-conf
```
and then run it by
```
sudo sysv-rc-conf
```
You can remove powernowd from all its current runlevels then.  The power management/scaling modules shouldn't be loaded now either.

---

### Post by wiz561 on 2007-02-06
Thank you for the information!  I've never ran this before but it is awesome!  I prefer command line utils rather than GUI ones...so this is pretty cool.

Now the bad news.  Powernowd doesn't exist in the list!  However, I see that cpufreqd and cpufrequt$ exist in the list.  Is this the same at Powernowd?


Thanks again for the util!

---

### Post by superm1 on 2007-02-06
> **wiz561 said:**
> Thank you for the information!  I've never ran this before but it is awesome!  I prefer command line utils rather than GUI ones...so this is pretty cool.

Now the bad news.  Powernowd doesn't exist in the list!  However, I see that cpufreqd and cpufrequt$ exist in the list.  Is this the same at Powernowd?


Thanks again for the util!
CPUfreqd is another daemon available for the same task, you can disable it just the same through here.

---

### Post by gearshifter on 2007-02-08
i have the same problem where IVTV drop one of my two tuners?  (Hauppage 500 card)

I can watch tv, watch recordings and when i go to watch tv again, the tuner wont load.  After it goes back to the main menu, i can select "Watch TV" and it will default to the other tv tuner.  Eventually both will fail and I will have to restart my computer to get both of them to work again.

---

### Post by superm1 on 2007-02-08
> **gearshifter said:**
> i have the same problem where IVTV drop one of my two tuners?  (Hauppage 500 card)

I can watch tv, watch recordings and when i go to watch tv again, the tuner wont load.  After it goes back to the main menu, i can select "Watch TV" and it will default to the other tv tuner.  Eventually both will fail and I will have to restart my computer to get both of them to work again.
Anything in dmesg or /var/log/mythtv/mythbackend.log after this happens?  You might consider installing the latest version of ivtv available.  Directions are at the bottom of the ivtv wiki page for how to do this.

---

### Post by gearshifter on 2007-02-08
```
[  173.403284] ivtv1 warning: 1000 ms time out waiting for firmware
[  173.403290] ivtv1 warning: Failed api call 0x00000082 with result 0xfffffff0
[  173.403299] ivtv1 warning: ENC: Failed stopping capture -16
[  176.621730] ivtv1 warning: No Free Mailbox for cmd 0x000000db after 100 tries!
[  176.621739] ivtv1 warning: Mailbox[0] 0x000000dc flags 0x00000003
[  176.621748] ivtv1 warning: Mailbox[1] 0x000000d9 flags 0x00000003
[  176.621755] ivtv1 warning: Mailbox[2] 0x000000c9 flags 0x00000003
[  176.621761] ivtv1 warning: Firmware UNRESPONSIVE when trying cmd 0x000000db!!!
[  179.859217] ivtv1 warning: No Free Mailbox for cmd 0x000000dc after 100 tries!
[  179.859226] ivtv1 warning: Mailbox[0] 0x000000dc flags 0x00000003
[  179.859234] ivtv1 warning: Mailbox[1] 0x000000dc flags 0x00000003
[  179.859240] ivtv1 warning: Mailbox[2] 0x000000dc flags 0x00000003
[  179.859245] ivtv1 warning: Firmware UNRESPONSIVE when trying cmd 0x000000dc!!!
[  187.871679] ivtv1 warning: 1000 ms time out waiting for firmware
[  187.871686] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  195.911151] ivtv1 warning: 1000 ms time out waiting for firmware
[  195.911158] ivtv1 warning: Failed api call 0x000000c8 with result 0xfffffff0
[  195.911209] ivtv1 warning: init error 21. Code -16
[  204.100906] ivtv1 warning: 1000 ms time out waiting for firmware
[  204.100913] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  212.158855] ivtv1 warning: 1000 ms time out waiting for firmware
[  212.158861] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  220.167412] ivtv1 warning: 1000 ms time out waiting for firmware
[  220.167419] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  228.193947] ivtv1 warning: 1000 ms time out waiting for firmware
[  228.193954] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  236.211073] ivtv1 warning: 1000 ms time out waiting for firmware
[  236.211080] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  244.216997] ivtv1 warning: 1000 ms time out waiting for firmware
[  244.217004] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  252.222721] ivtv1 warning: 1000 ms time out waiting for firmware
[  252.222728] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  260.242761] ivtv1 warning: 1000 ms time out waiting for firmware
[  260.242767] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  268.318543] ivtv1 warning: 1000 ms time out waiting for firmware
[  268.318549] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  276.332492] ivtv1 warning: 1000 ms time out waiting for firmware
[  276.332498] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  284.338395] ivtv1 warning: 1000 ms time out waiting for firmware
[  284.338401] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  292.692163] ivtv1 warning: 1000 ms time out waiting for firmware
[  292.692169] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  300.729940] ivtv1 warning: 1000 ms time out waiting for firmware
[  300.729946] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0
[  308.746134] ivtv1 warning: 1000 ms time out waiting for firmware
[  308.746141] ivtv1 warning: Failed api call 0x000000b7 with result 0xfffffff0

```

after that and mythtv menu loads i can click watch tv fast again and then i get tuner one except the default tuner2.  If i close out livetv again and open it again, i have lost both.  I had this problem in edgy with all the versions of ivtv so i upgraded to feisty so it is built into the kernel now.

---

### Post by gearshifter on 2007-02-08
i can open and close and open livtv and it will work fine.  It is when i change channels and close and then try to open again is when i lose it.

edit:  I disabled acpisupp and powernowd and that seems to do nothing.  So i am going to re-enable it.

```
2007-02-08 07:50:19.924 MainServer::HandleAnnounce Monitor
2007-02-08 07:50:21.874 adding: Jason-Desktop as a client (events: 0)
2007-02-08 07:50:21.876 MainServer::HandleAnnounce Monitor
2007-02-08 07:50:21.876 adding: Jason-Desktop as a client (events: 1)
2007-02-08 07:50:21.878 Reschedule requested for id -1.
2007-02-08 07:50:23.025 Scheduled 164 items in 1.1 = 0.48 match + 0.67 place
2007-02-08 10:13:06.331 MainServer::HandleAnnounce Playback
2007-02-08 10:13:06.358 adding: Jason-Desktop as a client (events: 0)
2007-02-08 10:13:14.523 Reschedule requested for id 0.
2007-02-08 10:13:14.978 MainServer::HandleAnnounce Playback
2007-02-08 10:13:15.010 adding: Jason-Desktop as a client (events: 0)
2007-02-08 10:13:15.024 TVRec(1): Changing from None to WatchingLiveTV
2007-02-08 10:13:15.171 TVRec(1): HW Tuner: 1->1
2007-02-08 10:13:16.673 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 10:13:16.755 Scheduled 164 items in 2.2 = 0.25 match + 1.98 place
2007-02-08 10:13:41.807 Finished recording Animal Miracles "Second Chance": channel 1044
2007-02-08 10:13:41.994 Finished recording Animal Miracles "Second Chance": channel 1044
0: start_time: 0.036 duration: 2.114
1: start_time: 0.026 duration: 2.095
stream: start_time: 0.289 duration: 23.601 bitrate=5286 kb/s
2007-02-08 10:13:42.030 AFD: Opened codec 0x2aaaac00a250, id(MPEG2VIDEO) type(Video)
2007-02-08 10:13:42.035 AFD: Opened codec 0x2aaaac00a870, id(MP2) type(Audio)
2007-02-08 10:13:42.084 TVRec(1): RingBufferChanged()
2007-02-08 10:13:42.092 Finished recording Animal Miracles "Second Chance": channel 1044
2007-02-08 10:16:45.874 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:18:45.981 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:20:46.112 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:21:01.593 Finished recording The Daily Show With Jon Stewart: channel 1066
2007-02-08 10:21:01.883 Finished recording The Daily Show With Jon Stewart: channel 1066
0: start_time: 2.204 duration: 39.519
1: start_time: 2.177 duration: 39.519
stream: start_time: 24.193 duration: 439.403 bitrate=5190 kb/s
2007-02-08 10:21:01.903 AFD: Opened codec 0x2aaab4466250, id(MPEG2VIDEO) type(Video)
2007-02-08 10:21:01.909 AFD: Opened codec 0x2aaab4469ab0, id(MP2) type(Audio)
2007-02-08 10:21:01.964 TVRec(1): RingBufferChanged()
2007-02-08 10:21:01.974 Finished recording The Daily Show With Jon Stewart: channel 1066
2007-02-08 10:21:08.321 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 10:21:08.481 Finished recording Mickey Blue Eyes: channel 1012
0: start_time: 41.781 duration: 0.550
1: start_time: 41.746 duration: 0.549
stream: start_time: 463.849 duration: 6.487 bitrate=5248 kb/s
2007-02-08 10:21:08.500 AFD: Opened codec 0x2aaab4022660, id(MPEG2VIDEO) type(Video)
2007-02-08 10:21:08.507 AFD: Opened codec 0x2aaab4024b40, id(MP2) type(Audio)
2007-02-08 10:21:08.602 TVRec(1): RingBufferChanged()
2007-02-08 10:21:08.609 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 10:21:11.257 Finished recording Globe Trekker "Kenya": channel 1056
2007-02-08 10:21:11.289 Finished recording Globe Trekker "Kenya": channel 1056
0: start_time: 42.384 duration: 0.207
1: start_time: 42.362 duration: 0.197
stream: start_time: 470.689 duration: 2.550 bitrate=5120 kb/s
2007-02-08 10:21:11.316 AFD: Opened codec 0x78b4f0, id(MPEG2VIDEO) type(Video)
2007-02-08 10:21:11.316 TVRec(1): RingBufferChanged()
2007-02-08 10:21:11.323 AFD: Opened codec 0x714e30, id(MP2) type(Audio)
2007-02-08 10:21:11.331 Finished recording Globe Trekker "Kenya": channel 1056
2007-02-08 10:22:46.221 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:22:46.227 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:22:46.245 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:24:46.352 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:24:46.353 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:24:46.353 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:26:46.463 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:26:46.472 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:26:46.473 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:28:46.575 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:28:46.576 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:28:46.576 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:30:00.913 Finished recording The Daily Show With Jon Stewart: channel 1066
0: start_time: 42.658 duration: 47.616
1: start_time: 42.617 duration: 47.630
stream: start_time: 473.521 duration: 529.514 bitrate=5191 kb/s
2007-02-08 10:30:00.936 AFD: Opened codec 0x703c80, id(MPEG2VIDEO) type(Video)
2007-02-08 10:30:00.943 AFD: Opened codec 0x78f9d0, id(MP2) type(Audio)
2007-02-08 10:30:00.958 TVRec(1): Enabling Full LiveTV UI.
2007-02-08 10:30:01.068 TVRec(1): RingBufferChanged()
2007-02-08 10:30:01.086 Finished recording The Daily Show With Jon Stewart: channel 1066
2007-02-08 10:30:46.689 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:30:46.697 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:30:46.697 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:32:46.804 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:32:46.805 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:32:46.805 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:34:46.910 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:34:46.911 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:34:46.911 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:36:47.021 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:36:47.026 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:36:47.027 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:38:47.133 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:38:47.146 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:38:47.147 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:40:47.295 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:40:47.326 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:40:47.328 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:42:47.486 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:42:47.497 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:42:47.500 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:44:47.610 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:44:47.624 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:44:47.626 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:46:47.742 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:46:47.748 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:46:47.749 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:48:47.847 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:48:47.847 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:48:47.848 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:50:47.946 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:50:47.948 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:50:47.948 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:52:48.045 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:52:48.047 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:52:48.047 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:54:48.144 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:54:48.145 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:54:48.146 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:56:48.248 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:56:48.250 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:56:48.250 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 10:58:48.360 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 10:58:48.360 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 10:58:48.361 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 11:00:01.073 Finished recording The Colbert Report: channel 1066
2007-02-08 11:00:01.151 TVRec(1): Enabling Full LiveTV UI.
0: start_time: 90.351 duration: 161.958
1: start_time: 90.308 duration: 161.970
stream: start_time: 1003.417 duration: 1800.017 bitrate=5190 kb/s
2007-02-08 11:00:01.175 AFD: Opened codec 0x65bea0, id(MPEG2VIDEO) type(Video)
2007-02-08 11:00:01.178 AFD: Opened codec 0x794200, id(MP2) type(Audio)
2007-02-08 11:00:01.630 TVRec(1): RingBufferChanged()
2007-02-08 11:00:01.649 Finished recording The Colbert Report: channel 1066
2007-02-08 11:00:48.467 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 11:00:48.470 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 11:00:48.470 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 11:01:20.270 TVRec(1): Changing from WatchingLiveTV to None
2007-02-08 11:01:20.374 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:03:25.211 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-02-08 11:03:25.996 New DB connection, total: 1
2007-02-08 11:03:26.028 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:03:26.305 Current Schema Version: 1160
Starting up as the master server.
QSettings::sync: filename is null/empty
2007-02-08 11:03:26.646 New DB connection, total: 2
2007-02-08 11:03:26.708 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:03:26.864 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:03:26.994 New DB connection, total: 3
2007-02-08 11:03:26.995 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:03:27.270 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:03:27.551 New DB scheduler connection
2007-02-08 11:03:27.582 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:03:27.618 Main::Starting HttpServer
2007-02-08 11:03:27.776 Main::Registering HttpStatus Extension
2007-02-08 11:03:27.936 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-02-08 11:03:27.988 Enabled verbose msgs:  important general
2007-02-08 11:03:27.938 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:03:28.073 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-02-08 11:03:28.143 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:03:28.166 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-02-08 11:03:29.842 Reschedule requested for id -1.
2007-02-08 11:03:58.595 Scheduled 164 items in 28.8 = 27.82 match + 0.93 place
2007-02-08 11:03:58.602 Seem to be woken up by USER
2007-02-08 11:04:15.518 MainServer::HandleAnnounce Monitor
2007-02-08 11:04:15.523 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:04:15.524 MainServer::HandleAnnounce Monitor
2007-02-08 11:04:15.531 adding: Jason-Desktop as a client (events: 1)
2007-02-08 11:04:15.544 MainServer::HandleAnnounce Playback
2007-02-08 11:04:15.551 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:04:15.576 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:04:15.584 TVRec(2): HW Tuner: 2->2
2007-02-08 11:04:16.073 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:04:23.203 Finished recording Martha: channel 1004
2007-02-08 11:04:23.384 Finished recording Martha: channel 1004
0: start_time: 0.036 duration: 0.508
1: start_time: 0.026 duration: 0.488
stream: start_time: 0.289 duration: 5.750 bitrate=5747 kb/s
2007-02-08 11:04:23.410 AFD: Opened codec 0x6ad250, id(MPEG2VIDEO) type(Video)
2007-02-08 11:04:23.430 AFD: Opened codec 0x6ad6f0, id(MP2) type(Audio)
2007-02-08 11:04:23.470 TVRec(2): RingBufferChanged()
2007-02-08 11:04:23.479 Finished recording Martha: channel 1004
QSettings::sync: filename is null/empty
2007-02-08 11:04:27.201 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:04:27.264 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:04:27.692 MainServer::HandleAnnounce Playback
2007-02-08 11:04:27.696 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:04:27.697 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:04:27.704 TVRec(2): HW Tuner: 2->2
2007-02-08 11:04:27.905 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:04:34.087 MPEGRec(/dev/video1) Error: select timeout - ivtv driver has stopped responding
2007-02-08 11:04:43.423 Expiring Animal Miracles "Second Chance" from Thu Feb 8 10:00:00 2007, 15 MBytes, forced expire (LiveTV recording)
2007-02-08 11:04:43.428 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 11:04:43.428 Expiring Globe Trekker "Kenya" from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 11:04:43.429 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 48 MBytes, forced expire (LiveTV recording)
2007-02-08 11:06:07.310 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:06:43.544 Expiring Martha from Thu Feb 8 11:00:00 2007, 4 MBytes, forced expire (LiveTV recording)
2007-02-08 11:06:43.549 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 2 MBytes, forced expire (LiveTV recording)
2007-02-08 11:08:07.478 MainServer::HandleAnnounce Playback
2007-02-08 11:08:07.486 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:08:18.915 MainServer::HandleAnnounce Playback
2007-02-08 11:08:18.922 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:08:18.924 TVRec(1): Changing from None to WatchingLiveTV
2007-02-08 11:08:18.931 TVRec(1): HW Tuner: 1->1
2007-02-08 11:08:19.138 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:09:28.204 TVRec(1): Changing from WatchingLiveTV to None
2007-02-08 11:09:28.283 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:11:34.119 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-02-08 11:11:34.495 New DB connection, total: 1
2007-02-08 11:11:34.501 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:11:34.541 Current Schema Version: 1160
Starting up as the master server.
QSettings::sync: filename is null/empty
2007-02-08 11:11:34.652 New DB connection, total: 2
2007-02-08 11:11:34.653 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:11:34.716 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:11:34.770 New DB connection, total: 3
2007-02-08 11:11:34.795 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:11:35.139 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:11:35.352 New DB scheduler connection
2007-02-08 11:11:35.353 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:11:35.356 Main::Starting HttpServer
2007-02-08 11:11:35.408 Main::Registering HttpStatus Extension
2007-02-08 11:11:35.487 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-02-08 11:11:35.497 Enabled verbose msgs:  important general
2007-02-08 11:11:35.489 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:11:35.526 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-02-08 11:11:35.545 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-02-08 11:11:35.538 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:11:37.445 Reschedule requested for id -1.
2007-02-08 11:12:09.497 Scheduled 164 items in 32.1 = 30.64 match + 1.41 place
2007-02-08 11:12:09.505 Seem to be woken up by USER
2007-02-08 11:12:54.434 MainServer::HandleAnnounce Monitor
2007-02-08 11:12:54.437 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:12:54.438 MainServer::HandleAnnounce Monitor
2007-02-08 11:12:54.438 adding: Jason-Desktop as a client (events: 1)
2007-02-08 11:12:54.450 MainServer::HandleAnnounce Playback
2007-02-08 11:12:54.456 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:12:54.483 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:12:54.486 TVRec(2): HW Tuner: 2->2
2007-02-08 11:12:54.899 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 42 MBytes, forced expire (LiveTV recording)
2007-02-08 11:12:54.996 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:13:00.373 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:13:00.473 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:13:00.662 MainServer::HandleAnnounce Playback
2007-02-08 11:13:00.666 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:13:00.667 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:13:00.674 TVRec(2): HW Tuner: 2->2
QSettings::sync: filename is null/empty
2007-02-08 11:13:00.815 New DB connection, total: 4
2007-02-08 11:13:00.816 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:13:00.880 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:13:05.483 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:13:05.654 Finished recording Scrubs "My Occurrence": channel 1066
0: start_time: 0.036 duration: 0.282
1: start_time: 0.026 duration: 0.266
stream: start_time: 0.289 duration: 3.248 bitrate=5983 kb/s
2007-02-08 11:13:05.680 AFD: Opened codec 0x2aaaac3df0c0, id(MPEG2VIDEO) type(Video)
2007-02-08 11:13:05.698 AFD: Opened codec 0x2aaaac3df490, id(MP2) type(Audio)
2007-02-08 11:13:05.756 TVRec(2): RingBufferChanged()
2007-02-08 11:13:05.765 Finished recording Scrubs "My Occurrence": channel 1066
QSettings::sync: filename is null/empty
2007-02-08 11:13:08.038 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:13:08.090 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 11:13:08.382 MainServer::HandleAnnounce Playback
2007-02-08 11:13:08.386 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:13:08.387 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:13:08.390 TVRec(2): HW Tuner: 2->2
2007-02-08 11:13:08.587 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:13:14.193 MPEGRec(/dev/video1) Error: select timeout - ivtv driver has stopped responding
2007-02-08 11:13:15.095 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:13:22.299 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 11:13:22.309 MythSocket(6fa470:-1): writeStringList: Error, socket went unconnected.
2007-02-08 11:13:40.666 MainServer::HandleAnnounce Playback
2007-02-08 11:13:40.668 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:13:40.669 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:13:40.674 TVRec(2): HW Tuner: 2->2
2007-02-08 11:13:40.884 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:13:47.399 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:14:20.562 MainServer::HandleAnnounce Playback
2007-02-08 11:14:20.566 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:14:31.902 MainServer::HandleAnnounce Playback
2007-02-08 11:14:31.906 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:14:31.908 TVRec(1): Changing from None to WatchingLiveTV
2007-02-08 11:14:31.912 TVRec(1): HW Tuner: 1->1
2007-02-08 11:14:32.119 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:14:37.601 TVRec(1): Changing from WatchingLiveTV to None
2007-02-08 11:14:37.673 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:14:37.951 MainServer::HandleAnnounce Playback
2007-02-08 11:14:37.955 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:14:37.956 TVRec(1): Changing from None to WatchingLiveTV
2007-02-08 11:14:37.959 TVRec(1): HW Tuner: 1->1
2007-02-08 11:14:38.161 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:14:41.383 TVRec(1): Changing from WatchingLiveTV to None
2007-02-08 11:14:41.421 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:14:41.671 MainServer::HandleAnnounce Playback
2007-02-08 11:14:41.675 adding: Jason-Desktop as a client (events: 0)
2007-02-08 11:14:41.676 TVRec(1): Changing from None to WatchingLiveTV
2007-02-08 11:14:41.679 TVRec(1): HW Tuner: 1->1
2007-02-08 11:14:41.879 MPEGRec(/dev/video0) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:14:46.289 TVRec(1): Changing from WatchingLiveTV to None
2007-02-08 11:14:46.366 Finished recording Scrubs "My Occurrence": channel 1066
2007-02-08 11:14:55.018 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 2 MBytes, forced expire (LiveTV recording)
2007-02-08 11:14:55.023 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 2 MBytes, forced expire (LiveTV recording)
2007-02-08 11:14:55.023 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 11:14:55.024 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 0 MBytes, forced expire (LiveTV recording)
2007-02-08 11:15:43.234 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 11:15:43.243 TVRec(2): Changing from None to WatchingLiveTV
2007-02-08 11:15:43.245 TVRec(2): HW Tuner: 2->2
2007-02-08 11:15:43.452 MPEGRec(/dev/video1) Error: Error getting codec params using old IVTV ioctl
			eno: Bad address (14)
2007-02-08 11:15:43.488 TVRec(2): Changing from WatchingLiveTV to None
2007-02-08 11:15:44.066 Finished recording Mickey Blue Eyes: channel 1012
2007-02-08 11:15:44.074 MythSocket(2aaaac02a8d0:-1): writeStringList: Error, socket went unconnected.
2007-02-08 11:15:44.075 MythSocket(2aaaac42f5f0:-1): writeStringList: Error, socket went unconnected.
2007-02-08 11:19:57.912 Using runtime prefix = /usr
QSettings::sync: filename is null/empty
2007-02-08 11:19:58.340 New DB connection, total: 1
2007-02-08 11:19:58.361 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:19:58.396 Current Schema Version: 1160
Starting up as the master server.
QSettings::sync: filename is null/empty
2007-02-08 11:19:58.530 New DB connection, total: 2
2007-02-08 11:19:58.532 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:19:58.572 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:19:58.617 New DB connection, total: 3
2007-02-08 11:19:58.618 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:19:58.910 EITHelper: localtime offset -5:00:00 
QSettings::sync: filename is null/empty
2007-02-08 11:19:59.173 New DB scheduler connection
2007-02-08 11:19:59.184 Connected to database 'mythconverg' at host: localhost
2007-02-08 11:19:59.198 Main::Starting HttpServer
2007-02-08 11:19:59.260 Main::Registering HttpStatus Extension
2007-02-08 11:19:59.379 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-02-08 11:19:59.392 Enabled verbose msgs:  important general
2007-02-08 11:19:59.382 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:19:59.420 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-02-08 11:19:59.439 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-02-08 11:19:59.506 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-02-08 11:20:01.308 Reschedule requested for id -1.
2007-02-08 11:20:18.753 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 3 MBytes, forced expire (LiveTV recording)
2007-02-08 11:20:18.836 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 1 MBytes, forced expire (LiveTV recording)
2007-02-08 11:20:18.933 Expiring Scrubs "My Occurrence" from Thu Feb 8 11:00:00 2007, 2 MBytes, forced expire (LiveTV recording)
2007-02-08 11:20:18.987 Expiring Mickey Blue Eyes from Thu Feb 8 10:00:00 2007, 0 MBytes, forced expire (LiveTV recording)
2007-02-08 11:20:34.473 Scheduled 164 items in 33.2 = 26.83 match + 6.33 place
2007-02-08 11:20:34.488 Seem to be woken up by USER
```
That is the myth logs

---

### Post by wiz561 on 2007-02-08
Ahhh.  Finally!  Somebody else who has the same problem as me!!!!

I'm running Feisty, tried Edgy, and I still get the messages.  I've also tried the cvs and the stable version of ivtv (on edgy and dapper), and I would always get these messages.  I've also tried to disable powernowd and cpufreq, and even disable "cool 'n quiet" in the bios, but I still get those same messages.

Hopefully somebody can help!


Good Luck!!!

---

### Post by gearshifter on 2007-02-08
ah hell, ive had it for a while lol.  It's making me crazy.

edit:  Should we post a bug?  I've never posted one before but I'll back you up if you do!

edit2:  I have posted a bug report @ [https://launchpad.net/ubuntu/+source/ivtv/+bug/84105](https://launchpad.net/ubuntu/+source/ivtv/+bug/84105)


please respond if you have the same issues.

jason

---

### Post by superm1 on 2007-02-08
> **gearshifter said:**
> ah hell, ive had it for a while lol.  It's making me crazy.

edit:  Should we post a bug?  I've never posted one before but I'll back you up if you do!

edit2:  I have posted a bug report @ [https://launchpad.net/ubuntu/+source/ivtv/+bug/84105](https://launchpad.net/ubuntu/+source/ivtv/+bug/84105)


please respond if you have the same issues.

jason
Wiz this is your thread right? 

[http://www.gossamer-threads.com/lists/ivtv/users/34265](http://www.gossamer-threads.com/lists/ivtv/users/34265)

Could you download a feisty herd 3 disk and see if the issue is present in the newer kernel?  Ivtv is supposed to be supported out of the box as well.  You don't have to install the disk, just boot it, and you can do some basic testing with it.  Install myth on the disk if need be (you will need lots of RAM to do this though since the whole disk is loaded to memory).

---

### Post by wiz561 on 2007-02-08
Hi!

   Well, I posted a comment on the launchpad bugtraq page about it...hopefully others can see it as well.

    As far as Herd 3 goes, that is my latest experiment and it still exists on it.  Here is my kernel version...

Linux guido 2.6.20-6-generic #2 SMP Wed Jan 31 19:04:30 UTC 2007 x86_64 GNU/Linux

Here is my ivtv init strings...

Feb  8 18:58:46 guido kernel: [   24.736888] ivtv:  ==================== START INIT IVTV ====================
Feb  8 18:58:46 guido kernel: [   24.736893] ivtv:  version 0.9.1 (tagged release) loading
Feb  8 18:58:46 guido kernel: [   24.736895] ivtv:  Linux version: 2.6.20-6-generic SMP mod_unload 
Feb  8 18:58:46 guido kernel: [   24.736896] ivtv:  In case of problems please include the debug info between
Feb  8 18:58:46 guido kernel: [   24.736898] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Feb  8 18:58:46 guido kernel: [   24.736900] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Feb  8 18:58:46 guido kernel: [   25.285341] ivtv0: Autodetected Hauppauge card (cx23416 based)
Feb  8 18:58:46 guido kernel: [   25.935752] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Feb  8 18:58:46 guido kernel: [   26.136957] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
Feb  8 18:58:46 guido kernel: [   26.151376] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   26.229521] ivtv0: Autodetected Hauppauge WinTV PVR-150
Feb  8 18:58:46 guido kernel: [   26.229522] ivtv0: reopen i2c bus for IR-blaster support
Feb  8 18:58:46 guido kernel: [   26.229578] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
Feb  8 18:58:46 guido kernel: [   26.316640] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   26.462022] cx25840 3-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   29.379630] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   29.436740] ivtv0: Encoder revision: 0x02050032
Feb  8 18:58:46 guido kernel: [   29.436799] ivtv0: Registered device video1 for encoder MPEG
Feb  8 18:58:46 guido kernel: [   29.437017] ivtv0: Registered device video32 for encoder YUV
Feb  8 18:58:46 guido kernel: [   29.437239] ivtv0: Registered device vbi1 for encoder VBI
Feb  8 18:58:46 guido kernel: [   29.437399] ivtv0: Registered device video24 for encoder PCM audio
Feb  8 18:58:46 guido kernel: [   29.738138] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Feb  8 18:58:46 guido kernel: [   29.738155] ivtv:  ====================  END INIT IVTV  ====================

And here is a sample of what it looks like when it crashes...

Feb  7 11:00:45 guido kernel: [49876.939977] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:00:45 guido kernel: [49876.939985] ivtv0 warning: Failed api call 0x00000082 with result 0xfffffff0
Feb  7 11:00:45 guido kernel: [49876.939995] ivtv0 warning: ENC: Failed stopping capture -16
Feb  7 11:00:48 guido kernel: [49880.163531] ivtv0 warning: No Free Mailbox for cmd 0x000000db after 100 tries!
Feb  7 11:00:48 guido kernel: [49880.163538] ivtv0 warning: Mailbox[0] 0x000000dc flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163544] ivtv0 warning: Mailbox[1] 0x000000d9 flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163550] ivtv0 warning: Mailbox[2] 0x000000c9 flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163554] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x000000db!!!
Feb  7 11:00:51 guido kernel: [49883.391090] ivtv0 warning: No Free Mailbox for cmd 0x000000dc after 100 tries!
Feb  7 11:00:51 guido kernel: [49883.391098] ivtv0 warning: Mailbox[0] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391105] ivtv0 warning: Mailbox[1] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391111] ivtv0 warning: Mailbox[2] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391115] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x000000dc!!!
Feb  7 11:00:59 guido kernel: [49891.481956] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:00:59 guido kernel: [49891.481963] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:01:08 guido kernel: [49899.936929] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:01:08 guido kernel: [49899.936936] ivtv0 warning: Failed api call 0x000000c8 with result 0xfffffff0
Feb  7 11:01:08 guido kernel: [49899.936943] ivtv0 warning: init error 21. Code -16
Feb  7 11:01:16 guido kernel: [49908.207654] ivtv0 warning: 1000 ms time out waiting for firmware
<a bunch of these messages are repeated...>
Feb  7 11:06:41 guido kernel: [50233.138760] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:41 guido kernel: [50233.138768] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:06:49 guido kernel: [50241.329604] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:49 guido kernel: [50241.329611] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:06:58 guido kernel: [50249.496504] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:58 guido kernel: [50249.496511] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:06 guido kernel: [50257.587344] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:06 guido kernel: [50257.587351] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:14 guido kernel: [50265.614248] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:14 guido kernel: [50265.614255] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:22 guido kernel: [50273.757124] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:22 guido kernel: [50273.757131] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:30 guido kernel: [50281.792010] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:30 guido kernel: [50281.792017] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:33 guido kernel: [50285.115743] ivtv0 warning: No Free Mailbox for cmd 0x00000081 after 100 tries!
Feb  7 11:07:33 guido kernel: [50285.115753] ivtv0 warning: Mailbox[0] 0x000000d6 flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115758] ivtv0 warning: Mailbox[1] 0x000000dc flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115764] ivtv0 warning: Mailbox[2] 0x000000cd flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115768] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x00000081!!!
Feb  7 11:07:33 guido kernel: [50285.115771] ivtv0 warning: Error starting capture!
Feb  7 11:07:33 guido kernel: [50285.115774] ivtv0 warning: Failed to start capturing for stream 0

---

### Post by superm1 on 2007-02-08
> **wiz561 said:**
> Hi!

   Well, I posted a comment on the launchpad bugtraq page about it...hopefully others can see it as well.

    As far as Herd 3 goes, that is my latest experiment and it still exists on it.  Here is my kernel version...

Linux guido 2.6.20-6-generic #2 SMP Wed Jan 31 19:04:30 UTC 2007 x86_64 GNU/Linux

Here is my ivtv init strings...

Feb  8 18:58:46 guido kernel: [   24.736888] ivtv:  ==================== START INIT IVTV ====================
Feb  8 18:58:46 guido kernel: [   24.736893] ivtv:  version 0.9.1 (tagged release) loading
Feb  8 18:58:46 guido kernel: [   24.736895] ivtv:  Linux version: 2.6.20-6-generic SMP mod_unload 
Feb  8 18:58:46 guido kernel: [   24.736896] ivtv:  In case of problems please include the debug info between
Feb  8 18:58:46 guido kernel: [   24.736898] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Feb  8 18:58:46 guido kernel: [   24.736900] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Feb  8 18:58:46 guido kernel: [   25.285341] ivtv0: Autodetected Hauppauge card (cx23416 based)
Feb  8 18:58:46 guido kernel: [   25.935752] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Feb  8 18:58:46 guido kernel: [   26.136957] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
Feb  8 18:58:46 guido kernel: [   26.151376] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   26.229521] ivtv0: Autodetected Hauppauge WinTV PVR-150
Feb  8 18:58:46 guido kernel: [   26.229522] ivtv0: reopen i2c bus for IR-blaster support
Feb  8 18:58:46 guido kernel: [   26.229578] **WARNING** I2C adapter driver [ivtv i2c driver #0] forgot to specify physical device; fix it!
Feb  8 18:58:46 guido kernel: [   26.316640] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   26.462022] cx25840 3-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   29.379630] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #0)
Feb  8 18:58:46 guido kernel: [   29.436740] ivtv0: Encoder revision: 0x02050032
Feb  8 18:58:46 guido kernel: [   29.436799] ivtv0: Registered device video1 for encoder MPEG
Feb  8 18:58:46 guido kernel: [   29.437017] ivtv0: Registered device video32 for encoder YUV
Feb  8 18:58:46 guido kernel: [   29.437239] ivtv0: Registered device vbi1 for encoder VBI
Feb  8 18:58:46 guido kernel: [   29.437399] ivtv0: Registered device video24 for encoder PCM audio
Feb  8 18:58:46 guido kernel: [   29.738138] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
Feb  8 18:58:46 guido kernel: [   29.738155] ivtv:  ====================  END INIT IVTV  ====================

And here is a sample of what it looks like when it crashes...

Feb  7 11:00:45 guido kernel: [49876.939977] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:00:45 guido kernel: [49876.939985] ivtv0 warning: Failed api call 0x00000082 with result 0xfffffff0
Feb  7 11:00:45 guido kernel: [49876.939995] ivtv0 warning: ENC: Failed stopping capture -16
Feb  7 11:00:48 guido kernel: [49880.163531] ivtv0 warning: No Free Mailbox for cmd 0x000000db after 100 tries!
Feb  7 11:00:48 guido kernel: [49880.163538] ivtv0 warning: Mailbox[0] 0x000000dc flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163544] ivtv0 warning: Mailbox[1] 0x000000d9 flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163550] ivtv0 warning: Mailbox[2] 0x000000c9 flags 0x00000003
Feb  7 11:00:48 guido kernel: [49880.163554] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x000000db!!!
Feb  7 11:00:51 guido kernel: [49883.391090] ivtv0 warning: No Free Mailbox for cmd 0x000000dc after 100 tries!
Feb  7 11:00:51 guido kernel: [49883.391098] ivtv0 warning: Mailbox[0] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391105] ivtv0 warning: Mailbox[1] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391111] ivtv0 warning: Mailbox[2] 0x000000dc flags 0x00000003
Feb  7 11:00:51 guido kernel: [49883.391115] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x000000dc!!!
Feb  7 11:00:59 guido kernel: [49891.481956] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:00:59 guido kernel: [49891.481963] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:01:08 guido kernel: [49899.936929] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:01:08 guido kernel: [49899.936936] ivtv0 warning: Failed api call 0x000000c8 with result 0xfffffff0
Feb  7 11:01:08 guido kernel: [49899.936943] ivtv0 warning: init error 21. Code -16
Feb  7 11:01:16 guido kernel: [49908.207654] ivtv0 warning: 1000 ms time out waiting for firmware
<a bunch of these messages are repeated...>
Feb  7 11:06:41 guido kernel: [50233.138760] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:41 guido kernel: [50233.138768] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:06:49 guido kernel: [50241.329604] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:49 guido kernel: [50241.329611] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:06:58 guido kernel: [50249.496504] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:06:58 guido kernel: [50249.496511] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:06 guido kernel: [50257.587344] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:06 guido kernel: [50257.587351] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:14 guido kernel: [50265.614248] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:14 guido kernel: [50265.614255] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:22 guido kernel: [50273.757124] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:22 guido kernel: [50273.757131] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:30 guido kernel: [50281.792010] ivtv0 warning: 1000 ms time out waiting for firmware
Feb  7 11:07:30 guido kernel: [50281.792017] ivtv0 warning: Failed api call 0x000000b7 with result 0xfffffff0
Feb  7 11:07:33 guido kernel: [50285.115743] ivtv0 warning: No Free Mailbox for cmd 0x00000081 after 100 tries!
Feb  7 11:07:33 guido kernel: [50285.115753] ivtv0 warning: Mailbox[0] 0x000000d6 flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115758] ivtv0 warning: Mailbox[1] 0x000000dc flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115764] ivtv0 warning: Mailbox[2] 0x000000cd flags 0x00000003
Feb  7 11:07:33 guido kernel: [50285.115768] ivtv0 warning: Firmware UNRESPONSIVE when trying cmd 0x00000081!!!
Feb  7 11:07:33 guido kernel: [50285.115771] ivtv0 warning: Error starting capture!
Feb  7 11:07:33 guido kernel: [50285.115774] ivtv0 warning: Failed to start capturing for stream 0
Wow your on top of things with already testing on herd3 :)
I'm assuming this was a 64 bit build you tested.  Same problem exists on 32 bit?  
Also are you sure the card is physically fine?  As in properly inserted and all?  There was a post I came across that someone's PVR150 I2C didn't work.  He ended up having to shave off part of the metal bracket to make sure it made full contact with the PCI slot the way his case way laid out.

---

### Post by gearshifter on 2007-02-08
it was working fine on dapper for me, so i know its gotta be alright.  I had lirc working too but now lirc doesnt work with the latest kernel yet.

---

### Post by wiz561 on 2007-02-09
It was working fine on Dapper for me too.  I got a new HD card (KWorld ATSC-110) and it turned out that Dapper or ivtv didn't recognize the card.  So, I had to load up video4linux drivers because the latest of that did recognize the card.  After I loaded that up on Dapper, ivtv would crash when it would do the modprobe.  

I then read an article that the latest kernel has built in support for these cards.  So, I upgraded to Edgy, just to see if that would work in there.  It didn't.  So then, I went to the next step and jumped to Feisty.  The cards are both detected and working...somewhat.  I just get the firmware unresponsive message....but, I just live with it by rebooting.  Kind of a pain...but it is the best I could do with all versions of ubuntu.

I've also tried to switch PCI slots because somebody mentioned something about it.  That didn't help.  I ****MIGHT***** try to go back to Dapper this weekend, depending on how much patience I have (and time).  Somebody posted something that when you build video4linux, do a 'make ivtv' and it will compile the ivtv drivers into video4linux.  I think that was where my problem was existing.  But in order to do that, it would take a lot of time to rebuild everything.  So, I don't know what's going to happen....  Oh, also, ffmpeg kept crashing and running out of memory on Feisty.  I know this is OT, but that was another reason why I was thinking of jumping back.


Mike

---

### Post by gearshifter on 2007-02-11
how long do bugs take to get confirmed?  I know it probably takes some time for a bug fix but how many people do we need for it to be confirmed?

---

### Post by superm1 on 2007-02-11
> **gearshifter said:**
> how long do bugs take to get confirmed?  I know it probably takes some time for a bug fix but how many people do we need for it to be confirmed?
Well at this point there are newer packages available that just havent gotten built yet.  These need to be confirmed against the newer packages once they get built, and if they still occur against the newer packages - a bug filed upstream.  Thats the big hold up with the 24 bugs currently filed.

---

### Post by wiz561 on 2007-02-12
Alright.  I have a fix!  At least somewhat...

I took off Feisty and decided to go back to Edgy.  Granted, it wasn't the fix everybody was looking for....but it is working.  

In order to get it to work, I had to compile the kernel from kernel.org.  It's a pain in the butt, but I followed this page...

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Afterwards, I get this with uname...

Linux guido 2.6.19.3-custom-custom2 #1 SMP Sat Feb 10 22:37:05 CST 2007 x86_64 GNU/Linux

I installed ivtv version...

ivtv-0.9.1.tar.gz

From there, I'm able to use my Kworld card because it's being detected by video4linux.  And since it doesn't have ivtv already compiled in because it's the .19 kernel and not the .20 one, it doesn't get the FIRMWARE UNRESPONSIVE message that we all dread.

I've been using this now for about 2 days or so, and I have exit'ed and went back in numerous times.  I don't want to jinx anything, but so far, things are working great.  My next problem is the "NVP: Prebuffering Pause", but I'll save that for another day.

For those who had an AMD64 processor and are getting the "FIRMWARE UNRESPONSIVE" messages, I would highly recommend taking the time to compile the 2.6.19 kernel and install ivtv 0.9.1 as this seems to work well.

There was only one problem though.  When I was starting IVTV for the first time, I was getting some strange error about CMXsomething or other.  A google search turned up one link that says that when you compile the kernel, to disable something.  This web page explains it.

[http://www.gossamer-threads.com/lists/ivtv/users/34349](http://www.gossamer-threads.com/lists/ivtv/users/34349)

Hope this helps everybody out.

---

