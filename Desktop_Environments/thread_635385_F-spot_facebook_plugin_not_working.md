---
title: "F-spot facebook plugin not working"
date: 2007-12-08
forum: Desktop Environments
---

### Post by Blutack on 2007-12-08
Has anybody else managed to get the facebook export plugin for F-spot to actually work?  It downloads fine and claims to be installed but there is nothing in the Export menu.  I have tried restarting F-spot, disabling and re-enabling and uninstalling and reinstalling.  Starting from the terminal gives this output.
```

blutack@tanstaafl:~$ f-spot
Initializing Mono.Addins
Starting new FSpot server
Query: SELECT photos.id, photos.time, photos.directory_path, photos.name, photos.description, photos.roll_id, photos.default_version_id FROM photos ORDER BY photos.time
Query: SELECT photos.id, photos.time, photos.directory_path, photos.name, photos.description, photos.roll_id, photos.default_version_id FROM photos ORDER BY photos.time
Query: SELECT photos.id, photos.time, photos.directory_path, photos.name, photos.description, photos.roll_id, photos.default_version_id FROM photos ORDER BY photos.time

(f-spot:7065): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(f-spot:7065): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
Query: SELECT photos.id, photos.time, photos.directory_path, photos.name, photos.description, photos.roll_id, photos.default_version_id FROM photos ORDER BY photos.time
Reloading
Query: SELECT photos.id, photos.time, photos.directory_path, photos.name, photos.description, photos.roll_id, photos.default_version_id FROM photos ORDER BY photos.time
item changed
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0018.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0018.JPG

(f-spot:7065): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0018.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0018.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSC00189.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSC00189.JPG
open uri = file:///home/blutack/Photos/2007/11/17/DSC00194.JPG
open uri = file:///home/blutack/Photos/2007/11/17/DSC00194.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0017.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0017.JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0016 (Modified in GIMP Image Editor).JPG
open uri = file:///home/blutack/Photos/2007/11/13/DSCN0016 (Modified in GIMP Image Editor).JPG

```
Thanks in advance, even if you don't have an answer if it works for you could you tell me please?

---

### Post by Mr. Picklesworth on 2007-12-08
Have you enabled it via Edit -> Manage Extensions in the program menu?

Edit:
Duh, of course you have! Sorry about the useless suggestion :(
(Well, assuming you installed it through there in the first place. You did, right?)

Same boat here, now that I have tried the extension myself. I wonder if it is to do with the extension's core dependency not being met...
Information for the extension says it wants 0.4.0.3457, whereas f-spot -V gives 0.4.0.0. Seems improbable, but worth a look.

Update:
No joy with 0.4.1.

Update 2:
Jumped to conclusions there. I learned shortly after reverting to 0.4 that having upgraded means that I will never be able to use 0.4 again since the database went with it. A bit of fiddling later, the Facebook exporter is working in 0.4.1, but I do not remember why... It seems that it may have been caused by me disabling then enabling the default exporters extension.

---

### Post by mrtorrent on 2007-12-09
I'm having the same problem. I've tried disabling and re-enabling both the default export plugins and the Facebook one and no joy. Still googling around, so I'll mention it here if I come across anything...

---

### Post by Blutack on 2007-12-11
Thanks guys!  I've tried to compile mono apps before and painful is an understatement, so I'm just going to keep exporting them to desktop and using facebook java uploader.

---

### Post by sds50 on 2007-12-18
I can't seem to get this plugin working either.

Going through the install process (install Add-ins) allows me to select it in a list and install, where it says installed correctly, but it never appears under "Export" in the add-in manager, and certainly not under the Export option in the file menu.

On top of this, trying to repeat the process now says installation failed, presumably because the facebook plugin files exist in .gnome2/f-spot/addins.

This leaves me slightly bemused as to how this is supposed to work (this problem seems consistent over a couple of different distributions on different machines...)

---

### Post by Skerit on 2008-01-08
So then I'm still wondering how Mr Picklesworth fixed it ... 

I just upgraded to Hardy to get it to work (as I was too lazy to compile 0.4.1.. and I'm also too lazy to upload picture by picture :))

Anyway, there aren't that many config files, right? So could we maybe compare those?

*Edit: Looking in the ~/.gnome2/f-spot/addin-db-001/addin-date/global/ map there are several *.maddin files, but the facebook exporter doesn't seem to create one. On the other hand all the other files (the files the other extensions also make) are there.. so it's just this .maddin file problem

---

### Post by Blutack on 2008-01-10
I spent about an hour messing around creating .maddin files and moving stuff around.
No joy unfortunately.  Think it requires the latest version.
God damn Mono.

Edit: My old trick of dpkg -i --force-all with the hardy package didn't work either, it just segfaults.
Double damn Mono!

---

### Post by Skerit on 2008-01-10
Wlel I did install hardy completely (runs quite stable at the moment) but have noo desire to hack the maddin files with a hex editor :P

And yet this hsouldn't be that hard to fix!

---

### Post by BradDet on 2008-01-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/178476](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/178476) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

 After playing around a bit I got the face book exporter working for F-Spot 0.4.0 on Ubuntu Feisty.

I'm not sure of all the instructions, but if someone could try this and let me know if it works that would be great

You can download 0.91 version of the facebook exporter here

[http://www.bwebcentral.com/fb/facebookexport.tgz]("http://www.bwebcentral.com/fb/facebookexport.tgz")

unzip/untar it and run

make
make install

You may have to delete the /home/adminbrad/.gnome2/f-spot/addin-db-000 to have it show up.

Don't forget to backup your photos.db file just in case

If you running Feisty and you don't have F-Spot 0.4.0 you can install prevu and then compile it form the dsc file. 

Please let me know if this works for you. I was happy to finally get it working !

---

### Post by kroiz on 2008-04-11
I downloaded and extracted when I tried to build first It failed
```
gmcs -target:library -out:FacebookExport.dll FacebookExport.cs  -pkg:glade-sharp-2.0 -pkg:gtk-sharp-2.0 -pkg:f-spot -r:Mono.Posix -r:Mono.Facebook.dll -resource:FacebookExport.glade -resource:FacebookExport.addin.xml 
make: gmcs: Command not found
make: *** [FacebookExport.dll] Error 127

```Then I installed from synaptic mono-gmcs
I built it again successfully (I think)
```

kroiz@ubuntulap:~/facebookexporter$ make
gmcs -target:library -out:FacebookExport.dll FacebookExport.cs  -pkg:glade-sharp-2.0 -pkg:gtk-sharp-2.0 -pkg:f-spot -r:Mono.Posix -r:Mono.Facebook.dll -resource:FacebookExport.glade -resource:FacebookExport.addin.xml 
FacebookExport.cs(461,42): warning CS0219: The variable `popup' is assigned but its value is never used
FacebookExport.cs(548,61): warning CS0219: The variable `photo' is assigned but its value is never used
FacebookExport.cs(33,39): warning CS0414: The private field `FSpot.Exporter.Facebook.FacebookAccount.keyring_item_name' is assigned but its value is never used
Compilation succeeded - 3 warning(s)

kroiz@ubuntulap:~/facebookexporter$ make install
cp *.dll ~/.gnome2/f-spot/addins/

```then when running f-spot I did not see an option to export to facebook indeed I deleted
```
 /home/adminbrad/.gnome2/f-spot/addin-db-000
```Then I run f-spot and the option appeared but when I click it f-spot crashes
```

** (f-spot:6043): WARNING **: The class FSpot.Widgets.IconView could not be loaded, used in f-spot, Version=0.4.1.0, Culture=neutral
Stacktrace:

  at GLib.Signal.voidObjectCallback (intptr,intptr) <0xffffffff>
  at GLib.Signal.voidObjectCallback (intptr,intptr) <0x000e0>
  at (wrapper native-to-managed) GLib.Signal.voidObjectCallback (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x00007>
  at Gnome.Program.Run () <0x00007>
  at FSpot.Driver.Main (string[]) <0x00858>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        f-spot [0x8194ca6]
        f-spot [0x81770ed]
        [0xffffe440]
        f-spot [0x81507fd]
        f-spot [0x8160fd2]
        f-spot [0x81751ee]
        f-spot [0x8176329]
        f-spot [0x817699e]
        f-spot [0x8176a98]
        f-spot(mono_compile_method+0x3b) [0x80b13bd]
        f-spot [0x808fe5a]
        [0xb7c1a032]
        [0xb3d704e8]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49) [0xb63c8c09]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122) [0xb63bb772]
        /usr/lib/libgobject-2.0.so.0 [0xb63cc611]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7) [0xb63cd847]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb63cda09]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58) [0xb6992fe8]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x14a) [0xb687d38a]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb687ef28]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb6876178]
        /usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e) [0xb68701de]
        /usr/lib/libgobject-2.0.so.0 [0xb63b9f89]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122) [0xb63bb772]
        /usr/lib/libgobject-2.0.so.0 [0xb63cc973]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f) [0xb63cd60f]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb63cda09]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb698e498]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x14f) [0xb686936f]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x307) [0xb686a587]
        /usr/lib/libgdk-x11-2.0.so.0 [0xb66d5b9a]
        /usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c) [0xb7f1511c]
        /usr/lib/libglib-2.0.so.0 [0xb7f1855f]
        /usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9) [0xb7f18909]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4) [0xb686a9e4]
        [0xb09c4640]
        [0xb09c45f0]
        [0xb09c45d0]
        [0xb77e6719]
        [0xb77e5075]
        f-spot [0x8176f50]
        f-spot(mono_runtime_invoke+0x27) [0x80b0b2f]
        f-spot(mono_runtime_exec_main+0x142) [0x80b5383]
        f-spot(mono_runtime_run_main+0x27e) [0x80b5631]
        f-spot(mono_jit_exec+0xbd) [0x805a4cb]
        f-spot [0x805a5a8]
        f-spot(mono_main+0x1683) [0x805bdc9]
        f-spot [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d71050]
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
[New Thread -1210738992 (LWP 6043)]
[New Thread -1281164400 (LWP 6050)]
[New Thread -1280046192 (LWP 6049)]
[New Thread -1258734704 (LWP 6046)]
[New Thread -1222108272 (LWP 6045)]
[New Thread -1216386160 (LWP 6044)]
(no debugging symbols found)
(no debugging symbols found)
....
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  6 Thread -1216386160 (LWP 6044)  0xffffe410 in __kernel_vsyscall ()
  5 Thread -1222108272 (LWP 6045)  0xffffe410 in __kernel_vsyscall ()
  4 Thread -1258734704 (LWP 6046)  0xffffe410 in __kernel_vsyscall ()
  3 Thread -1280046192 (LWP 6049)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1281164400 (LWP 6050)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210738992 (LWP 6043)  0xffffe410 in __kernel_vsyscall ()

Thread 6 (Thread -1216386160 (LWP 6044)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ed69f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb77f63ac in ?? ()
#4  0x00000000 in ?? ()

Thread 5 (Thread -1222108272 (LWP 6045)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ed3676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb775b1dc in ?? ()
#4  0xb775b1c4 in ?? ()
#5  0xb7ed1541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb775b1dc in ?? ()
#8  0xb775b1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 4 (Thread -1258734704 (LWP 6046)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ed38fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120e5b in ?? ()
#3  0xb775b464 in ?? ()
#4  0xb775b44c in ?? ()
#5  0xb4f93054 in ?? ()
#6  0x00000000 in ?? ()

Thread 3 (Thread -1280046192 (LWP 6049)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ed38fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120e5b in ?? ()
#3  0xb775d4e0 in ?? ()
#4  0xb775d4c8 in ?? ()
#5  0xb3b40060 in ?? ()
#6  0x00000000 in ?? ()

Thread 2 (Thread -1281164400 (LWP 6050)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ed38fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120e5b in ?? ()
#3  0xb775d54c in ?? ()
#4  0xb775d534 in ?? ()
#5  0xb3a2f058 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1210738992 (LWP 6043)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e272a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f46780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f46b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7c19844 in ?? ()
#6  0xb7c1982c in ?? ()
#7  0xb7c19828 in ?? ()
#8  0xb7c19824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)


```

---

