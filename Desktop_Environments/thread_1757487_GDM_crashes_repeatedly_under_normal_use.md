---
title: "GDM crashes repeatedly under normal use"
date: 2011-05-13
forum: Desktop Environments
---

### Post by Lazaruss on 2011-05-13
Ever since installing Ubuntu 11.04, GDM/Unity has crashed and terminated every couple of times i use it. No record in dmesg, no idea how else to check up on it. Running kernel 2.6.38-9-generic.

Occurs under normal use/load, never noticed a specific factor that causes it.

---

### Post by aphatak on 2011-05-13
Any clues in /var/log, by any chance?

---

### Post by Lazaruss on 2011-05-13
```
May 13 18:10:16 sml-laptop gdm-simple-greeter[11363]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May 13 18:10:16 sml-laptop gdm-simple-greeter[11363]: WARNING: Unable to load CK history: no seat-id found
May 13 18:10:17 sml-laptop gdm-session-worker[11365]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 13 18:10:19 sml-laptop gdm-session-worker[11365]: pam_sm_authenticate: Called
May 13 18:10:19 sml-laptop gdm-session-worker[11365]: pam_sm_authenticate: username = [samuel]
```

That's all i could find related to gdm, trouble is i forget when exactly it happened, will have to make note next time

---

### Post by ryankask on 2011-05-14
The same error is occurring for me, causing GDM to about three or four times a day.

```
May 14 10:51:31 ryan-laptop gdm-simple-greeter[4509]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May 14 10:51:31 ryan-laptop gdm-simple-greeter[4509]: WARNING: Unable to load CK history: no seat-id found
May 14 10:51:33 ryan-laptop gdm-session-worker[4511]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 14 10:51:35 ryan-laptop gdm-session-worker[4511]: pam_sm_authenticate: Called
```

I see something similar in Launchpad but it's not really getting any attention. 

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540774](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540774)

---

### Post by Lazaruss on 2011-05-15
Yes, that entry in the log was the correct one, and yes, that bug is correct.

```
May 15 22:03:02 sml-laptop gdm-simple-greeter[25739]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May 15 22:03:02 sml-laptop gdm-simple-greeter[25739]: WARNING: Unable to load CK history: no seat-id found
May 15 22:03:04 sml-laptop gdm-session-worker[25741]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 15 22:03:07 sml-laptop gdm-session-worker[25741]: pam_sm_authenticate: Called
May 15 22:03:07 sml-laptop gdm-session-worker[25741]: pam_sm_authenticate: username = [samuel]
```

---

### Post by ktamm on 2011-06-15
Has anyone found a fix or workaround to this issue? I am having the same problems and its starting to drive me crazy.


Thanks!

---

### Post by Lazaruss on 2011-06-15
What programs do you run regularly? We must have something common here.

Usually, I have Chrome, Emesene, Skype and Spotify open.

---

### Post by ktamm on 2011-06-16
Chrome is really all I have open when it crashes. 

Sooo annoying when it happens.

---

### Post by Zapster on 2011-06-22
Same problem here with 10.10. GDM only crashes if chrome is running. Might be somehow chrome/chrome-plugin related. I'm using the daily ppa version.

EDIT: these post might be related
[http://ubuntuforums.org/showthread.php?t=1693116](http://ubuntuforums.org/showthread.php?t=1693116)
[http://ubuntuforums.org/showthread.php?t=1754687](http://ubuntuforums.org/showthread.php?t=1754687)

---

### Post by mauricep on 2011-06-25
I get exactly the same problem running Mint 11. I too use Chromium, and suspect that this might be the common point between us.

I thought that maybe the crash was from mounting USB devices or from Spideroak, but after your posts, I suspect Chromium.

---

### Post by petersielje on 2011-07-21
Got the same problem. Not using chromium. Intel graphics driver. Usually happens quickly after login when I first open a window, push alt+f2 or so. Does not happen too often and only during a short timespan after login.

```
Jul 20 21:26:17 xxx gdm-simple-greeter[2251]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Jul 20 21:26:17 xxx gdm-simple-greeter[2251]: WARNING: Unable to load CK history: no seat-id found
Jul 20 21:26:17 xxx gdm-simple-greeter[2251]: WARNING: Unable to parse history: (null)   42#012
Jul 20 21:26:17 xxx gdm-simple-greeter[2251]: WARNING: Unable to parse history: (null)   3#012
Jul 20 21:26:18 xxx gdm-session-worker[2253]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
```

---

### Post by walopower on 2011-08-23
Ubuntu 11.04 64bit. Same think, gnome logs out about 3 times/day. I rarely use anythink else than firefox, nautilus, Gimp, aMSN.
Graphic hardware: NVIDIA PCI-e 8600.

Syslog:
```

Aug 23 19:34:24 iwd gdm-simple-greeter[3566]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Aug 23 19:34:24 iwd gdm-simple-greeter[3566]: WARNING: Unable to load CK history: no seat-id found
Aug 23 19:34:28 iwd gdm-session-worker[3568]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 23 19:34:30 iwd gdm-session-worker[3568]: pam_sm_authenticate: Called

```

Also My laptop (11.04) Gnome hangs (not logs out), I can change tty and restart gdm, this happens also about 3 times/day. I have tested 2 installation. Have not investigated laptop yet, I will be back when I will find something.

Before 11.04 has not been anything like this since 6.06.
Only "special" program that I use both computers in startup is xgamma.
Both computers are same widgets (system state, netspeed, gnome sensors applet, clock).

---

### Post by royer10r on 2011-08-23
same here. hopefully this post goes through before it crashes again... 32 bit and 64 bit ubuntu
```


Aug 23 15:55:04 notyo-main gdm-simple-greeter[1041]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Aug 23 15:55:04 notyo-main NetworkManager[615]: <info> Scheduling stage 5
Aug 23 15:55:04 notyo-main NetworkManager[615]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 23 15:55:04 notyo-main NetworkManager[615]: <info> Done scheduling stage 5
Aug 23 15:55:04 notyo-main NetworkManager[615]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 23 15:55:04 notyo-main NetworkManager[615]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Aug 23 15:55:05 notyo-main NetworkManager[615]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Aug 23 15:55:05 notyo-main gdm-simple-greeter[1041]: WARNING: Unable to load CK history: no seat-id found
Aug 23 15:55:05 notyo-main NetworkManager[615]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Aug 23 15:55:05 notyo-main NetworkManager[615]: <info> Activation (eth0) successful, device activated.
Aug 23 15:55:05 notyo-main NetworkManager[615]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 23 15:55:05 notyo-main kernel: [   17.191426] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug 23 15:55:06 notyo-main gdm-session-worker[1044]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 23 15:55:11 notyo-main rtkit-daemon[1052]: Successfully made thread 1305 of process 1305 (n/a) owned by '1000' high priority at nice level -11.
Aug 23 15:55:11 notyo-main rtkit-daemon[1052]: Supervising 4 threads of 2 processes of 2 users.

```

---

### Post by royer10r on 2011-08-23
i have Chrome, Firefox, and Terminal/ssh windows open all the time. but that is it. the screen goes fuzzy all of the sudden while I'm working and does a hard reboot.

---

### Post by humbe76 on 2011-11-28
I have the same issue.. I seem to be running lucid from what I see in /etc/apt/sources.list

After I dist-upgraded last time I started getting problems of GDM crashing. Usually daily or more often.

I typically run a lot of terminals, firefox and thunderbird and I use virtual desktop and two monitors.

I use the command:

xrandr --output DVI-0 --mode 1920x1200 --pos 1920x0 --output VGA-0 --mode 1920x1200 --pos 0x0

in order to get my monitors set up (running it after X login as I'm unsure of where else to put it)

I have a virtual desktop available. Usually I think it crashes when I change virtual desktop. I have also seen it happen when I open new page in firefox.

Some output from logs:
> 
Nov 28 15:32:45 morgul gdm-session-worker[20786]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Nov 28 15:32:49 morgul gnome-session[20823]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)
Nov 28 15:32:49 morgul rtkit-daemon[1557]: Sucessfully made thread 20891 of process 20891 (n/a) owned by '1000' high priority at nice level -11.
Nov 28 15:32:49 morgul rtkit-daemon[1557]: Supervising 4 threads of 2 processes of 2 users.
Nov 28 15:32:49 morgul pulseaudio[20891]: pid.c: Stale PID file, overwriting.
Nov 28 15:32:49 morgul gnome-session[20823]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Failed to execute child process "tracker-applet" (No such file or directory)
Nov 28 15:32:49 morgul gnome-session[20823]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Failed to execute child process "trackerd" (No such file or directory)
Nov 28 15:32:49 morgul rtkit-daemon[1557]: Sucessfully made thread 20910 of process 20891 (n/a) owned by '1000' RT at priority 5.
Nov 28 15:32:49 morgul rtkit-daemon[1557]: Supervising 5 threads of 2 processes of 2 users.
Nov 28 15:32:50 morgul rtkit-daemon[1557]: Sucessfully made thread 20922 of process 20891 (n/a) owned by '1000' RT at priority 5.
Nov 28 15:32:50 morgul rtkit-daemon[1557]: Supervising 6 threads of 2 processes of 2 users.
Nov 28 15:32:50 morgul rtkit-daemon[1557]: Sucessfully made thread 20928 of process 20928 (n/a) owned by '1000' high priority at nice level -11.
Nov 28 15:32:50 morgul rtkit-daemon[1557]: Supervising 7 threads of 3 processes of 2 users.
Nov 28 15:32:50 morgul pulseaudio[20928]: pid.c: Daemon already running.
Nov 28 15:32:57 morgul pulseaudio[20891]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Nov 28 15:32:57 morgul pulseaudio[20891]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/morgul:@/tmp/.ICE-unix/20823,unix/morgul:/tmp/.ICE-unix/20823"): initialization failed.
Nov 28 15:33:48 morgul init: apport pre-start process (21682) terminated with status 1
Nov 28 15:33:48 morgul init: apport post-stop process (21683) terminated with status 1
Nov 28 15:33:51 morgul AptDaemon: INFO: Initializing daemon


I have a compaq nc6000 computer with ATI radeon gfx card.

Really hate this as it takes some time to set up the desktop again.

---

### Post by rhyshack on 2011-12-19
I had the same problem running 11.04 on a Fujitsu Lifebook A Series, Firefox browser. Then I noticed an entry in my dmesg which indicated it was overheating, so I blew out dust with compressed air, and it seems to have fixed the problem.

I hope this helps someone!! It's about my turn.

---

