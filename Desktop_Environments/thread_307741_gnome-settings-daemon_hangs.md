---
title: "gnome-settings-daemon hangs"
date: 2006-11-27
forum: Desktop Environments
---

### Post by haynold on 2006-11-27
Hi:

I have an odd problem with gnome-settings-daemon. When I try to start up, sometimes it works fine, but often it hangs, leaving me with a blank screen. I haven't found the conditions that make it work or fail--to me it appears random at this point.

In order to find out more, I have tried running gnome-settings-daemon from a terminal (without any of the other GNOME stuff running).

This is the result if nothing else runs:

```

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb77b87f8 in connect () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e96d99 in esd_close () from /usr/lib/libesd.so.0
#3  0xb7e97201 in esd_open_sound () from /usr/lib/libesd.so.0
#4  0xb7ea5b18 in gnome_config_get_int_with_default_ ()
   from /usr/lib/libgnome-2.so.0
#5  0xb7ea604b in gnome_sound_connection_get () from /usr/lib/libgnome-2.so.0
#6  0x0805a235 in gnome_settings_locate_pointer ()
#7  0x080559ea in gnome_settings_daemon_new ()
#8  0x080543c3 in main ()

```

If I try to make life a little easier for the daemon by starting esd before running gnome-settings-daemon, it still crashes thus:

```

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb76ee8c4 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb77847e8 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#3  0xb7784cb8 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb7bd3765 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0x080544a8 in main ()

```

Does anyone have an idea what's going on there?

Best,

     Oliver

---

### Post by haynold on 2006-11-30
Here's the solution:

The networking scripts somehow messes up network initialization, and lo isn't properly initialized. ifdown lo followed by ifup lo solves the problem.

---

