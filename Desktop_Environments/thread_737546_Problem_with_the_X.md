---
title: "Problem with the X"
date: 2008-03-27
forum: Desktop Environments
---

### Post by ladwinster on 2008-03-27
Hi. I'm running Ubuntu 7.10 and sometimes my X goes down and turns into the login screen. It's kind of annoying because when I doing works for univ it goes down :(


Anyone can help?

---

### Post by overdrank on 2008-03-27
> **ladwinster said:**
> Hi. I'm running Ubuntu 7.10 and sometimes my X goes down and turns into the login screen. It's kind of annoying because when I doing works for univ it goes down :(


Anyone can help?

Hi and welcome, what is the model of the graphics card and have you installed the drivers for it?

---

### Post by ladwinster on 2008-03-28
It's an Intel 915GM Expresse. My computer it's a HP nc6220

---

### Post by ladwinster on 2008-03-29
BUMP

I never had to install drivers for the graphics card....

---

### Post by mali2297 on 2008-03-29
Do you have desktop effects (Compiz Fusion) enabled?

In your home folder there is a hidden file called **.xsession-errors**. After X has gone down, look for any intelligible error messages in this file (ignore warnings and such).

---

### Post by ladwinster on 2008-03-29
Yes i'm using compiz.

Here it is what i got from that file

> (process:14276): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:14280): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/adwin-laptop:/tmp/.ICE-unix/14273
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Initializing gnome-mount extension


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
** Message: A não iniciar o servidor de área de trabalho remota
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 27570 1206835200 1206807630
evolution-alarm-notify-Message:  Sun Mar 30 00:00:00 2008

evolution-alarm-notify-Message:  Sat Mar 29 16:20:30 2008

alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Sun Mar 30 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/adwin/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/adwin/.evolution/calendar/local/system - Calendar Open Async... 0x80c9680
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80dd920
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/adwin/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/adwin/.evolution/tasks/local/system - Calendar Open Async... 0x80d99b0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/adwin/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/adwin/.evolution/memos/local/system - Calendar Open Async... 0x80e1120
alarm-notify.c:393 (cal_opened_cb) file:///home/adwin/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80c8490: Received at thread b4d32b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c9680
alarm-queue.c:581 (load_alarms_for_today) - From Sat Mar 29 16:20:34 2008
 to Sat Mar 29 16:20:34 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80c8490: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x80d1030: Received at thread b4d32b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80dd920
alarm-queue.c:581 (load_alarms_for_today) - From Sat Mar 29 16:20:34 2008
 to Sat Mar 29 16:20:34 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d1030: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/adwin/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e0498: Received at thread b4d32b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80e1120
alarm-queue.c:581 (load_alarms_for_today) - From Sat Mar 29 16:20:34 2008
 to Sat Mar 29 16:20:34 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e0498: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/adwin/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e0498:/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by ladwinster on 2008-03-30
anyone? Please help me with this.

---

### Post by mali2297 on 2008-03-30
Can you see any pattern in the events before X goes down? (Perhaps an app that you run.)

Try disabling Compiz for a while, does X still crash?

---

### Post by ladwinster on 2008-03-30
It crashed with Compiz disabled. The last time it crashed i was using Gedit... but I don't think it's because of it. I'm always using Gedit.

---

### Post by mali2297 on 2008-03-30
I'm sorry but I don't have solution for you. :-(

If no one else here comes to assistance, you may consider [filing a bug report.]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by ladwinster on 2008-03-30
:S 

ok Thanks anyway. I've removed compiz and so far it didn't crashed.... We will see.

---

