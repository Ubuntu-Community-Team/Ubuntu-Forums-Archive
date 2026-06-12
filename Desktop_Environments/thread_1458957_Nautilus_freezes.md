---
title: "Nautilus freezes"
date: 2010-04-20
forum: Desktop Environments
---

### Post by Anzan on 2010-04-20
I'm having some problems with Nautilus.

When it runs I get this error msg:

(nautilus:3314): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


When I right click on something, sometimes on the desktop, sometimes in Nautilus either the desktop icons will not respond or the Nautilus window freezes.

I've looked around in Configuration Editor for the preferences listed un the error message but cannot find anything.

Can anyone help please?

---

### Post by Anzan on 2010-04-20
Actually, even left-clicking doesn't work now.

---

### Post by Anzan on 2010-04-20
When it segfaults I get this message (running Nautilus from the terminal):

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::indent-expanders' of type `gboolean' from rc file value "((GString*) 0xa26fa80)" of type `GString'

---

### Post by Anzan on 2010-04-20
Now Nautilus won't start and I get this message:

(nautilus:3623): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


I found this through Google:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/454234)

but am unsure what to do.

---

### Post by Anzan on 2010-04-20
Fixed.

I had created an .svg file in Inkscape.

Nautilus could not recgnize it.

I rm it in terminal.

---

### Post by DavetheDude on 2010-04-26
Hi Anzan, 

I recently encountered this problem while using Inkscape. How did you know which file was causing the trouble?

Thanks

---

### Post by jjpcexpert on 2010-07-25
I'm debugging nautilus (need to go to the so-called software shop to get symbols) and getting the symbols. *AAARRRGGGHHHH Needs a stacktrace* This is a biggie for non-devs like me!

Latest non-stacktrace data:

```
 bash@~ $ gdb nautilus
(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e60b70 (LWP 3748)]
[Thread 0xb7e60b70 (LWP 3748) exited]

(nautilus:3745): Unique-DBus-WARNING **: Error while sending message: Did 
not receive a reply. Possible causes include: the remote application did 
not send a reply, the message bus security policy blocked the reply, the 
reply timeout expired, or the network connection was broken. (this error 
times two)

[New Thread 0xb7e60b70 (LWP 3759)]
[New Thread 0xb764cb70 (LWP 3760)]
[New Thread 0xb6e4bb70 (LWP 3761)]
[Thread 0xb7e60b70 (LWP 3759) exited]
[Thread 0xb764cb70 (LWP 3760) exited]
[Thread 0xb6e4bb70 (LWP 3761) exited]

Program exited normally.
```

What's funny, is that the same thing as above happened again! All the numbers were different though.

Backtrace news:
```
There isn't a stack.                # First run of GDB on Nautilus
/* Same thing again. No stack. */         # Second run
; On third run, taken a backtrace half way though (with the ^C)
; and it came out:
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x00d8fb86 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x00f6c13b in ?? () from /lib/libdbus-1.so.3
#3  0x00f640ef in ?? () from /lib/libdbus-1.so.3
#4  0x00f622cc in ?? () from /lib/libdbus-1.so.3
#5  0x00f4cba3 in ?? () from /lib/libdbus-1.so.3
#6  0x00f4f317 in ?? () from /lib/libdbus-1.so.3
#7  0x00f5ca51 in dbus_pending_call_block () from /lib/libdbus-1.so.3
#8  0x001b26df in ?? () from /usr/lib/libdbus-glib-1.so.2
#9  0x001b3142 in dbus_g_proxy_call () from /usr/lib/libdbus-glib-1.so.2
#10 0x001a184f in ?? () from /usr/lib/libunique-1.0.so.0
#11 0x0019e3f8 in unique_backend_send_message () from /usr/lib/libunique-
    1.0.so.0
#12 0x0019d557 in unique_app_send_message () from /usr/lib/libunique-
    1.0.so.0
#13 0x0806ecf8 in nautilus_application_startup (application=0x823b0f0, 
    kill_shell=0, no_default_window=0, 
    no_desktop=0, browser_window=0, geometry=0x0, urls=0x0) at nautilus-application.c:885
#14 0x08080dcf in main (argc=1, argv=0xbffff3f4) at nautilus-main.c:569
; That is a huge backtrace.
; After continuing after stopping when the first thread started:
; Non-stacktrace:
(gdb) continue
Continuing.

(nautilus:3895): Unique-DBus-WARNING **: Error while sending message: Did 
not receive a reply. Possible causes include: the remote application did 
not send a reply, the message bus security policy blocked the reply, the 
reply timeout expired, or the network connection was broken. ; times two

[Thread 0xb7e60b70 (LWP 3896) exited] 
[New Thread 0xb7e60b70 (LWP 3934)]
[New Thread 0xb764cb70 (LWP 3935)]
[New Thread 0xb6e4bb70 (LWP 3936)]
[Thread 0xb7e60b70 (LWP 3934) exited]
[Thread 0xb764cb70 (LWP 3935) exited]
[Thread 0xb6e4bb70 (LWP 3936) exited]

Program exited normally.

; The backtrace after that:
No stack

```
So obviously a sticky here.

---

### Post by legion1978 on 2011-09-17
if theres an inkscape autosave file on home directory, corrupted or whatever, nautilus locks on it and freezes.. rm on terminal does fix it.

u can tell cause it gets the "wait" icon from nautilus and then freezes.
hope it helps---

[edit] it will freeze *any* directory containing a corrupted or complex .svg file.. not sure which one is it cause the files does open in inkscape correctly.

---

### Post by didistortion on 2011-10-23
I had the same problem with some corrupted mp4 files. Nautilus freezes. I tried disabeling the preview option in Nautilus, but it still freezes. So I used VLC to find out which files where corrupted and deleted them accordingly. After that Nautilus works as supposed.

---

### Post by nothingspecial on 2011-10-23
This thread is old and ever so slightly moldy.

Closed

---

