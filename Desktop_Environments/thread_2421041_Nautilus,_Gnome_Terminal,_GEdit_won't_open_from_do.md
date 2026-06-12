---
title: "Nautilus, Gnome Terminal, GEdit won't open from dock panel or activities"
date: 2019-06-15
forum: Desktop Environments
---

### Post by bab5470 on 2019-06-15
For some reason, (around when I upgraded to Ubuntu 18.04 **I THINK**), launching nautilus, gnome-terminal, or gedit from either the gnome dock panel or activities **sometimes** doesn't work. Let me elaborate.  

When I first reboot my machine I can open them from activities or the dock just fine, but after awhile, trying to launch them results in a swirly in the upper left hand corner but they never open. It looks like they are crashing based on seeing the processes appear and then disappear.

I can however open mate terminal and always launch `nautilus` or `gedit` but `gnome-terminal` fails with an error (I'll post that below). 

I have tried other file managers such as dolphin (which seems to work fine) but I would like to use nautilus. I've googled this issue until my fingers bled and the closest I can find is people saying they fixed the problem but they're not sure what they did to fix it (which obviously isn't super helpful). 

When I launch nautilus via mate terminal I do see some warnings/errors but I don't know if they are relevant:

```
Initializing nautilus-font-manager extension
Initializing nautilus-image-converter extension
sys:1: Warning: Two different plugins tried to register 'NautilusDiscBurn'.
sys:1: Warning: g_type_add_interface_dynamic: assertion 'G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

```
If I check my process list there's only ever a single nautilus process or gnome-terminal process running at any one time. 

As mentioned above, if I run gnome-terminal I also get the following warnings/errors:

```
# _g_io_module_get_default: Found default implementation gvfs (GDaemonVfs) for ‘gio-vfs’
# Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached

```
Running gedit via mate-terminal works without any errors at all. 

I repro'd the issue (attempting to open nautilus, then gnome-terminal then gedit) and here are the logs:

```
Jun 15 07:03:30 superman gnome-shell[3266]: g_environ_setenv: assertion 'value != NULL' failed
Jun 15 07:03:30 superman dbus-daemon[2839]: [session uid=1000 pid=2839] Activating service name='org.gnome.Nautilus' requested by ':1.37' (uid=1000 pid=3266 comm="/usr/bin/gnome-shell " label="unconfined")
Jun 15 07:03:30 superman dbus-daemon[2839]: [session uid=1000 pid=2839] Successfully activated service 'org.gnome.Nautilus'
Jun 15 07:03:30 superman org.gnome.Nautilus[2839]: Unable to init server: Could not connect: Connection refused
Jun 15 07:03:30 superman nautilus[23805]: cannot open display: :1001
Jun 15 07:03:44 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.UtrhA7.mount: Succeeded.
Jun 15 07:03:47 superman gnome-shell[3266]: g_environ_setenv: assertion 'value != NULL' failed
Jun 15 07:03:47 superman org.gnome.Shell.desktop[3266]: # _g_io_module_get_default: Found default implementation gvfs (GDaemonVfs) for ‘gio-vfs’
Jun 15 07:03:47 superman dbus-daemon[2839]: [session uid=1000 pid=2839] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.1033' (uid=1000 pid=24088 comm="/usr/bin/gnome-termina
Jun 15 07:03:47 superman systemd[2465]: Starting GNOME Terminal Server...
Jun 15 07:03:47 superman gnome-terminal-server[24091]: Unable to init server: Could not connect: Connection refused
Jun 15 07:03:47 superman gnome-terminal-server[24091]: Failed to parse arguments: Cannot open display:
Jun 15 07:03:47 superman systemd[2465]: gnome-terminal-server.service: Main process exited, code=exited, status=10/n/a
Jun 15 07:03:47 superman systemd[2465]: gnome-terminal-server.service: Failed with result 'exit-code'.
Jun 15 07:03:47 superman systemd[2465]: Failed to start GNOME Terminal Server.
Jun 15 07:03:50 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.Cb9nxx.mount: Succeeded.
Jun 15 07:03:50 superman systemd[2465]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.Cb9nxx.mount: Succeeded.
Jun 15 07:03:55 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.sNYGAa.mount: Succeeded.
Jun 15 07:03:55 superman systemd[2465]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.sNYGAa.mount: Succeeded.
Jun 15 07:04:00 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.YWhE0K.mount: Succeeded.
Jun 15 07:04:00 superman systemd[2465]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.YWhE0K.mount: Succeeded.
Jun 15 07:04:03 superman gnome-shell[3266]: g_environ_setenv: assertion 'value != NULL' failed
Jun 15 07:04:03 superman dbus-daemon[2839]: [session uid=1000 pid=2839] Activating service name='org.gnome.gedit' requested by ':1.37' (uid=1000 pid=3266 comm="/usr/bin/gnome-shell " label="unconfined")
Jun 15 07:04:03 superman dbus-daemon[2839]: [session uid=1000 pid=2839] Successfully activated service 'org.gnome.gedit'
Jun 15 07:04:03 superman org.gnome.gedit[2839]: Unable to init server: Could not connect: Connection refused
Jun 15 07:04:03 superman gedit[24349]: cannot open display: :1001
Jun 15 07:04:06 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.JleHYo.mount: Succeeded.
Jun 15 07:04:11 superman systemd[2465]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.q9E2JP.mount: Succeeded.
Jun 15 07:04:11 superman systemd[1]: run-docker-runtime\x2drunc-moby-d2719f3d00929e1f124ac5c15bfbeb7a8ec0bbbcc347f105eb3e00fa5539d690-runc.q9E2JP.mount: Succeeded.
Jun 15 07:04:12 superman org.gnome.Shell.desktop[3266]: # Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached
Jun 15 07:04:14 superman gnome-shell[3266]: Object Meta.Background (0x555d9e369ca0), has been already deallocated — impossible to access it. This might be caused by the object having been destroyed from C code using something such as dest
Jun 15 07:04:14 superman gnome-shell[3266]: g_object_run_dispose: assertion 'G_IS_OBJECT (object)' failed
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: == Stack trace for context 0x555d9bd7d200 ==
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #0   555daf0d2370 i   resource:///org/gnome/shell/ui/background.js:722 (7f34d8408430 @ 22)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #1   7ffdec996250 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (7f34d8ad0670 @ 54)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #2   7ffdec9963a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:342 (7f34d8ad0700 @ 1742)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #3   7ffdec996450 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:355 (7f34d8ad0790 @ 100)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #4   7ffdec9964e0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:370 (7f34d8ad0820 @ 10)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #5   7ffdec996560 I   resource:///org/gnome/gjs/modules/signals.js:128 (7f34d8acb820 @ 386)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #6   7ffdec996610 b   resource:///org/gnome/shell/ui/tweener.js:238 (7f34d8acb3a0 @ 159)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #7   7ffdec9966b0 b   resource:///org/gnome/shell/ui/tweener.js:209 (7f34d8acb280 @ 15)
Jun 15 07:04:14 superman gnome-shell[3266]: Object Meta.Background (0x555d9e369ca0), has been already deallocated — impossible to access it. This might be caused by the object having been destroyed from C code using something such as dest
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: == Stack trace for context 0x555d9bd7d200 ==
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #0   555daf0d23f8 i   resource:///org/gnome/shell/ui/background.js:722 (7f34d8408430 @ 22)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #1   555daf0d2370 i   resource:///org/gnome/shell/ui/tweener.js:106 (7f34d8ac8940 @ 37)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #2   7ffdec996250 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (7f34d8ad0670 @ 54)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #3   7ffdec9963a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:342 (7f34d8ad0700 @ 1742)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #4   7ffdec996450 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:355 (7f34d8ad0790 @ 100)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #5   7ffdec9964e0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:370 (7f34d8ad0820 @ 10)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #6   7ffdec996560 I   resource:///org/gnome/gjs/modules/signals.js:128 (7f34d8acb820 @ 386)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #7   7ffdec996610 b   resource:///org/gnome/shell/ui/tweener.js:238 (7f34d8acb3a0 @ 159)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #8   7ffdec9966b0 b   resource:///org/gnome/shell/ui/tweener.js:209 (7f34d8acb280 @ 15)
Jun 15 07:04:14 superman gnome-shell[3266]: g_object_run_dispose: assertion 'G_IS_OBJECT (object)' failed
Jun 15 07:04:14 superman gnome-shell[3266]: Object Meta.Background (0x555d9e369ca0), has been already deallocated — impossible to access it. This might be caused by the object having been destroyed from C code using something such as dest
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: == Stack trace for context 0x555d9bd7d200 ==
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #0   555daf0d23f8 i   resource:///org/gnome/shell/ui/background.js:722 (7f34d8408430 @ 22)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #1   555daf0d2370 i   resource:///org/gnome/shell/ui/tweener.js:106 (7f34d8ac8940 @ 37)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #2   7ffdec996250 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (7f34d8ad0670 @ 54)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #3   7ffdec9963a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:342 (7f34d8ad0700 @ 1742)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #4   7ffdec996450 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:355 (7f34d8ad0790 @ 100)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #5   7ffdec9964e0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:370 (7f34d8ad0820 @ 10)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #6   7ffdec996560 I   resource:///org/gnome/gjs/modules/signals.js:128 (7f34d8acb820 @ 386)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #7   7ffdec996610 b   resource:///org/gnome/shell/ui/tweener.js:238 (7f34d8acb3a0 @ 159)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #8   7ffdec9966b0 b   resource:///org/gnome/shell/ui/tweener.js:209 (7f34d8acb280 @ 15)
Jun 15 07:04:14 superman gnome-shell[3266]: g_object_run_dispose: assertion 'G_IS_OBJECT (object)' failed
Jun 15 07:04:14 superman gnome-shell[3266]: Object Meta.Background (0x555d9e10ed20), has been already deallocated — impossible to access it. This might be caused by the object having been destroyed from C code using something such as dest
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: == Stack trace for context 0x555d9bd7d200 ==
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #0   555daf0d23f8 i   resource:///org/gnome/shell/ui/background.js:722 (7f34d8408430 @ 22)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #1   555daf0d2370 i   resource:///org/gnome/shell/ui/tweener.js:106 (7f34d8ac8940 @ 37)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #2   7ffdec996250 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (7f34d8ad0670 @ 54)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #3   7ffdec9963a0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:342 (7f34d8ad0700 @ 1742)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #4   7ffdec996450 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:355 (7f34d8ad0790 @ 100)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #5   7ffdec9964e0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:370 (7f34d8ad0820 @ 10)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #6   7ffdec996560 I   resource:///org/gnome/gjs/modules/signals.js:128 (7f34d8acb820 @ 386)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #7   7ffdec996610 b   resource:///org/gnome/shell/ui/tweener.js:238 (7f34d8acb3a0 @ 159)
Jun 15 07:04:14 superman org.gnome.Shell.desktop[3266]: #8   7ffdec9966b0 b   resource:///org/gnome/shell/ui/tweener.js:209 (7f34d8acb280 @ 15)
Jun 15 07:04:14 superman gnome-shell[3266]: g_object_run_dispose: assertion 'G_IS_OBJECT (object)' failed

```



Immediately after a fresh reboot everything seems to work fine for awhile though. 

Has anyone else experienced this and/or do you have any pointers on things I could look at or try to fix this?

Thanks in Advance,
Brad

---

### Post by dino99 on 2019-06-15
Mixing DEs is always a trouble source.
Try first to clean the system:
- use genuine sources/packages
- install gtkorphan & bleachbit, then use them (bleachbit as root, carefully select items)

That suppose you also use (only) the default pathes/rights made at installation time.

---

### Post by bab5470 on 2019-06-15
I only installed mate-terminal as a last resort as I otherwise was stuck rebooting my entire box to open nautilus or gnome terminal otherwise. 

Likewise using dolphin file manager was done simply to test if some other file manager worked or if it had the same issues. 

Installing both of those applications was done *after* I started having issues though. 

(I'm not saying that running applications from different desktop environments isn't a source of the problem just pointing out that it was done after I started having trouble.) 

I'm trying gtkorphan and bleachbit and will follow up with results.

---

### Post by bab5470 on 2019-06-15
Running gtkorphan and bleachbit hasn't resolved the issue. Other ideas?

---

