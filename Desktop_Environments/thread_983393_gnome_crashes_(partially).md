---
title: "gnome crashes (partially)"
date: 2008-11-15
forum: Desktop Environments
---

### Post by argo82 on 2008-11-15
Hi!
I'm running 8.04 since a few months, but recently, gnome crashes basically daily after some time of running. It's not completely locking, First thing I usually notice is that when clicking on the Application bar, it doesn't open and the (Applications|Places|System) part of the bar becomes invisible. Applications that I start for example by shortcut on the desktop freeze on start (like the Gnome terminal emulator) or run slowly (movie player). One thing that occurs always on these "crashes" is that I don't have sound any more.
As far as I remember, this happened always after using firefox, mostly after viewing some flash movie and then closing it. It doesn't necessarily coincide with firefox crashing.

As there is no application bar to log out, I use ctrl-alt-backspace to restart the x server. But while I can enter username and password, login in doesn't work, I only see a blank wallpaper.
Switching to another terminal works. I can't see any significant cpu/memory usage in top and I don't really now what I can do to find the cause of the problem.

I post some lines of the system logs, I noticed the strange behavior of the system at around 22:30. The logs are taken before restarting the x server or doing anything else.

syslog:
> 
Nov 15 21:10:15 SUNSHINE dhclient: bound to [removed] -- renewal in 1701 seconds.
Nov 15 21:17:02 SUNSHINE /USR/SBIN/CRON[4717]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 15 21:38:36 SUNSHINE dhclient: DHCPREQUEST of <null address> on eth0 to [removed] port 67
Nov 15 21:38:36 SUNSHINE dhclient: DHCPACK of [removed] from [removed]
Nov 15 21:38:36 SUNSHINE dhclient: bound to [removed]-- renewal in 1644 seconds.
Nov 15 21:38:36 SUNSHINE NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Nov 15 22:06:00 SUNSHINE dhclient: DHCPREQUEST of <null address> on eth0 to [removed] port 67
Nov 15 22:06:00 SUNSHINE dhclient: DHCPACK of [removed] from [removed]
Nov 15 22:06:00 SUNSHINE dhclient: bound to [removed] -- renewal in 1677 seconds.
Nov 15 22:06:00 SUNSHINE NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Nov 15 22:17:01 SUNSHINE /USR/SBIN/CRON[6924]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 15 22:21:26 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 22:21:26 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:22:44 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 22:22:44 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:22:50 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:33:57 SUNSHINE dhclient: DHCPREQUEST of <null address> on eth0 to [removed] port 67
Nov 15 22:33:57 SUNSHINE dhclient: DHCPACK of [removed] from [removed]
Nov 15 22:33:57 SUNSHINE dhclient: bound to [removed] -- renewal in 1488 seconds.
Nov 15 22:33:57 SUNSHINE NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 


user.log
> 
Nov 15 20:49:27 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 20:49:39 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 20:49:39 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 20:49:41 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 20:49:41 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 20:49:57 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 20:49:57 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 20:50:07 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 20:50:07 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 21:01:00 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 21:01:00 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 21:01:05 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 21:01:05 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 21:01:20 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 21:01:20 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:21:26 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 22:21:26 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:22:44 SUNSHINE pulseaudio[6671]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Nov 15 22:22:44 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.
Nov 15 22:22:50 SUNSHINE pulseaudio[6671]: sink-input.c: Failed to create sink input: too many inputs per sink.

In messages, I just have the same pulseaudio error.
In Xorg.0.log there is no error at all, just a warning about my keyboard layout or so.

Can it be related to that pulseaudio thing? I get these messages all the time though, also when the system runs normally. What other logs may be interesting to look at in this case? I'm not experienced in this regard.

Thanks for any help!
argo

---

