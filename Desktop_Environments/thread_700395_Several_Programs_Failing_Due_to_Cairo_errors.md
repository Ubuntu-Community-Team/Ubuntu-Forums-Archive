---
title: "Several Programs Failing Due to Cairo errors"
date: 2008-02-18
forum: Desktop Environments
---

### Post by flickerfly on 2008-02-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mono/+bug/191414](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/191414) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having problems with a variety of programs throwing errors. The consistent piece among all of them seems to be Cairo. I don't know what this is, but I sure seem to have messed it up. I'm hoping you can look over the various error messages and give me some advice.

I've tried doing reinstalls of everything with mono and cairo in the name that is installed on my computer. I've tried running ldconfig. I may have messed something up when I compiled mono related depends myself. I've since tried rubenv's mono packages from his launchpad repository and then removed them and gone back to the more traditional repositories.

At some point, I thought it a mono bug so posted on a related bug, 191414 that sounded similar.

Anyway, here's what I have to give some clues to the problem...

When I start vim, it works, but starts by complaining:
```
$ vim
vim: /opt/mono-1.2.6/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
vim: Symbol `ospeed' has different size in shared object, consider re-linking

```

GTKPod has the some complaint, but it won't start at all:
```
$ gtkpod
gtkpod: /opt/mono-1.2.6/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
gtkpod: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

```
When compiling Geany complains and fails:
```
/bin/bash ../libtool --silent --tag=CXX --mode=link g++  -g -O2   -o geany  about.o build.o callbacks.o dialogs.o document.o editor.o encodings.o filetypes.o geanyobject.o geanywraplabel.o highlighting.o interface.o keybindings.o keyfile.o main.o msgwindow.o navqueue.o notebook.o plugins.o prefix.o prefs.o printing.o project.o sciwrappers.o search.o socket.o support.o symbols.o templates.o tools.o treeviews.o ui_utils.o utils.o vte.o ../scintilla/libscintilla.a ../tagmanager/libtagmanager.a -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0     
/usr/lib/libcairo.so: undefined reference to `png_read_info@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_filler@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_packing@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_tIME@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_IHDR@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_read_update_info@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_interlace_handling@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_write_fn@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_write_end@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_create_read_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_read_image@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_gray_to_rgb@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_bKGD@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_get_IHDR@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_strip_16@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_create_write_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_write_user_transform_fn@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_write_info@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_convert_from_time_t@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_destroy_write_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_get_io_ptr@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_palette_to_rgb@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_destroy_read_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_read_end@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_error@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_read_user_transform_fn@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_write_image@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_read_fn@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_create_info_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_expand_gray_1_2_4_to_8@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_get_valid@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_tRNS_to_alpha@PNG12_0'
collect2: ld returned 1 exit status
make[2]: *** [geany] Error 1
make[2]: Leaving directory `/home/josiah/src/geany/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josiah/src/geany'
make: *** [all] Error 2

```

All my mono programs complain: 
```
$ tomboy
Corlib not in sync with this runtime: expected corlib version 60, found 56.
Loaded from: /usr/lib/mono/2.0/mscorlib.dll
Download a newer corlib or a newer runtime at http://www.go-mono.com/daily.
```

```
$ banshee
Corlib not in sync with this runtime: expected corlib version 60, found 56.
Loaded from: /usr/lib/mono/2.0/mscorlib.dll
Download a newer corlib or a newer runtime at http://www.go-mono.com/daily.
```

```
$ f-spot

** (/usr/lib/f-spot/f-spot.exe:30548): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly: NDesk.DBus (assemblyref_index=8)
     Version: 1.0.0.0
     Public Key: f6716e4f9b2ed099
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).

** (/usr/lib/f-spot/f-spot.exe:30548): WARNING **: Could not load file or assembly 'NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099' or one of its dependencies.
Stacktrace:

Native stacktrace:

        f-spot [0x8194ca6]
        f-spot [0x81770ed]
        [0xffffe440]
        f-spot(mono_object_new+0x18) [0x80b596a]
        f-spot(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        f-spot(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        f-spot [0x810f9a7]
        f-spot [0x811a390]
        f-spot(mono_class_vtable+0x181) [0x80b29b3]
        f-spot(mono_object_new+0x18) [0x80b596a]
        f-spot(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        f-spot(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        f-spot [0x810f9a7]
        f-spot [0x8176370]
        f-spot [0x817699e]
        f-spot [0x8176a98]
        f-spot [0x8176f2d]
        f-spot(mono_runtime_invoke+0x27) [0x80b0b2f]
        f-spot(mono_runtime_exec_main+0x142) [0x80b5383]
        f-spot(mono_runtime_run_main+0x27e) [0x80b5631]
        f-spot(mono_jit_exec+0xbd) [0x805a4cb]
        f-spot [0x805a5a8]
        f-spot(mono_main+0x1683) [0x805bdc9]
        f-spot [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cad050]
        f-spot [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1211541808 (LWP 30548)]
[New Thread -1222968432 (LWP 30550)]
[New Thread -1217188976 (LWP 30549)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1217188976 (LWP 30549) 0xffffe410 in __kernel_vsyscall ()
  2 Thread -1222968432 (LWP 30550) 0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211541808 (LWP 30548) 0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1217188976 (LWP 30549)):
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb7e129f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2 0x0811bc9f in ?? ()
#3 0xb77323ac in ?? ()
#4 0x00000000 in ?? ()

Thread 2 (Thread -1222968432 (LWP 30550)):
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb7e0f676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2 0x08120dde in ?? ()
#3 0xb76991dc in ?? ()
#4 0xb76991c4 in ?? ()
#5 0xb7e0d541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6 0x081210eb in ?? ()
#7 0xb76991dc in ?? ()
#8 0xb76991c4 in ?? ()
#9 0x00000000 in ?? ()

Thread 1 (Thread -1211541808 (LWP 30548)):
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb7d632a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2 0xb7e82780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3 0xb7e82b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4 0x08194d84 in ?? ()
#5 0xb7b55844 in ?? ()
#6 0xb7b5582c in ?? ()
#7 0xb7b55828 in ?? ()
#8 0xb7b55824 in ?? ()
#9 0x00000000 in ?? ()
#0 0xffffe410 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Aborted (core dumped)
```

---

### Post by dmartin on 2008-02-18
I'm having very similar problems.  Only strange thing is that this server was once headless.  I've since installed ubuntu-desktop.  I've tried reinstall libcairo2, but it didn't make any difference.  Very lost here.

---

### Post by flickerfly on 2008-02-19
I talked with the Cairo guys on IRC and they said that I had 2 instances of Cairo setup, one inside a mono install I had in /opt. I moved that mono directory so it couldn't be found anymore and it all seems to have straightened out. I then had to do some cleanup of mono and reinstall some other things but my cairo complaints went away.

This was working right at the end of the day yesterday so I'm not sure it is all straightened out, but sure is a lot better.

---

