---
title: "notify osd"
date: 2014-04-28
forum: Desktop Environments
---

### Post by pfeiffep on 2014-04-28
I would like to stop the pop-up bubble message and sound when a new email arrives. I don't want to disable all pop-up bubbles - just email
I've found notify-osd is installed, the notification-daemon is located in /usr/lib,  but I didn't find a conf file ...> [INDENT]pfeiffep@pete-dell:/usr/share/notify-osd$ ls -al[/INDENT]
[INDENT]total 20[/INDENT]
[INDENT]drwxr-xr-x   3 root root  4096 Apr 16 21:24 .[/INDENT]
[INDENT]drwxr-xr-x 300 root root 12288 Apr 26 11:02 ..[/INDENT]
[INDENT]drwxr-xr-x   4 root root  4096 Apr 16 21:25 icons[/INDENT]

System Info:[INDENT]Ubuntu 14.04, gnome flashback, metacity
Intel celeron processor 1.5 Ghz
2 GB memory
40 GB hdd
Thunder Bird email client[/INDENT]

I would like to know how to configure notify-osd for this and other unforseen needs.

TIA for any suggestions

---

### Post by tgalati4 on 2014-04-28
The notification framework is deeply embedded in the operating system.  What mail program are you using?  Check that email program's preferences.  Each application handles calls to the notification daemon.  Your own scripts can call it as well:

```
man notify-send
```

Each application has a configuration file that controls how notifications are handled.  The notification daemon config file handles the placement and duration of the pop-ups, but not where they are coming from.

---

### Post by ian-weisser on 2014-04-28
You don't configure notify-osd at all.
You configure your mail client.

Notify-osd has no way to filter or block messages - it merely draws the bubble and fills it with content from the sending applications.

---

### Post by pfeiffep on 2014-04-28
Thank you both - I found the settings in Thunderbird
         Edit >> Preferences >> General >> When New Messages Arrive (2 check boxes)

---

