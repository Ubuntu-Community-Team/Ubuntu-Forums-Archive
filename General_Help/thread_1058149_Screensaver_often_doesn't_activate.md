---
title: "Screensaver often doesn't activate"
date: 2009-02-02
forum: General Help
---

### Post by Lars Stokholm on 2009-02-02
More often than not my screensaver never activates and the screen never goes off. Sometimes it does, but mostly it doesn't. Why may that be?

Edit: Perhaps it might be relevant that my Visual Effects, under System > Preferences > Appearance, are set to None.

---

### Post by IronGiant on 2009-02-02
My first guess would be the driver for the video card. Have you tried removing the driver and reloading it?

---

### Post by Lars Stokholm on 2009-02-03
There's nothing listed under System > Administration > Hardware Drivers.

And my xorg.conf is empty!? :shock:

'xset dpms force off' is working fine...

---

### Post by IronGiant on 2009-02-03
What type of display adapter does your computer use!

---

### Post by Lars Stokholm on 2009-02-05
Where do I see that?

---

### Post by Lars Stokholm on 2009-03-06
Bump. Now I'm on new hardware (laptop as opposed to my desktop) and this is still a problem.

I found out that killing gnome-screensaver (*killall gnome-screensaver*) and starting it again will get rid of the problem **for a while**.

Unfortunately it doesn't last very long: I come and go to and from my machines; a few times in a row I return to find my screen black (which is fine), but eventually I will return and find that the screen is still 'on'. So I have to kill gnome-screensaver and start it again.

I've experienced this on two completely different machines - am I really the only one?

---

### Post by Lars Stokholm on 2009-03-06
I tried running gnome-screensaver --debug and here is the output when it goes wrong:> **[idle_timer] gs-watcher-x11.c:1115 (21:54:59):	 in idle timer**
[watcher_idle_notice_cb] gs-monitor.c:170 (21:54:59):	 Idle notice signal detected: 1
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:505 (21:54:59):	 Idle notice signal not handled: 1
[idle_timer] gs-watcher-x11.c:1115 (21:55:09):	 in idle timer
[watcher_idle_cb] gs-monitor.c:110 (21:55:09):	 Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:547 (21:55:09):	 Setting session idle: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:551 (21:55:09):	 Trying to set idle state when already idle
[_gs_watcher_set_session_idle] gs-watcher-x11.c:528 (21:55:09):	 Idle changed signal not handled: 1
[maybe_send_signal] gs-watcher-x11.c:1069 (21:55:09):	 Idle signal was not handled, restarting watcher
[gs_watcher_set_active] gs-watcher-x11.c:731 (21:55:09):	 turning watcher: OFF
[_gs_watcher_set_active_internal] gs-watcher-x11.c:714 (21:55:09):	 Stopping idle watcher
[gs_watcher_set_active] gs-watcher-x11.c:731 (21:55:09):	 turning watcher: ON
[_gs_watcher_set_active_internal] gs-watcher-x11.c:718 (21:55:09):	 Starting idle watcher
[power_timer] gs-watcher-x11.c:1080 (21:55:39):	 in power timer
[power_timer] gs-watcher-x11.c:1098 (21:55:39):	 Setting power notice elapsed: 30006
[watcher_power_notice_cb] gs-monitor.c:139 (21:55:39):	 Power notice signal detected: 1
[_gs_watcher_set_session_power_notice] gs-watcher-x11.c:478 (21:55:39):	 Changing power notice state: 1
**[idle_timer] gs-watcher-x11.c:1115 (21:59:59):	 in idle timer**
[watcher_idle_notice_cb] gs-monitor.c:170 (21:59:59):	 Idle notice signal detected: 1
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:505 (21:59:59):	 Idle notice signal not handled: 1
[idle_timer] gs-watcher-x11.c:1115 (22:00:09):	 in idle timer
[watcher_idle_cb] gs-monitor.c:110 (22:00:09):	 Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:547 (22:00:09):	 Setting session idle: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:551 (22:00:09):	 Trying to set idle state when already idle
[_gs_watcher_set_session_idle] gs-watcher-x11.c:528 (22:00:09):	 Idle changed signal not handled: 1
[maybe_send_signal] gs-watcher-x11.c:1069 (22:00:09):	 Idle signal was not handled, restarting watcher
[gs_watcher_set_active] gs-watcher-x11.c:731 (22:00:09):	 turning watcher: OFF
[_gs_watcher_set_active_internal] gs-watcher-x11.c:714 (22:00:09):	 Stopping idle watcher
[gs_watcher_set_active] gs-watcher-x11.c:731 (22:00:09):	 turning watcher: ON
[_gs_watcher_set_active_internal] gs-watcher-x11.c:718 (22:00:09):	 Starting idle watcher
[power_timer] gs-watcher-x11.c:1080 (22:00:39):	 in power timer
[power_timer] gs-watcher-x11.c:1098 (22:00:39):	 Setting power notice elapsed: 30003
[watcher_power_notice_cb] gs-monitor.c:139 (22:00:39):	 Power notice signal detected: 1
[_gs_watcher_set_session_power_notice] gs-watcher-x11.c:478 (22:00:39):	 Changing power notice state: 1And it goes on like this without the screen ever turning off. As you can see this is just a loop of all the same things happening again and again and again every five minutes (my idle time). What it should be doing is this:> **[idle_timer] gs-watcher-x11.c:1115 (20:52:21):	 in idle timer**
[watcher_idle_notice_cb] gs-monitor.c:170 (20:52:21):	 Idle notice signal detected: 1
[_gs_watcher_set_session_idle_notice] gs-watcher-x11.c:505 (20:52:21):	 Idle notice signal not handled: 1
[idle_timer] gs-watcher-x11.c:1115 (20:52:31):	 in idle timer
[watcher_idle_cb] gs-monitor.c:110 (20:52:31):	 Idle signal detected: 1
[gs_listener_set_session_idle] gs-listener-dbus.c:547 (20:52:31):	 Setting session idle: 1

[listener_check_activation] gs-listener-dbus.c:412 (20:52:31):	 Checking for activation
[gs_listener_update_console_kit_idle] gs-listener-dbus.c:296 (20:52:31):	 Updating ConsoleKit idle status: 1
[gs_listener_update_console_kit_idle] gs-listener-dbus.c:321 (20:52:31):	 [some dbus error removed by me]
[_gs_watcher_set_session_idle] gs-watcher-x11.c:524 (20:52:31):	 Changing idle state: 1That is what it says five minutes before the screen turns off successfully (my screen off time is ten minutes). What's the problem?

---

