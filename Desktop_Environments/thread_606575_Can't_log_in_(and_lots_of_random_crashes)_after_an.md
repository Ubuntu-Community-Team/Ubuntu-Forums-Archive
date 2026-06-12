---
title: "Can't log in (and lots of random crashes) after an update"
date: 2007-11-08
forum: Desktop Environments
---

### Post by wj32 on 2007-11-08
One time after logging I got the message "the Gnome Settings Daemon is not replying" or something. I also got a message saying "dbus blablabla". I thought alright, I'll just start gnome-settings-daemon myself. I did. During that session I installed all the updates that were available, as usual. I noticed as I was about to shut down several options were missing from the dialog. I couldn't Hibernate, and some other action was missing. Today I started up Ubuntu and logged in to find that my hard drive was going on and on. I waited for a while and then investigated. It turned out nautilus was using up 100% CPU. I killed it and checked nautilus-debug-log.txt. It contained around 1000 lines or so of "Caught signal 11" or something similar. Each line was written a few milliseconds after the previous line.

Then I tried the fail safe mode. I clicked "Options" on the login screen. The login screen crashed. Tried again. Crashed again. Eventually I got twm to run along with some xterms. I started synaptic. That didn't crash. I started gnome-settings-daemon. That didn't crash either. Then I started synaptic again. This time it crashed (segfault). I stopped gnome-settings-daemon. synaptic didn't segfault.

However, nearly all other GNOME apps segfault (gedit, evolution, etc.). Gnome-terminal doesn't segfault. I ran gdb on them. They ALL segfault because of a call to strcmp(). Here's the backtrace:

```

#0  0xb72a4028 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#1  0xb795b03c in _gtk_icon_cache_has_icon () from /usr/lib/libgtk-x11-2.0.so.0
#2  0xb7962ced in gtk_icon_theme_has_icon () from /usr/lib/libgtk-x11-2.0.so.0
#3  0xb78ae623 in gtk_action_group_add_actions_full ()
   from /usr/lib/libgtk-x11-2.0.so.0
#4  0xb78ae75e in gtk_action_group_add_actions ()
   from /usr/lib/libgtk-x11-2.0.so.0
#5  0x0809cb25 in ?? ()
#6  0x08225690 in ?? ()
#7  0x0814c820 in ?? ()
#8  0x0000001b in ?? ()
#9  0x08222838 in ?? ()
#10 0x08181b20 in ?? ()
#11 0xb7bb282c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#12 0x08222838 in ?? ()
#13 0x08181b20 in ?? ()
#14 0x0820e598 in ?? ()
#15 0x08222128 in ?? ()
#16 0xbfdf0698 in ?? ()
#17 0x080a12b3 in ?? ()
#18 0x08222838 in ?? ()
#19 0x0814ce6e in ?? ()
#20 0x00000000 in ?? ()

```

Can someone *please* help me? I have no idea why this is happening. I tried reinstalling gtk2, dbus, gconf2, and gnome-desktop-data. Nothing worked.

Some similar posts/reports:

[http://www.google.com/search?q=_gtk_icon_cache_has_icon+()+from+/usr/lib/libgtk-x11-2.0.so.]("http://www.google.com/search?q=_gtk_icon_cache_has_icon+()+from+/usr/lib/libgtk-x11-2.0.so.")

---

### Post by tschew on 2008-01-06
I have the same problem on a gutsy machine.

---

