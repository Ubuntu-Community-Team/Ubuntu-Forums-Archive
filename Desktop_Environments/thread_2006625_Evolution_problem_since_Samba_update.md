---
title: "Evolution problem since Samba update"
date: 2012-06-19
forum: Desktop Environments
---

### Post by chinleybrewer on 2012-06-19
I'm using Xubuntu 12.04 64bit.

Since this morning I have a problem with Evolution mail.  If I run it I can view emails in different folders fine but if for example I try to expunge the trash folder, it locks up requiring a Kill.  Same thing if I try to send mail or receive mail.

It could be coincidence but this morning the following upgrades were carried out:
libsmbclient
libswscale2
libpam-winbind
libavutil51
smbclient
libbclient0
libavcodec53
samba-common
libpostproc52
samba
libavformat53
samba-common-bin
winbind

If I use Task Manager, what I see is lots of lines of:
/usr/lib/gvfs/gvfsd-smb --spawner :1.9 /org/gtk/gvfs/exec_spaw/?
where ? is a number

My limited understanding tells me that gvfs and Samba are connected to perhaps this is a clue.

Each time I restart Evolution and try again these increase but do not die when I kill evolution.

I've tried starting evolution with --debug=File but file is created but never contains anything.

I've tried starting evolution via gdb to get a back trace (I Ctrl-C once evolution has locked up then do backtrace) - but it does not mean much to me:

<snip>
Thread 1 (Thread 0x7ffff7fb19c0 (LWP 3148)):
#0  0x00007ffff5c2db03 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007ffff2b07de0 in ?? () from /lib/x86_64-linux-gnu/libdbus-1.so.3
#2  0x00007ffff2b06ccd in ?? () from /lib/x86_64-linux-gnu/libdbus-1.so.3
#3  0x00007ffff2af1c05 in ?? () from /lib/x86_64-linux-gnu/libdbus-1.so.3
#4  0x00007ffff2af2ca2 in ?? () from /lib/x86_64-linux-gnu/libdbus-1.so.3
#5  0x00007ffff2f58e6a in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0
#6  0x00007ffff74da797 in ?? () from /usr/lib/libedataserverui-3.0.so.1
#7  0x00007ffff74da8b5 in ?? () from /usr/lib/libedataserverui-3.0.so.1
#8  0x00007ffff74da261 in ?? () from /usr/lib/libedataserverui-3.0.so.1
---Type <return> to continue, or q <return> to quit---
#9  0x00007ffff5f4bd53 in g_main_dispatch (context=0x651f50)
    at /build/buildd/glib2.0-2.32.3/./glib/gmain.c:2539
#10 g_main_context_dispatch (context=0x651f50)
    at /build/buildd/glib2.0-2.32.3/./glib/gmain.c:3075
#11 0x00007ffff5f4c0a0 in g_main_context_iterate (dispatch=1, 
    block=<optimized out>, context=0x651f50, self=<optimized out>)
    at /build/buildd/glib2.0-2.32.3/./glib/gmain.c:3146
#12 g_main_context_iterate (context=0x651f50, block=<optimized out>, 
    dispatch=1, self=<optimized out>)
    at /build/buildd/glib2.0-2.32.3/./glib/gmain.c:3083
#13 0x00007ffff5f4c49a in g_main_loop_run (loop=0xce8100)
    at /build/buildd/glib2.0-2.32.3/./glib/gmain.c:3340
#14 0x00007ffff691132d in gtk_main ()
   from /usr/lib/x86_64-linux-gnu/libgtk-3.so.0
#15 0x0000000000401ff2 in main ()

I have no idea what to try next.  Providing I do not try to send/receive or empty the trash, all works in Evolution.

Can anyone suggest something to try?
Many thanks

---

### Post by chinleybrewer on 2012-06-20
No suggestions??:(

---

### Post by chinleybrewer on 2012-07-03
I've managed to track the problem down to gnome-keyring-daemon.  If I do gnome-keyring-daemon -r then it is replaced, asks for my password and then all is well with evolution.  What I don't yet understand is why I have to do this perhaps 80% of the times I log in...

---

