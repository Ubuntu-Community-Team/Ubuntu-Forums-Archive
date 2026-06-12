---
title: "Nautilus crashing on specific folder on Windows share"
date: 2008-06-24
forum: Debian
---

### Post by Shakey_Jake33 on 2008-06-24
Running Debian Testing 64-bit. Trying to browse my other machines, and seems to work fine, except it crashes when browsing *specific* directories. As far as I can tell, there is nothing special about those directories (no special names or anything), but I did a complete reinstall of Debian and it crashes on those *same* directories.

Interestingly -

-Ubuntu LiveCD's Nautilus does NOT crash, it browses them fine.
-Konquorer browses them fine.

I don't know what could be causing this, I'll post the crash report: 

> Distribution: Debian lenny/sid
Gnome Release: 2.22.2 2008-05-29 (Debian)
BugBuddy Version: 2.22.0

System: Linux 2.6.24-1-amd64 #1 SMP Sat May 10 09:28:10 UTC 2008 x86_64
X Vendor: The X.Org Foundation
X Vendor Release: 10400090
Selinux: No
Accessibility: Disabled
GTK+ Theme: Clearlooks
Icon Theme: gnome

Memory status: size: 505868288 vsize: 505868288 resident: 32346112 share: 17502208 rss: 32346112 rss_rlim: 18446744073709551615
CPU usage: start_time: 1214303640 rtime: 234 utime: 218 stime: 16 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
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
[New Thread 0x2acaa4e7f220 (LWP 3471)]
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
0x00002aca9df56edf in waitpid () from /lib/libpthread.so.0
#0 0x00002aca9df56edf in waitpid () from /lib/libpthread.so.0
#1 0x00002aca9cf4d5a6 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2 0x00002aca9cf4d8b8 in g_spawn_command_line_sync ()
from /usr/lib/libglib-2.0.so.0
#3 0x00002acaa56364b3 in ?? ()
from /usr/lib/gtk-2.0/modules/libgnomebreakpad.so
#4 <signal handler called>
#5 0x000000000049be28 in ?? ()
#6 0x00002aca9cf0e28d in ?? () from /usr/lib/libglib-2.0.so.0
#7 0x000000000049efde in ?? ()
#8 0x000000000049f27a in ?? ()
#9 0x00002aca9c61fa69 in ?? () from /usr/lib/libgnomevfs-2.so.0
#10 0x00002aca9cf1a0f2 in g_main_context_dispatch ()
from /usr/lib/libglib-2.0.so.0
#11 0x00002aca9cf1d396 in ?? () from /usr/lib/libglib-2.0.so.0
#12 0x00002aca9cf1d657 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#13 0x00002aca9b600b63 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#14 0x000000000044028b in ?? ()
#15 0x00002aca9e1821c4 in __libc_start_main () from /lib/libc.so.6
#16 0x000000000042c569 in ?? ()
#17 0x00007fff11b73df8 in ?? ()
#18 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x2acaa4e7f220 (LWP 3471)):
#0 0x00002aca9df56edf in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1 0x00002aca9cf4d5a6 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#2 0x00002aca9cf4d8b8 in g_spawn_command_line_sync ()
from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3 0x00002acaa56364b3 in ?? ()
from /usr/lib/gtk-2.0/modules/libgnomebreakpad.so
No symbol table info available.
#4 <signal handler called>
No symbol table info available.
#5 0x000000000049be28 in ?? ()
No symbol table info available.
#6 0x00002aca9cf0e28d in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7 0x000000000049efde in ?? ()
No symbol table info available.
#8 0x000000000049f27a in ?? ()
No symbol table info available.
#9 0x00002aca9c61fa69 in ?? () from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#10 0x00002aca9cf1a0f2 in g_main_context_dispatch ()
from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0x00002aca9cf1d396 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0x00002aca9cf1d657 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0x00002aca9b600b63 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0x000000000044028b in ?? ()
No symbol table info available.
#15 0x00002aca9e1821c4 in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#16 0x000000000042c569 in ?? ()
No symbol table info available.
#17 0x00007fff11b73df8 in ?? ()
No symbol table info available.
#18 0x0000000000000000 in ?? ()
No symbol table info available.
#0 0x00002aca9df56edf in waitpid () from /lib/libpthread.so.0
The program is running. Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]


----------- .xsession-errors (12 sec old) ---------------------
Window manager warning: Failed to read saved session file /home/shakeyjake33/.metacity/sessions/default0.ms: Failed to open file '/home/shakeyjake33/.metacity/sessions/default0.ms': No such file or di
seahorse nautilus module initialized
Initializing gnome-mount extension
** (gnome-panel:3469): WARNING **: Failed to establish a connection with GDM: No such file or directory
** Message: <info> You are now connected to the wireless network 'sj33'.
kbuildsycoca running...
DCOP Cleaning up dead connections.
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
connection_message_func(): Callback
CALLBACK: fill-authentication!!!
** (nautilus:3471): WARNING **: No description found for mime type "x-directory/smb-share" (file is "D"), please tell the gnome-vfs mailing list. 

I'm actually having to use Vista for now, since I *need* to be able to access those shares.

---

