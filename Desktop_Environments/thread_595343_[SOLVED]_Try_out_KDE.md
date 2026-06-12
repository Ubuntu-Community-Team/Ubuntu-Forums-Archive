---
title: "[SOLVED] Try out KDE?"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Excalibre on 2007-10-28
I'm running Gutsy amd-64 and I'm wondering if there's an easy way to try out KDE (easier than, for instance, partitioning and installing Kubuntu in a spare partition.) I'll still have all my applications and so forth, right? I'm just wondering if I'll like it better since Gnome doesn't seem to be very configurable.

---

### Post by Baby Boy on 2007-10-28
Kubuntu LiveCD.

---

### Post by aysiu on 2007-10-28
Try this:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Excalibre on 2007-10-28
Okay, it's installed, but when I tried to start a KDE session, it told me it couldn't start kstartconfig (or something like that.) :confused:

---

### Post by Excalibre on 2007-10-28
Okay, so I went to this thread
[http://ubuntuforums.org/showthread.php?t=77729](http://ubuntuforums.org/showthread.php?t=77729)
to see how to get the KDE apps out of my gnome menus, and did it, and it seemed to work, but now after logging off and logging on again my whole menu is screwed up; there's like nothing in any of my menus.

I have a suspicion it has something to do with permissions because they seem to be screwed up but I don't know what it is or what to do.

Can anyone please help me?

---

### Post by Excalibre on 2007-10-28
And when I go into /usr/share/applications with Nautilus it doesn't know the size, type, date modified, permissions, etc, for anything.

WTF? Can anyone please help me?

---

### Post by Excalibre on 2007-10-28
Okay, never mind the menu thing. The permissions just got screwed up. I fixed them.

But about KDE - when I try to start it, it gives an error about kstartupconfig and output this error file:

```


(process:6790): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:6794): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
trying to create local folder /home/damon/.kde/share: Permission denied
trying to create local folder /home/damon/.kde/share: Permission denied
trying to create local folder /home/damon/.kde/share: Permission denied
SESSION_MANAGER=local/ursula:/tmp/.ICE-unix/6787
Checking for Xgl: not present. 
Initializing gnome-mount extension

(gnome-panel:6849): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (nautilus:6850): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6850): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6850): WARNING **: Can not get _NET_WORKAREA

** (nautilus:6850): WARNING **: Can not determine workarea, guessing at layout
Detected PCI ID for VGA: 01:00.0 0300: 10de:0421 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 85850 1193702400 1193616550
evolution-alarm-notify-Message:  Mon Oct 29 20:00:00 2007

evolution-alarm-notify-Message:  Sun Oct 28 20:09:10 2007

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Mon Oct 29 20:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/damon/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/damon/.evolution/calendar/local/system - Calendar Open Async... 0x6c7a40
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x6cc040
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/damon/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/damon/.evolution/tasks/local/system - Calendar Open Async... 0x6d9560
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/damon/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/damon/.evolution/memos/local/system - Calendar Open Async... 0x6ded20
alarm-notify.c:393 (cal_opened_cb) file:///home/damon/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/damon/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6c3620: Received at thread 41042950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6c7a40
alarm-queue.c:581 (load_alarms_for_today) - From Sun Oct 28 20:09:12 2007
 to Sun Oct 28 20:09:12 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) file:///home/damon/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6c3620: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6c21b0: Received at thread 41042950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6d9560
alarm-queue.c:581 (load_alarms_for_today) - From Sun Oct 28 20:09:12 2007
 to Sun Oct 28 20:09:12 2007

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6c21b0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6b16d0: Received at thread 41042950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6ded20
alarm-queue.c:581 (load_alarms_for_today) - From Sun Oct 28 20:09:12 2007
 to Sun Oct 28 20:09:12 2007

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6b16d0: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6dd950: Received at t  PID TTY          TIME CMD

```

---

### Post by TeaSwigger on 2007-10-28
The only errors I can understand in there are indeed due to permission issues. Can you think what was done which would've changed the permissions, and possibly of what and to what?

gksu nautilus --no-desktop to browse /usr/share/applications as it's likely and hopefully current "user" but do be sure you're careful in there.

---

### Post by Excalibre on 2007-10-28
When I mentioned permissions, I was talking about the momentary disappearance of my gnome menus after I ran a command from another thread to hide KDE applications from gnome. That's resolved.

But that was after I installed kubuntu-desktop anyway, and that didn't work from the get-go. When I looked at permissions on that .kde directory that it was having troubles with, only root has any permissions, but most of the hidden directories in my home directory are like that. Is that wrong? I can't think of anything that would have changed them; it must have been aptitude that created that directory anyhow. And shouldn't whatever process is trying to start KDE have root privileges anyway?

---

### Post by Excalibre on 2007-10-28
Okay, so I uninstalled kubuntu-desktop, killed that directory, reinstalled, and now it works.

I don't know how the permissions got screwed up but obviously I did something dumb. Never mind.

---

