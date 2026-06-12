---
title: "Screen Lock Crashes...."
date: 2011-01-02
forum: Desktop Environments
---

### Post by SchneiderIS on 2011-01-02
I have a problem that is really making my Zotac MagHD-ND01 useless.  I had Ubuntu 10.04 installed on it and working great but I have since done a fresh install of 10.10 that is randomly (somewhat) flipping out to the screen lock.  When this happens the VNC server stops until I go to the box and press on my user name, enter my password, and then login again.  When I get back into the box though any applications, Thunar and the like, are all closed.  It is as if the desktop has crashed.

Thought it has happened randomly while using the machine as a MythTV frontend it appears to happen more consistently when I try to launch a new application.  It has happened when trying to launch Synaptic and when trying to run some of the setting applications.

Does anyone have any ideas on this one?  

The following are from my logs:

kern.log
```
Jan  2 09:37:12 FamillyRoom kernel: [46270.029989] mythfrontend.re[2193]: segfault at 35 ip 00007f50713dd4f3 sp 00007f505bffe748 error 4 in libQtCore.so.4.7.0[7f5071325000+28f000]
```

messages
```
Jan  2 07:58:56 FamillyRoom rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="799" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan  2 09:37:12 FamillyRoom kernel: [46270.029989] mythfrontend.re[2193]: segfault at 35 ip 00007f50713dd4f3 sp 00007f505bffe748 error 4 in libQtCore.so.4.7.0[7f5071325000+28f000]
```

daemon.log
```
Jan  2 09:37:10 FamillyRoom NetworkManager[825]: <error> [1293986230.593454] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:10 FamillyRoom acpid: client 1596[0:0] has disconnected
Jan  2 09:37:10 FamillyRoom acpid: client 1596[0:0] has disconnected
Jan  2 09:37:10 FamillyRoom acpid: client connected from 2397[0:0]
Jan  2 09:37:10 FamillyRoom acpid: 1 client rule loaded
Jan  2 09:37:10 FamillyRoom acpid: client connected from 2397[0:0]
Jan  2 09:37:10 FamillyRoom acpid: 1 client rule loaded
Jan  2 09:37:11 FamillyRoom NetworkManager[825]: <error> [1293986231.667565] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:11 FamillyRoom gnome-session[2419]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan  2 09:37:11 FamillyRoom gnome-session[2419]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: WARNING: Unable to lookup user name pschneid: Success
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 09:37:27 FamillyRoom gdm-session-worker[2435]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  2 09:37:33 FamillyRoom NetworkManager[825]: <error> [1293986253.411498] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:33 FamillyRoom NetworkManager[825]: <error> [1293986253.464710] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

syslog
```
Jan  2 09:37:10 FamillyRoom NetworkManager[825]: <error> [1293986230.593454] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:10 FamillyRoom acpid: client 1596[0:0] has disconnected
Jan  2 09:37:10 FamillyRoom acpid: client 1596[0:0] has disconnected
Jan  2 09:37:10 FamillyRoom acpid: client connected from 2397[0:0]
Jan  2 09:37:10 FamillyRoom acpid: 1 client rule loaded
Jan  2 09:37:10 FamillyRoom acpid: client connected from 2397[0:0]
Jan  2 09:37:10 FamillyRoom acpid: 1 client rule loaded
Jan  2 09:37:11 FamillyRoom NetworkManager[825]: <error> [1293986231.667565] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:11 FamillyRoom gnome-session[2419]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan  2 09:37:11 FamillyRoom gnome-session[2419]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan  2 09:37:12 FamillyRoom kernel: [46270.029989] mythfrontend.re[2193]: segfault at 35 ip 00007f50713dd4f3 sp 00007f505bffe748 error 4 in libQtCore.so.4.7.0[7f5071325000+28f000]
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: WARNING: Unable to lookup user name pschneid: Success
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 09:37:12 FamillyRoom gdm-simple-greeter[2431]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 09:37:27 FamillyRoom gdm-session-worker[2435]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  2 09:37:33 FamillyRoom NetworkManager[825]: <error> [1293986253.411498] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 09:37:33 FamillyRoom NetworkManager[825]: <error> [1293986253.464710] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

---

### Post by SchneiderIS on 2011-01-02
Just had the crash happen again and here is the new Syslog entries.

```
Jan  2 10:05:01 FamillyRoom NetworkManager[825]: <error> [1293987901.435027] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 10:05:01 FamillyRoom acpid: client 2397[0:0] has disconnected
Jan  2 10:05:01 FamillyRoom acpid: client 2397[0:0] has disconnected
Jan  2 10:05:01 FamillyRoom acpid: client connected from 2835[0:0]
Jan  2 10:05:01 FamillyRoom acpid: 1 client rule loaded
Jan  2 10:05:02 FamillyRoom acpid: client connected from 2835[0:0]
Jan  2 10:05:02 FamillyRoom acpid: 1 client rule loaded
Jan  2 10:05:02 FamillyRoom NetworkManager[825]: <error> [1293987902.996622] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 10:05:03 FamillyRoom gnome-session[2857]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan  2 10:05:03 FamillyRoom gnome-session[2857]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan  2 10:05:03 FamillyRoom gdm-simple-greeter[2869]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  2 10:05:03 FamillyRoom gdm-simple-greeter[2869]: WARNING: Unable to lookup user name pschneid: Success
Jan  2 10:05:03 FamillyRoom gdm-simple-greeter[2869]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 10:05:03 FamillyRoom gdm-simple-greeter[2869]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width 557 and height -3
Jan  2 10:05:24 FamillyRoom gdm-session-worker[2873]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  2 10:05:29 FamillyRoom NetworkManager[825]: <error> [1293987929.954712] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 10:05:30 FamillyRoom NetworkManager[825]: <error> [1293987930.11755] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  2 10:05:30 FamillyRoom NetworkManager[825]: <error> [1293987930.14501] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

It is looking to me like a possible networking issue.

---

### Post by SchneiderIS on 2011-01-02
I should note that the solution at: [http://ubuntuforums.org/showthread.php?t=1607867]("http://ubuntuforums.org/showthread.php?t=1607867") does not resolve my issue.  The same options are not available for my NVIDIA card.  It does though open the potential for this being a video driver configuration issue.

---

### Post by SchneiderIS on 2011-01-03
Bump.  Help please.

---

### Post by SchneiderIS on 2011-01-05
Bump Again.

I have submitted a bug but have not heard anything on it since the weekend.  Any help would be appreciated.

---

### Post by SchneiderIS on 2011-01-06
Ping?

---

### Post by wamarler on 2011-01-18
Hey SchneiderIS,

I wanted to let you know that you're not alone with this problem. The description you posted matches what I'm seeing *exactly*. 

Which bug did you file? I'd like to comment on it, add my own logs, etc. 

Were you able to attach a debugger to anything and get a stack trace or debugger output or the like? I want to do this myself, but I'm not entirely sure what to attach the debugger *to*. 

wam

---

### Post by SchneiderIS on 2011-01-18
> **wamarler said:**
> Hey SchneiderIS,

I wanted to let you know that you're not alone with this problem. The description you posted matches what I'm seeing *exactly*. 

Which bug did you file? I'd like to comment on it, add my own logs, etc. 

Were you able to attach a debugger to anything and get a stack trace or debugger output or the like? I want to do this myself, but I'm not entirely sure what to attach the debugger *to*. 

wam

Welcome to the game.

The bug identifier that I got was at the following URL: [https://bugs.launchpad.net/bugs/696995]("https://bugs.launchpad.net/bugs/696995")

In another forum I was told that it had to do with a conflict in VDPAU however when I switched to a Fedora based MythDora the problem disappeared.  This may be due to the fact that the Fedora version is also only 12 and not the latest and greatest.  Since I have heard absolutely nothing from the bug submission other than the number I don't hold hope on a speedy solution.

As for how to submit the bug I followed the instructions from the bug site on how to install the right packages and make the submission.  Sorry, I really don't remember the steps myself.

Good luck with it.  Since I have a solution with an alternate distribution I am sort of giving up on it.

---

### Post by wamarler on 2011-01-19
Can you link the forum where you found that it may be VDPAU-related?

---

