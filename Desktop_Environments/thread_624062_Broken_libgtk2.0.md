---
title: "Broken libgtk2.0?"
date: 2007-11-26
forum: Desktop Environments
---

### Post by niemand on 2007-11-26
Just did the security patches and now gnome and all its applications crash. Sigh...

Picking an simple application, lets look at gnome-terminal since the results should be obvious. If I do an strace it ends with no terminal but this information:

stat("/usr/share/pixmaps", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
stat("/usr/share/pixmaps", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
open("/usr/share/pixmaps/icon-theme.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/pixmaps", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 15
fstat(15, {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
fcntl(15, F_SETFD, FD_CLOEXEC)          = 0
getdents(15, /* 110 entries */, 4096)   = 4080
getdents(15, /* 107 entries */, 4096)   = 4088
getdents(15, /* 13 entries */, 4096)    = 456
getdents(15, /* 0 entries */, 4096)     = 0
close(15)                               = 0
stat("/usr/share/gdm/pixmaps", 0x7fffe4344c50) = -1 ENOENT (No such file or directory)
gettimeofday({1196104059, 98699}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++

Note, all other applications die in same manner. So, using gdb:

 (gdb) backtrace
#0  0x00002b91b59e27d9 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#1  0x00002b91b59e2ab9 in _gtk_icon_cache_get_icon_flags ()
   from /usr/lib/libgtk-x11-2.0.so.0
#2  0x00002b91b59e7a49 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#3  0x00002b91b59e8425 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#4  0x00002b91b59e956d in gtk_icon_theme_lookup_icon ()
   from /usr/lib/libgtk-x11-2.0.so.0
#5  0x00002b91b59e9680 in gtk_icon_theme_load_icon ()
   from /usr/lib/libgtk-x11-2.0.so.0
#6  0x00002b91b4401dcb in launchpad_integration_add_item_factory ()
   from /usr/lib/liblaunchpad-integration.so.0
#7  0x00002b91b4401eb8 in ?? () from /usr/lib/liblaunchpad-integration.so.0
#8  0x00002b91b4402035 in launchpad_integration_get_action_group ()
   from /usr/lib/liblaunchpad-integration.so.0
#9  0x00002b91b440217f in launchpad_integration_add_items ()
   from /usr/lib/liblaunchpad-integration.so.0
#10 0x000000000042d383 in ?? ()
#11 0x00002b91b7183eb0 in g_type_create_instance ()
   from /usr/lib/libgobject-2.0.so.0
#12 0x00002b91b716b22d in ?? () from /usr/lib/libgobject-2.0.so.0
#13 0x00002b91b7169664 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#14 0x00002b91b716a0ac in g_object_new_valist ()
   from /usr/lib/libgobject-2.0.so.0
#15 0x00002b91b716a2e1 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#16 0x000000000042c0bc in ?? ()
#17 0x0000000000419a35 in ?? ()
#18 0x000000000041a41b in ?? ()
#19 0x000000000041afb5 in ?? ()
#20 0x00002b91b7dbdb44 in __libc_start_main () from /lib/libc.so.6
#21 0x0000000000411039 in ?? ()
#22 0x00007ffff68c4dd8 in ?? ()
#23 0x0000000000000000 in ?? ()
(gdb)


Not too much of a surprise since all of the symbols have been stripped. So I decided to rebuild libgtk2.0 with symbols. So I did the following:

apt-get build-dep libgtk2.0-0
export DEB_BUILD_OPTIONS="nostrip,noopt fakeroot" ; apt-get -b source libgtk2.0-0

The build then dies with:

gcc -Wall -g -O0 -o gdk-pixbuf-csource gdk-pixbuf-csource.o -pthread  ./.libs/libgdk_pixbuf-2.0.a /usr/lib/libtiff.so -lz -lc /usr/lib/libjpeg.so -lpng12 -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so -lrt /usr/lib/libglib-2.0.so
./.libs/libgdk_pixbuf-2.0.a(gdk-pixbuf-io.o): In function `process_module_file':
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:396: undefined reference to `skip_space'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:419: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:428: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:436: undefined reference to `scan_int'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:443: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:451: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:461: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:474: undefined reference to `scan_string'
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:493: undefined reference to `scan_string'
./.libs/libgdk_pixbuf-2.0.a(gdk-pixbuf-io.o):/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:497: more undefined references to `scan_string' follow
./.libs/libgdk_pixbuf-2.0.a(gdk-pixbuf-io.o): In function `process_module_file':
/root/gtk+2.0-2.12.0/gdk-pixbuf/gdk-pixbuf-io.c:504: undefined reference to `scan_int'
collect2: ld returned 1 exit status
make[5]: *** [gdk-pixbuf-csource] Error 1
make[5]: Leaving directory `/root/gtk+2.0-2.12.0/debian/build/static/gdk-pixbuf'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/root/gtk+2.0-2.12.0/debian/build/static/gdk-pixbuf'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/root/gtk+2.0-2.12.0/debian/build/static/gdk-pixbuf'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/gtk+2.0-2.12.0/debian/build/static'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/gtk+2.0-2.12.0/debian/build/static'
make: *** [debian/stampdir/build-stamp-static] Error 2
Build command 'cd gtk+2.0-2.12.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

It is interesting that the missing symbols have a vague reference to parsing and handling pixmaps as shown with the strace and gdb output.

So, can someone please tell where I can find the functions scan_string, scan_int and the rest of them. It would make sense that these missing variables are the root of my problem.

Of course, any other suggestions are welcome as well. It is just hard to work with the system currently being without gnome for now.

Thanks in advance for any and all help.

---

### Post by niemand on 2007-11-26
It is fixed. Just detected and installed the new gnome-system-tools and things are once again working.

---

### Post by burkha on 2008-01-02
I ran into this exact same issue after a standard update. I was seeing similar strace results and google pointed me to your post. Resintalling gnome-system-tools fixed it for me.

Thank you!

---

