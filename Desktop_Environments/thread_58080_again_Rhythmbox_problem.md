---
title: "again Rhythmbox problem"
date: 2005-08-18
forum: Desktop Environments
---

### Post by giopas on 2005-08-18
Hi!

I've a question about Rhythmbox for you:  :)
I've altready read all past 3ds about the problem, but I didn't solve it.

I've got, on an External HD (FAT32), more than 100Gb of music organized - in the past (but, until I won't be able to solve this problem, still in the present  :|  ) - with iTunes for Windows. I let you imagine: more than 1000 folders, and a lot of different files' formats (mp3, waw, ogg, m4a, jpg, tiff, txt, etc...) that are impossible even to browse!

I tryed to import all that stuff in Rhythmbox, but after some minutes it always craches.
I don't know what is the problem: maybe too much music? or some unknown file format?

How can I fix that problem?

I've though to upgrade to the last (unstable) Rhythmbox GUI (taking it from Breezy repositories), but there are to much dependencies to upgrade, so I think it would be quite dangerous for the stability of my desktop...

Let me know, plz!

enjoy, ;)
giopas

---

### Post by giopas on 2005-08-19
Hi!

I tryed to lunch Rhythmbox from the root terminal, typing "Rhythmbox -d". This is what I discovered (I report just the end of all the process, that has taken more than one hour):

```
[0x8149b58] [rb_metadata_load] rb-metadata-gst.c:477 (02:02:18): loading metadata for uri: file:///media/EXTERNAL HD/Archivio Musicale/Music%20Guy%2CBram%2CStephan/R%C3%A9pondeur/Unknown%20Album/Big%20Teuf.mp3
[0x8149b58] [rb_metadata_gst_typefind_cb] rb-metadata-gst.c:430 (02:02:18): found type application/x-id3
[0x80ebe18] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:556 (02:02:18): entryview changed
[0x80ebe18] [rb_shell_clipboard_sync] rb-shell-clipboard.c:364 (02:02:18): syncing clipboard
[0x80ebe18] [rb_shell_player_entry_view_changed_cb] rb-shell-player.c:1515 (02:02:18): entry view changed
[0x80ebe18] [rb_shell_player_sync_buttons] rb-shell-player.c:1684 (02:02:18): syncing with source 0x82e7b68
[0x80ebe18] [rb_shell_player_set_play_button] rb-shell-player.c:1577 (02:02:18): setting play button
[0x80ebe18] [rb_statusbar_entry_view_changed_cb] rb-statusbar.c:582 (02:02:18): entry view changed
[0x80ebe18] [rb_playlist_manager_save_playlists] rb-playlist-manager.c:599 (02:02:20): saving the playlists
[0x80ebe18] [rb_playlist_manager_save_playlists] rb-playlist-manager.c:602 (02:02:20): no save needed, ignoring
Segmentation fault
```

Any idea? Plz!

enjoy,
giopas

---

### Post by giopas on 2005-08-19
Doh!!!   ](*,) 

I just realized that I wrote in a wrong section: I use Hoary 5.04!!!

sorry mods, can you kindly move this 3d in the right section,please (and cancel this post)? :-# 

enjoy, ;)
giopas

---

### Post by doclivingston on 2005-08-19
First, I wouldn't run rhythmbox on a root terminal - just running it from a normal one should be fine.


That debug log doesn't show anything odd, it's saying it loaded some files sucessfully and then crashed.

If you have gdb installed can you open a terminal and run "gdb rhythmbox" and then "continue", attempt import your music into Rhythmbox, when it crashes it will freeze rather than exiting. Go back to the terminal where gdb should have stopped and type "thread apply all bt" and copy the output here. That should help determine why it's crashing.

If you don't have gdb installed you can install it via "apt-get install gdb" or with synaptic.

---

### Post by giopas on 2005-08-19
Thnx doclivingston!

I'm trying to run "gdb rhythmbox" in a terminal and typing after "continue", but it doesn't work. I tryed even running Rhythmbox before and after "gdb rhythmbox", but it seems not working.

I'm very a newbye, can you tell me better what have I to do...  :-| 

This is wht the terminal says:
```
giopas@ubuntu:~$ gdb rhythmbox
GNU gdb 6.3-debian
Copyright 2004 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i386-linux"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) continue
The program is not being run.
```

I really wonder if you can help me fix this problem, and finally enjoy with Rhythmbox!

enjoy, ;)
giopas

---

### Post by doclivingston on 2005-08-19
Sorry, my brain isn't fully awake yet - that should be "run" not "continue".

---

### Post by giopas on 2005-08-19
no problem! ;)

I'm waiting for all the process... I'll edit this post writing the result!

thnx a lot!
giopas

---

### Post by giopas on 2005-08-19
Here the bug report is.
```
(rhythmbox:8937): GLib-GObject-WARNING **: gvalue.c:89: cannot initialize GValue with type `gchararray', the value has already been initialized as `gchararray'

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1237595216 (LWP 8943)]
0xb76a52e2 in gst_debug_log_default () from /usr/lib/libgstreamer-0.8.so.1
(gdb) thread apply all bt

Thread 10 (Thread -1281086544 (LWP 8962)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb747200e in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb79404fd in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#3  0xb794053e in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#4  0xb742b362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
#5  0xb746fae0 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7394c9a in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread -1280820304 (LWP 8961)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb747200e in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb79404fd in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#3  0xb794053e in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#4  0xb742b362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
#5  0xb746fae0 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
---Type <return> to continue, or q <return> to quit---
#6  0xb7394c9a in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread -1280554064 (LWP 8960)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb747200e in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb79404fd in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#3  0xb794053e in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
#4  0xb742b362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
#5  0xb746fae0 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb7394c9a in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread -1263055952 (LWP 8946)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb738c549 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb74138de in g_main_loop_get_context () from /usr/lib/libglib-2.0.so.0
#3  0xb7412f57 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#4  0xb741351e in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#5  0xb751af28 in link_thread_io_context () from /usr/lib/libORBit-2.so.0
#6  0xb746a398 in ?? () from /usr/lib/libglib-2.0.so.0
#7  0xb4b74ad8 in ?? ()
---Type <return> to continue, or q <return> to quit---
#8  0xb742b362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
Previous frame inner to this frame (corrupt stack?)
#0  0xb76a52e2 in gst_debug_log_default () from /usr/lib/libgstreamer-0.8.so.1
(gdb)
```

what does it means? :(

enjoy, ;)
giopas

---

### Post by doclivingston on 2005-08-19
Hmm... that stack trace doesn't help over much, but the gst_debug_log_default() at the end makes me think there may be a gstreamer problem.

Can you try "rhythmbox --gst-debug-level=2" and see what it prints out before it crashes?

---

### Post by giopas on 2005-08-19
ok

EDIT: during the loading/debugging process, Rhythmbox has displayed an error (in a separate Rhythmbox window), saying that is "impossible to determinate the stream type" of a certain mp3 file.

After the result of the new debug, i can move that file out the music folder.

giopas

---

### Post by giopas on 2005-08-19
here the other bug report:

```
WARN  (0x82a27f8 - 312348:07:03.123296000)  GST_SCHEDULING(10126) gstpad.c(3224):_invent_event: needed to invent a DISCONT 0x9480c08 (no time) for id3demux10006:src => typefindelement10006:sink
WARN  (0x82a27f8 - 312348:07:03.256983000)        typefind(10126) gsttypefindelement.c(400):stop_typefinding:<typefindelement10006> could not seek to required position 52129, hope for the best
Segmentation fault
```

thnx again!

enjoy, ;)
giopas


EDIT: take a look at the Edit of the precedent message.

---

### Post by doclivingston on 2005-08-19
The "impossible to determinate the stream type" message means that Gstreamer can't decode that particular file, it may be either be corrupted or fixed in newer versions of gst-plugins. Can other music applications read that file?

Of the GStreamer debug output, don't worry about the DISCONT thing, that is normal. I'm not sure about the "typefind/could not seek" message, I know a bit about GStreamer, but I'm not an expert.


Back in your original message is a reference to "file:///media/EXTERNAL HD/Archivio Musicale/Music Guy%2CBram%2CStephan/R%C3%A9pondeur/Unknown Album/Big Teuf.mp3"; either that file or one of the ones it is trying to load after it is causing GStreamer to crash. My suggestion if to temporarily move all of the tracks out of that folder and see if you can import everything else. If that works, put the tracks that were in there back one at a time, importing between each, to find out which one is causing the crash.

Once you've figured out which one is doing it, it might be worth filing a bug report and attaching that particular track.

---

### Post by giopas on 2005-08-19
I've taken out all that files that were refused by rhythmbox.
Now, I've started a new debug, and this is the answer:
>  (rhythmbox:10201): GLib-GObject-WARNING **: gvalue.c:89: cannot initialize GValue with type `gchararray', the value has already been initialized as `gchararray'


EDIT: I tryed to run rhythmbox in debug mode but twice it has not finished it, because the entire system has frozen. That's strange...  :roll: 

Any idea or solution? PLZ

enjoy, ;)
giopas

---

### Post by doclivingston on 2005-08-20
The issue that is causing that warning shouldn't really be a problem (hopefully).

I have no idea why your system is locking up; Rhythmbox shouldn't be able to cause something like that, unless it's triggering a hardware issue that only shows up under intensive cpu/memory usage (which importing tracks is).


Sorry I'm not much more help, all the problems I've seen importing tracks are usually due to GStreamer not liking the file (and sometimes crashing due to a bug in gstreamer).

---

### Post by giopas on 2005-08-20
thnx anyway, doclivingston, I think I'll wait the next Rhythmbox release...

I also tryed to install Itunes with CrossOver Office, but I can't ear any sound even if it runs...

Have you got any other mp3 player like iTunes/Rhythmbox suggestion?

enjoy, ;)
giopas

---

### Post by doclivingston on 2005-08-20
[QUOTE=giopas]thnx anyway, doclivingston, I think I'll wait the next Rhythmbox release...[/quote]

0.9.0 is out, but it hasn't been backported to Hoary yet (there is a request in the backport section though) because it requires totem 1.1.3 which hasn't been backported.

[QUOTE=giopas]I also tryed to install Itunes with CrossOver Office, but I can't ear any sound even if it runs...

Have you got any other mp3 player like iTunes/Rhythmbox suggestion?[/QUOTE]

I don't know of any that are particularly close, but quite a few people like Muine (although it requires mono).

---

