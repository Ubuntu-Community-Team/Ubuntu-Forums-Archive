---
title: "gnome-system-monitor won't start"
date: 2008-08-03
forum: Desktop Environments
---

### Post by raziv on 2008-08-03
Hi all,

When first logging into a new session I am able to run the gnome-system-monitor application - no problem, but some time into the session, gnome-system-monitor refuses to start anymore. Logging out and in again solves this temporarily (it starts successfully), and then again after some time it refuses to start. Here's how it looks:

When I try to start the gnome-system-monitor from the menu, a "Starting System Monitor" box appears in the bottom panel, then dissapears, and nothing else happens.

When I try to start it from a terminal, the terminal hangs, without saying anything, and I have to close it forcefully through the "X" button.

The various log files that appear in the "System Log Viewer" (these are: auth.log, daemon.log, debug, messages, syslog, user.log and Xorg.0.log - I don't know any other ones to look in) don't show any relevant message.

I googled around and the only thing I could find is the GNOME_SYSTEM_MONITOR_DEBUG option. So I opened a new terminal, entered:
```

export GNOME_SYSTEM_MONITOR_DEBUG=1
gnome-system-monitor

```
, and what I got is :
```

** (gnome-system-monitor:28838): DEBUG: [0.457 procman.cpp:648 main] post gtk_init

```
, and then the terminal hung without (of course...) starting the system monitor.

Any suggestions?

Thanks in advance,
Raziv

---

### Post by raziv on 2008-08-10
err... bump? anyone?

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by AFarris01 on 2008-08-31
I'd love an answer to this problem, because the exact same thing is happening to me.  same output and everything:

andrew@BEC-LIN:~$ export GNOME_SYSTEM_MONITOR_DEBUG=1
andrew@BEC-LIN:~$ gnome-system-monitor
** (gnome-system-monitor:7710): DEBUG: [0.826 procman.cpp:648 main] post gtk_init

what the heck?

however for me, sometimes it wont work after my initial log in at all, and it also occasionally starts working spontaneously after being on for a while.  this is really bugging me, cause i like to frequently check running processes through that interface

---

### Post by AFarris01 on 2008-08-31
I just found this article that is of some interest to this particular problem.  it looks like a bug in the pearl library used in the gnome-system-monitor gtk.  here's the post for details:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463266](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463266)

supposedly its being fixed by the upstream gnome devs... anybody else have any more info?

---

### Post by raziv on 2008-11-05
> **AFarris01 said:**
> I just found this article that is of some interest to this particular problem.  it looks like a bug in the pearl library used in the gnome-system-monitor gtk.  here's the post for details:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463266](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463266)

supposedly its being fixed by the upstream gnome devs... anybody else have any more info?

I don't think it is the same problem since I don't get the error message described in that bug report.

Any other suggestion anyone? :confused:

---

### Post by r_sagarraju on 2010-01-09
I am unable to run Gnome system monitor either applet or command line....
If i try to run from applet nothing happens...
If i try it from command line this is what i get

```

(gnome-system-monitor:2551): WARNING **: SELinux was found but is not enabled.


GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted


```

After this I googled up..this thread came up and tried executing the code below.
```

export GNOME_SYSTEM_MONITOR_DEBUG=1
gnome-system-monitor

```
, and what I got is :
```

(gnome-system-monitor:2705): DEBUG: [1.103 procman.cpp:695 main] post gtk_init
** (gnome-system-monitor:2705): DEBUG: [1.112 procman.cpp:733 main] end init
** (gnome-system-monitor:2705): DEBUG: [1.123 smooth_refresh.cpp:68 load_gconf_value] smooth_refresh is enabled
** (gnome-system-monitor:2705): DEBUG: [1.123 procman.cpp:738 main] begin create_main_window
** (gnome-system-monitor:2705): DEBUG: [1.248 util.cpp:220 load_symbols] Found libselinux.so.1
** (gnome-system-monitor:2705): DEBUG: [1.248 util.cpp:236 load_symbols] Loaded getpidcon from libselinux.so.1
** (gnome-system-monitor:2705): DEBUG: [1.248 util.cpp:236 load_symbols] Loaded freecon from libselinux.so.1
** (gnome-system-monitor:2705): DEBUG: [1.248 util.cpp:236 load_symbols] Loaded is_selinux_enabled from libselinux.so.1

** (gnome-system-monitor:2705): WARNING **: SELinux was found but is not enabled.

** (gnome-system-monitor:2705): DEBUG: [1.260 load-graph.cpp:433 net_scale] bak 0 new_max 1024 pow2 10 coef10 1
** (gnome-system-monitor:2705): DEBUG: [1.260 load-graph.cpp:455 net_scale] rescale dmax = 0 max = 1 new_max = 1024
** (gnome-system-monitor:2705): DEBUG: [1.337 procman.cpp:740 main] end create_main_window
** (gnome-system-monitor:2705): DEBUG: [1.347 procman.cpp:756 main] begin gtk_main

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted


```

Any help would be really appreciated...
Thanks in advance..
Regards,
Sagar

---

