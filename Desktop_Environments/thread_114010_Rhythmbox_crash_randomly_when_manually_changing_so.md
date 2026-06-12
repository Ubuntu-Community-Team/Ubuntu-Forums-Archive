---
title: "Rhythmbox crash randomly when manually changing song"
date: 2006-01-07
forum: Desktop Environments
---

### Post by jimbz on 2006-01-07
**Edit:** Solved: I had to disable the accessibility tools, this isn't a rhythmbox issue. Thanks anyway

Hi guys,

First, please forgive me for my poor english, I'm a french student and I'm still far short of the target (beautiful isn't it? ;-) )

So I've got a very very annoying problem with rhythmbox. Unlike many people who criticize it, I'w very fond of its interface and the way it works but...It is unusable for me! Although I've got a quite little collection (5gb) rhythmbox crash randomly when I manually change the playing song (ie by clicking on it) but there isn't any problem if I let it do all the work (even when shuffle). When I say randomly, I mean that sometimes I can change 2 or 3 times but one more and *crash*.

So now some precision about this crash:
 - It is a clean crash ;-) the process simply dye, without any bugbuddy alert.
 - This issue has appeared for me from the version 0.90 (I use 0.92 right now)
 - I planned to submit a backtrace but I didn't manage to run rhythmbox in gdb, see what I have:
```
jim@jim:~$ gdb rhythmbox
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run -d
Starting program: /usr/bin/rhythmbox -d
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226709312 (LWP 6983)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)

(rhythmbox:6983): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
(no debugging symbols found)
(no debugging symbols found)
GTK Accessibility Module initialized

(rhythmbox:6983): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible
[0x81307e8] [rb_debug_init] rb-debug.c:129 (22:22:04): Debugging enabled
[0x81307e8] [main] main.c:228 (22:22:04): initializing Rhythmbox 0.9.2
[0x81307e8] [main] main.c:236 (22:22:04): going to create Bonobo object
[0x81307e8] [main] main.c:247 (22:22:04): going to create DBus object
[0x81307e8] [main] main.c:302 (22:22:04): Going to create a new shell
(no debugging symbols found)
(no debugging symbols found)
[0x81307e8] [rb_shell_constructor] rb-shell.c:817 (22:22:05): Constructing shell[0x81307e8] [rb_shell_constructor] rb-shell.c:850 (22:22:05): creating database object
[New Thread -1229403216 (LWP 7001)]
[New Thread -1237795920 (LWP 7003)]
[0x81307e8] [rb_shell_constructor] rb-shell.c:882 (22:22:05): shell: setting up tray icon
[0x81307e8] [tray_destroy_cb] rb-shell.c:2199 (22:22:05): creating new tray icon[0x81307e8] [rb_tray_icon_init] rb-tray-icon.c:178 (22:22:05): setting up tray icon
[0x81307e8] [tray_destroy_cb] rb-shell.c:2209 (22:22:05): done creating new tray icon 0x82f17b8
[0x81307e8] [rb_shell_constructor] rb-shell.c:886 (22:22:05): shell: initializing shell services
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
[0x81307e8] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:1922 (22:22:06): setting playing source to (nil)
[0x81307e8] [rb_shell_player_stop] rb-shell-player.c:1975 (22:22:06): stopping
[0x81307e8] [rb_shell_player_sync_with_source] rb-shell-player.c:1771 (22:22:06): playing source: (nil), active entry: (nil)
[0x81307e8] [rb_header_sync] rb-header.c:524 (22:22:06): syncing with node = (nil)
[0x81307e8] [rb_header_sync] rb-header.c:596 (22:22:06): not playing
[0x81307e8] [rb_shell_player_sync_control_state] rb-shell-player.c:1491 (22:22:06): syncing control state
[0x81307e8] [rb_statusbar_sync_state] rb-statusbar.c:612 (22:22:06): syncing state
[0x81307e8] [rb_shell_constructor] rb-shell.c:957 (22:22:06): Audioscrobbler support enabled.
[0x81307e8] [rb_audioscrobbler_init] rb-audioscrobbler.c:228 (22:22:06): Initialising Audioscrobbler
[0x81307e8] [rb_audioscrobbler_init] rb-audioscrobbler.c:230 (22:22:06): Plugin ID: rbx, Version 0.9.2 (Protocol 1.1)
[0x81307e8] [rb_audioscrobbler_load_queue] rb-audioscrobbler.c:1137 (22:22:06): Loading Audioscrobbler queue from "/home/jim/.gnome2/rhythmbox/audioscrobbler.queue"

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1237795920 (LWP 7003)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1229403216 (LWP 7001)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1237795920 (LWP 7003)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1229403216 (LWP 7001)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1237795920 (LWP 7003)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.

Program received signal SIG33, Real-time event 33.
[Switching to Thread -1229403216 (LWP 7001)]
0xffffe410 in __kernel_vsyscall ()
(gdb) continue
Continuing.

```

And then nothing happened: I waited for a while and I couldn't see any disk/cpu activity so I had to "Ctrl-C"

 -This is what I have with --gst-debug-level=2
```
c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.015562000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.016136000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.017589000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.021949000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.025666000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.026110000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
WARN  (0x868a960 - 315741:53:44.030590000)       queue_dataflow(12643) gstqueue.c(711):gst_queue_chain:<preroll_audio_src0> preroll_audio_src0: waiting for the app to restart source pad elements
Erreur de segmentation
```

Thank you by advance, I hope you can help

Jim (Yes, English name but French man anyway ^^).

---

### Post by jimbz on 2006-01-08
Up! Please, please help me, it's really the only thing that prevent my ubuntu box from being perfect!

At least tell me where to ask my question if you can't answer, I don't think bugzilla to be the right place because I don't know exactly if it's rhythmbox related or not.

---

