---
title: "Gnome Panel Crashes Over and Over"
date: 2007-02-08
forum: Desktop Environments
---

### Post by maddog39 on 2007-02-08
Hello all,

I have no idea what it is but somehow I keep breaking various parts of ubuntu.. well anyway. I was messing around with an ISO that I later find out is corrupt or something and isn't burning. So I go Right Click > Move to Trash but miss the "Move to Trash" and hit "Extract Here" causing gnome-panel to crash violently. Now I cant login at all to gnome because every time I do, gnome-panel immediatly crashes and the bug report tool pops up as usual and then gnome-panel automatically restarts or attempts to and then continues to keep crashing until I restart X. Via a failsafe terminal (I've tried failsafe GNOME, same thing happens) I have reinstalled just about everything. I reinstalled ubuntu-desktop, gnome-desktop, gnome-panel, etc none of them worked. I tried purging each of those packages and then to a fresh install, same result. In desperation I installed IceWM and are using that at the moment. But I have really run out of ideas on what to do. Anyone have any other solutions?

Thanks!
-maddog39

---

### Post by shareMenaPeace on 2007-02-08
At teh login screen switch to the consoel ALT F2 and type

```
killall gnome-panel
```
might work :)

---

### Post by maddog39 on 2007-02-09
I use Alt+F2 on a regular basis, so I tried it, and it doesnt work, probably because that freature is driven by gnome-panel, also it wouldn't have done anything anyway because if I tried to start it again, it'd just keep crashing. :/

---

### Post by shareMenaPeace on 2007-02-09
Can you login with failsafe session?

---

### Post by kurup on 2007-02-09
Am having the same problem. Was trying to install a mouse theme..thats when it happened. Failsafe GNOME works properly..but the minute I go back into normal GNOME session, all I see is my wallpaper. No task bar..nothing. Right click menu works tho. Alt+F2 does not work either. Any ideas what the problem might be..and how to fix it?

---

### Post by shareMenaPeace on 2007-02-09
Maybe you have a application inside 
System -> Preferences -> Session under Startup Programs which is errorness and cause the error. Try uninstalling the mouse theme or disable it first to see if it cause this.

---

### Post by jkzubu on 2007-02-09
maddog39-  I have the exact same problem with a different cause.  I tried to launch an .iso from a flash drive instead of using a cd.  Did you have or find any success solving your problem?  I have noticed that my .Trash-*username* ended up on the flash drive.  I am investigating whether I need to replace my .Trash- file in nautilus or somewhere else. Anybody? I am runnin' Edgy.

-J

---

### Post by ComplexNumber on 2007-02-09
> **maddog39 said:**
> Hello all,

I have no idea what it is but somehow I keep breaking various parts of ubuntu.. well anyway. I was messing around with an ISO that I later find out is corrupt or something and isn't burning. So I go Right Click > Move to Trash but miss the "Move to Trash" and hit "Extract Here" causing gnome-panel to crash violently. Now I cant login at all to gnome because every time I do, gnome-panel immediatly crashes and the bug report tool pops up as usual and then gnome-panel automatically restarts or attempts to and then continues to keep crashing until I restart X. Via a failsafe terminal (I've tried failsafe GNOME, same thing happens) I have reinstalled just about everything. I reinstalled ubuntu-desktop, gnome-desktop, gnome-panel, etc none of them worked. I tried purging each of those packages and then to a fresh install, same result. In desperation I installed IceWM and are using that at the moment. But I have really run out of ideas on what to do. Anyone have any other solutions?

Thanks!
-maddog39
at the login screen, choose failsafe and go into your home drieectory and rename the following to something like panelOLD:
[B] /home/<your-username>/.gconf/apps/panel


[/B] ie** 'mv **** /home/<your-username>/.gconf/apps/panel****[COLOR=White]....[/COLOR]/home/<your-username>/.gconf/apps/panelOLD'**

---

### Post by maddog39 on 2007-02-10
I tried your suggestion, yet it had no effect. I had also previously looked into the trash can problem myself, but that doesnt seem to fix anything either.

---

### Post by jkzubu on 2007-02-10
Part of the problem is in the error report below.  Although I have tried, there appears to be difficulty with the libthread or lib device files... Anybody?   Linux is usually so good about fixing itself.  Back in the Gnome Desktop, the panels won't load because the Gnome_Panel_Trash Applet cant be found... then hangs in infinite loop and forces you to abort.    The bug report indicates some errors related to the same files below.  To 'bug' out of Gnome, went into safe mode, loaded KDE, booted into KDE, and tried to sudo a few ideas to fix.  No luck.  I would rather  try to fix than reload ubuntu altogether.  The problem seems to be deeper than KDE or Gnome.  Any Ideas for resolution are appreciated.   -J


~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
47 not fully installed or removed.
Need to get 0B/1852kB of archives.
After unpacking 8061kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154888 files and directories currently installed.)
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libpthread.a', which is also in package libpthread-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by shareMenaPeace on 2007-02-10
Try booting in recovery mode (this logs you as root).

Than 
```

cd /home/userrname/

```
than

```
ls
```

than 
```
cd .Trash 
```

than 

```
ls
```

than delete the iso stuff at least

with```
 rm filename
```   or rm filen*

Than reboot normal and see if this fix anything,

When this not helps boot again in recovery mode and see if you can launch

```
startx
```


post any errors

---

### Post by jkzubu on 2007-02-10
...from above...

Also in Synaptic try to fix broken and resolve issues, message is:    E: /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb: trying to overwrite `/usr/lib/libpthread.a', which is also in package libpthread-dev

and upgrades, fixes, etc, all fail..   Getting scary.

---

### Post by maddog39 on 2007-02-10
Almost all the ubuntu updates lately have been really "edgy"... many reports of broken systems' after updates. Well speaking of updates, I have fixed my problem but only after much frustration. What I did was I went to the gnome website ([www.gnome.org](www.gnome.org)) and I downloaded the gnome-panel package version 2.16.3 and recompiled/installed from source. It did not work initially however after a few restarts the gnome-panel reset and is now fully functional again without any other problems. Although I do not confirm this as a fix because its really iffy on how/what actually fixed it.

---

### Post by ghetto2ivy on 2007-02-11
I'm getting a circular crash here too. Bug report tool launches, then the gnome panel crashes again. Restarts, renaming the panel directory, nothing works.

Here is the Gnome Panel Bug Report:
```
Memory status: size: 53338112 vsize: 0 resident: 53338112 share: 0 rss: 14020608 rss_rlim: 0
CPU usage: start_time: 1171253123 rtime: 0 utime: 62 stime: 0 cutime:60 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[New Thread -1225603408 (LWP 5810)]
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
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75e3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7edb1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74cb770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74ccef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76e7122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76e7159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76e71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b36d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b36dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b32591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76dcaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76de802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76e17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76e1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ae0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225603408 (LWP 5810)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75e3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7edb1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74cb770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74ccef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76e7122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76e7159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76e71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b36d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b36dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b32591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76dcaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76de802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76e17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76e1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ae0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

Steven

---

### Post by brk3 on 2007-02-12
hi this started happening to me also after an automatic update last night. very frustrating. however i have found the solution!

rm -rf .recently-used.xbel 

hope it works for you too, ubuntu should think twice before putting out dodgy updates this is not the first time something like this has happened. peace

---

### Post by raffytaffy on 2007-02-12
same problem here. installed cursor theme today..few hours later this problem start happening. At first i didnt correlate the two.but i filed bug report - [http://bugzilla.gnome.org/show_bug.cgi?id=407262](http://bugzilla.gnome.org/show_bug.cgi?id=407262)

i was mistaken to think it was caused by power management. i have uninstaled the curosr packages and rebooted. i really hope it wont repeat.

---

### Post by raffytaffy on 2007-02-12
it happen again. debug info - please help

Memory status: size: 39555072 vsize: 0 resident: 39555072 share: 0 rss: 18063360 rss_rlim: 0
CPU usage: start_time: 1171322516 rtime: 0 utime: 272 stime: 0 cutime:245 cstime: 0 timeout: 27 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1225750864 (LWP 3976)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75bf323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eb71b6 in libgnomeui_segv_handle (signum=11) at gnome-ui-init.c:874
#3  <signal handler called>
#4  icon_tip_buffer_compare (a=0x850ae38, b=0xbf9b5450) at main.c:292
#5  0xb638846c in message_sent (manager=0x812d6f0, icon=0x845fea8, 
    text=0x8486e60 "50 Cent - You Should Be Here", id=5, timeout=2000, 
    trays_screen=0x850ae38) at main.c:369
#6  0xb638a1cb in _na_marshal_VOID__OBJECT_STRING_LONG_LONG (
    closure=0x8317420, return_value=0x0, n_param_values=5, 
    param_values=0xbf9b56ac, invocation_hint=0xbf9b55bc, 
    marshal_data=0xb6388410) at na-marshal.c:121
#7  0xb780379b in IA__g_closure_invoke (closure=0x8317420, return_value=0x0, 
    n_param_values=5, param_values=0xbf9b56ac, invocation_hint=0xbf9b55bc)
    at gclosure.c:490
#8  0xb7813b93 in signal_emit_unlocked_R (node=0x8369398, detail=0, 
    instance=0x812d6f0, emission_return=0x0, instance_and_params=0xbf9b56ac)
    at gsignal.c:2440
#9  0xb78150b7 in IA__g_signal_emit_valist (instance=0x812d6f0, 
    signal_id=253, detail=0, var_args=0xbf9b58fc "! \224·xZ\233¿ \024*\b\b")
    at gsignal.c:2199
#10 0xb7815279 in IA__g_signal_emit (instance=0x812d6f0, signal_id=253, 
    detail=0) at gsignal.c:2243
#11 0xb6388c08 in na_tray_manager_handle_client_message_message_data (
    xev=0xbf9b5a78, event=0x82a1420, data=0x812d6f0) at na-tray-manager.c:411
#12 0xb79449a3 in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#13 0xb79453bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#14 0xb79457bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#15 0xb76ba802 in IA__g_main_context_dispatch (context=0x80ecb00)
    at gmain.c:2045
#16 0xb76bd7df in g_main_context_iterate (context=0x80ecb00, block=1, 
    dispatch=1, self=0x80c8b10) at gmain.c:2677
#17 0xb76bdb89 in IA__g_main_loop_run (loop=0x8243310) at gmain.c:2881
#18 0xb7abc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x08061d8c in main (argc=3, argv=0xbf9b5d44) at main.c:95

Thread 1 (Thread -1225750864 (LWP 3976)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75bf323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eb71b6 in libgnomeui_segv_handle (signum=11) at gnome-ui-init.c:874
	estatus = 1069128089
	sa = {__sigaction_handler = {sa_handler = 0, sa_sigaction = 0}, 
  sa_mask = {__val = {0, 4294115328, 3076186100, 3076190496, 139582504, 
      3214627000, 3075361348, 3076190496, 139582504, 32768, 98304, 32768, 
      65536, 1507328, 0, 0, 3079231284, 3214627092, 0, 3214627032, 
      3078952891, 139582504, 917528, 0, 3079231284, 3079231284, 3214627092, 
      3214627128, 3078947126, 3214627092, 138943188, 0}}, 
  sa_flags = -1080339984, sa_restorer = 0x9999999a}
	pid = 0
	in_segv = 1
#3  <signal handler called>
No symbol table info available.
#4  icon_tip_buffer_compare (a=0x850ae38, b=0xbf9b5450) at main.c:292
	buffer_a = <value optimized out>
	buffer_b = <value optimized out>
#5  0xb638846c in message_sent (manager=0x812d6f0, icon=0x845fea8, 
    text=0x8486e60 "50 Cent - You Should Be Here", id=5, timeout=2000, 
    trays_screen=0x850ae38) at main.c:369
	icontip = <value optimized out>
	find_buffer = {text = 0x85154f8 "°PQ\b", id = 5, 
  timeout = -1218728743}
#6  0xb638a1cb in _na_marshal_VOID__OBJECT_STRING_LONG_LONG (
    closure=0x8317420, return_value=0x0, n_param_values=5, 
    param_values=0xbf9b56ac, invocation_hint=0xbf9b55bc, 
    marshal_data=0xb6388410) at na-marshal.c:121
	data1 = (gpointer) 0x812d6f0
	data2 = <value optimized out>
	__PRETTY_FUNCTION__ = "_na_marshal_VOID__OBJECT_STRING_LONG_LONG"
#7  0xb780379b in IA__g_closure_invoke (closure=0x8317420, return_value=0x0, 
    n_param_values=5, param_values=0xbf9b56ac, invocation_hint=0xbf9b55bc)
    at gclosure.c:490
	marshal = (
    GClosureMarshal) 0xb638a160 <_na_marshal_VOID__OBJECT_STRING_LONG_LONG>
	marshal_data = (gpointer) 0x0
	__PRETTY_FUNCTION__ = "IA__g_closure_invoke"
#8  0xb7813b93 in signal_emit_unlocked_R (node=0x8369398, detail=0, 
    instance=0x812d6f0, emission_return=0x0, instance_and_params=0xbf9b56ac)
    at gsignal.c:2440
	tmp = <value optimized out>
	handler = (Handler *) 0x8365bc0
	accumulator = (SignalAccumulator *) 0x0
	emission = {next = 0x0, instance = 0x812d6f0, ihint = {
    signal_id = 253, detail = 0, run_type = G_SIGNAL_RUN_FIRST}, 
  state = EMISSION_RUN, chain_type = 4}
	class_closure = (GClosure *) 0x836a9d8
	handler_list = (Handler *) 0x8365bc0
	return_accu = (GValue *) 0x0
	accu = {g_type = 0, data = {{v_int = 0, v_uint = 0, v_long = 0, 
      v_ulong = 0, v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, 
      v_pointer = 0x0}, {v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, 
      v_int64 = 0, v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}
	signal_id = 253
	max_sequential_handler_number = 10852
	return_value_altered = 0
#9  0xb78150b7 in IA__g_signal_emit_valist (instance=0x812d6f0, 
    signal_id=253, detail=0, var_args=0xbf9b58fc "! \224·xZ\233¿ \024*\b\b")
    at gsignal.c:2199
	_flags = <value optimized out>
	_vtable = <value optimized out>
	_cvalues = {{v_int = -1216224748, v_long = -1216224748, 
    v_int64 = -5223262282825211372, v_double = -2.7614703882320527e-41, 
    v_pointer = 0xb781e214}, {v_int = -1218728768, v_long = -1218728768, 
    v_int64 = -5234400090803950400, v_double = -4.9639950306314885e-42, 
    v_pointer = 0xb75bacc0}, {v_int = -1217265180, v_long = -1217265180, 
    v_int64 = -5223262282826251804, v_double = -2.7614703877016514e-41, 
    v_pointer = 0xb77201e4}, {v_int = 1079749824, v_long = 1079749824, 
    v_int64 = -4640018061173478208, v_double = -0.02670348065195749, 
    v_pointer = 0x405bacc0}, {v_int = -1217564620, v_long = -1217564620, 
    v_int64 = 587444086268325940, v_double = 2.1787695555409238e-269, 
    v_pointer = 0xb76d7034}, {v_int = -1211317502, v_long = -1211317502, 
    v_int64 = -4640017990450101502, v_double = -0.026703726022961234, 
    v_pointer = 0xb7ccc302}, {v_int = -1217732265, v_long = -1217732265, 
    v_int64 = 492703506775, v_double = 2.4342787628303737e-312, 
    v_pointer = 0xb76ae157}, {v_int = -1217265180, v_long = -1217265180, 
    v_int64 = -4640017921736572444, v_double = -0.026703964420905182, 
    v_pointer = 0xb77201e4}}
	_lcopy_format = <value optimized out>
	_n_values = <value optimized out>
	return_value = {g_type = 3080207220, data = {{v_int = 135155944, 
      v_uint = 135155944, v_long = 135155944, v_ulong = 135155944, 
      v_int64 = 596162523339575528, v_uint64 = 596162523339575528, 
      v_float = 4.28266755e-34, v_double = 8.3267004144264563e-269, 
      v_pointer = 0x80e50e8}, {v_int = -1080338280, v_uint = 3214629016, 
      v_long = -1080338280, v_ulong = 3214629016, 
      v_int64 = -5218260020179019624, v_uint64 = 13228484053530531992, 
      v_float = -1.21364117, v_double = -6.0313670303297222e-41, 
      v_pointer = 0xbf9b5898}}}
	error = <value optimized out>
	instance_and_params = (GValue *) 0xbf9b56ac
	stack_values = {{g_type = 135211912, data = {{v_int = 135452400, 
        v_uint = 135452400, v_long = 135452400, v_ulong = 135452400, 
        v_int64 = 135452400, v_uint64 = 135452400, v_float = 4.41879347e-34, 
        v_double = 6.6922377486746863e-316, v_pointer = 0x812d6f0}, {
        v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, 
        v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}, {
    g_type = 136798096, data = {{v_int = 138804904, v_uint = 138804904, 
        v_long = 138804904, v_ulong = 138804904, v_int64 = 138804904, 
        v_uint64 = 138804904, v_float = 5.95818781e-34, 
        v_double = 6.8578734540692226e-316, v_pointer = 0x845fea8}, {
        v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, 
        v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}, {
    g_type = 64, data = {{v_int = 138964576, v_uint = 138964576, 
        v_long = 138964576, v_ulong = 138964576, v_int64 = 138964576, 
        v_uint64 = 138964576, v_float = 6.0315056e-34, 
        v_double = 6.8657622990494989e-316, v_pointer = 0x8486e60}, {
        v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, 
        v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}, {
    g_type = 32, data = {{v_int = 5, v_uint = 5, v_long = 5, v_ulong = 5, 
        v_int64 = 5, v_uint64 = 5, v_float = 7.00649232e-45, 
        v_double = 2.4703282292062327e-323, v_pointer = 0x5}, {v_int = 0, 
        v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, 
        v_float = 0, v_double = 0, v_pointer = 0x0}}}, {g_type = 32, data = {{
        v_int = 2000, v_uint = 2000, v_long = 2000, v_ulong = 2000, 
        v_int64 = 2000, v_uint64 = 2000, v_float = 2.80259693e-42, 
        v_double = 9.8813129168249309e-321, v_pointer = 0x7d0}, {v_int = 0, 
        v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, v_uint64 = 0, 
        v_float = 0, v_double = 0, v_pointer = 0x0}}}, {g_type = 0, data = {{
        v_int = 135160512, v_uint = 135160512, v_long = 135160512, 
        v_ulong = 135160512, v_int64 = -4640018405715451200, 
        v_uint64 = 13806725667994100416, v_float = 4.28476507e-34, 
        v_double = -0.026702285281859472, v_pointer = 0x80e62c0}, {
        v_int = -1215191697, v_uint = 3079775599, v_long = -1215191697, 
        v_ulong = 3079775599, v_int64 = 2429736297839, 
        v_uint64 = 2429736297839, v_float = -1.7362383e-05, 
        v_double = 1.2004492332157449e-311, v_pointer = 0xb791a56f}}}, {
    g_type = 0, data = {{v_int = 282, v_uint = 282, v_long = 282, 
        v_ulong = 282, v_int64 = 98784248090, v_uint64 = 98784248090, 
        v_float = 3.95166167e-43, v_double = 4.8805903331527775e-313, 
        v_pointer = 0x11a}, {v_int = 139643248, v_uint = 139643248, 
        v_long = 139643248, v_ulong = 139643248, v_int64 = 13024545136, 
        v_uint64 = 13024545136, v_float = 6.34313649e-34, 
        v_double = 6.4349803044063063e-314, v_pointer = 0x852c970}}}, {
    g_type = 848, data = {{v_int = -1215144912, v_uint = 3079822384, 
        v_long = -1215144912, v_ulong = 3079822384, v_int64 = 3079822384, 
        v_uint64 = 3079822384, v_float = -1.74474844e-05, 
        v_double = 1.5216344352272876e-314, v_pointer = 0xb7925c30}, {
        v_int = 0, v_uint = 0, v_long = 0, v_ulong = 0, v_int64 = 0, 
        v_uint64 = 0, v_float = 0, v_double = 0, v_pointer = 0x0}}}, {
    g_type = 3078742548, data = {{v_int = -1218728768, v_uint = 3076238528, 
        v_long = -1218728768, v_ulong = 3076238528, 
        v_int64 = -5234409956343829312, v_uint64 = 13212334117365722304, 
        v_float = -1.30936387e-05, v_double = -4.9577083459194688e-42, 
        v_pointer = 0xb75bacc0}, {v_int = 135372720, v_uint = 135372720, 
        v_long = 135372720, v_ulong = 135372720, 
        v_int64 = -4640018594693800016, v_uint64 = 13806725479015751600, 
        v_float = 4.38220621e-34, v_double = -0.026701629631503188, 
        v_pointer = 0x8119fb0}}}, {g_type = 0, data = {{v_int = 138957024, 
        v_uint = 138957024, v_long = 138957024, v_ulong = 138957024, 
        v_int64 = -4640018749309038368, v_uint64 = 13806725324400513248, 
        v_float = 6.02803789e-34, v_double = -0.026701093202135762, 
        v_pointer = 0x84850e0}, {v_int = -1216224748, v_uint = 3078742548, 
        v_long = -1216224748, v_ulong = 3078742548, 
        v_int64 = 587598155336507924, v_uint64 = 587598155336507924, 
        v_float = -1.54832742e-05, v_double = 2.2305743021122658e-269, 
        v_pointer = 0xb781e214}}}, {g_type = 139547896, data = {{
        v_int = -1080338536, v_uint = 3214628760, v_long = -1080338536, 
        v_ulong = 3214628760, v_int64 = -5241230261192271976, 
        v_uint64 = 13205513812517279640, v_float = -1.21361065, 
        v_double = -1.7407093033260563e-42, v_pointer = 0xbf9b5798}, {
        v_int = 135372720, v_uint = 135372720, v_long = 135372720, 
        v_ulong = 135372720, v_int64 = 580361922773360560, 
        v_uint64 = 580361922773360560, v_float = 4.38220621e-34, 
        v_double = 7.0651265373902946e-270, v_pointer = 0x8119fb0}}}, {
    g_type = 3214628824, data = {{v_int = -1220324639, v_uint = 3074642657, 
        v_long = -1220324639, v_ulong = 3074642657, 
        v_int64 = 580361925712630497, v_uint64 = 580361925712630497, 
        v_float = -1.16422025e-05, v_double = 7.0651290081674594e-270, 
        v_pointer = 0xb74352e1}, {v_int = 139547896, v_uint = 139547896, 
        v_long = 139547896, v_ulong = 139547896, 
        v_int64 = -4640018543150017288, v_uint64 = 13806725530559534328, 
        v_float = 6.299353e-34, v_double = -0.026701808459923065, 
        v_pointer = 0x85154f8}}}, {g_type = 3079929828, data = {{
        v_int = 135164128, v_uint = 135164128, v_long = 135164128, 
        v_ulong = 135164128, v_int64 = 580443733310206176, 
        v_uint64 = 580443733310206176, v_float = 4.28642546e-34, 
        v_double = 7.1338972221578968e-270, v_pointer = 0x80e70e0}, {
        v_int = -1218728743, v_uint = 3076238553, v_long = -1218728743, 
        v_ulong = 3076238553, v_int64 = 2429732760793, 
        v_uint64 = 2429732760793, v_float = -1.30936614e-05, 
        v_double = 1.2004474856828285e-311, v_pointer = 0xb75bacd9}}}, {
    g_type = 0, data = {{v_int = 282, v_uint = 282, v_long = 282, 
        v_ulong = 282, v_int64 = 98784248090, v_uint64 = 98784248090, 
        v_float = 3.95166167e-43, v_double = 4.8805903331527775e-313, 
        v_pointer = 0x11a}, {v_int = -1215481025, v_uint = 3079486271, 
        v_long = -1215481025, v_ulong = 3079486271, v_int64 = 415396346687, 
        v_uint64 = 415396346687, v_float = -1.68360984e-05, 
        v_double = 2.0523306430600701e-312, v_pointer = 0xb78d3b3f}}}, {
    g_type = 23, data = {{v_int = 1130, v_uint = 1130, v_long = 1130, 
        v_ulong = 1130, v_int64 = -5217354798906473366, 
        v_uint64 = 13229389274803078250, v_float = 1.58346726e-42, 
        v_double = -6.9543114700599421e-41, v_pointer = 0x46a}, {
        v_int = 135126040, v_uint = 135126040, v_long = 135126040, 
        v_ulong = 135126040, v_int64 = -5234409860500693992, 
        v_uint64 = 13212334213208857624, v_float = 4.2689363e-34, 
        v_double = -4.9577694206889151e-42, v_pointer = 0x80ddc18}}}, {
    g_type = 3214629144, data = {{v_int = -1215035033, v_uint = 3079932263, 
        v_long = -1215035033, v_ulong = 3079932263, 
        v_int64 = 580589558984608103, v_uint64 = 580589558984608103, 
        v_float = -1.76473532e-05, v_double = 7.2564796164556225e-270, 
        v_pointer = 0xb7940967}, {v_int = -1218731017, v_uint = 3076236279, 
        v_long = -1218731017, v_ulong = 3076236279, 
        v_int64 = -5234400090803952649, v_uint64 = 13212343982905598967, 
        v_float = -1.30915932e-05, v_double = -4.9639950306300554e-42, 
        v_pointer = 0xb75ba3f7}}}}
	free_me = (GValue *) 0x0
	signal_return_type = 4
	param_values = (GValue *) 0xbf9b56c0
	node = (SignalNode *) 0x8369398
	i = 4
	n_params = 4
	__PRETTY_FUNCTION__ = "IA__g_signal_emit_valist"
#10 0xb7815279 in IA__g_signal_emit (instance=0x812d6f0, signal_id=253, 
    detail=0) at gsignal.c:2243
	var_args = 0xbf9b58ec "¨þE\b`bP\b\005"
#11 0xb6388c08 in na_tray_manager_handle_client_message_message_data (
    xev=0xbf9b5a78, event=0x82a1420, data=0x812d6f0) at na-tray-manager.c:411
	msg = (PendingMessage *) 0x8481ee8
	p = (GList *) 0x845ec30
	len = 8
#12 0xb79449a3 in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#13 0xb79453bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#14 0xb79457bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#15 0xb76ba802 in IA__g_main_context_dispatch (context=0x80ecb00)
    at gmain.c:2045
No locals.
#16 0xb76bd7df in g_main_context_iterate (context=0x80ecb00, block=1, 
    dispatch=1, self=0x80c8b10) at gmain.c:2677
	got_ownership = <value optimized out>
	max_priority = 2147483647
	timeout = 30
	some_ready = 1
	nfds = <value optimized out>
	allocated_nfds = <value optimized out>
	fds = (GPollFD *) 0x836a800
	__PRETTY_FUNCTION__ = "g_main_context_iterate"
#17 0xb76bdb89 in IA__g_main_loop_run (loop=0x8243310) at gmain.c:2881
	got_ownership = -1218731040
	self = (GThread *) 0x80c8b10
	__PRETTY_FUNCTION__ = "IA__g_main_loop_run"
#18 0xb7abc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#19 0x08061d8c in main (argc=3, argv=0xbf9b5d44) at main.c:95
	context = <value optimized out>
	program = (GnomeProgram *) 0x80c9028
#0  0xffffe410 in __kernel_vsysc

---

### Post by raffytaffy on 2007-02-12
i am attempting to solve issue on my own. but i will keep you guys posted for others to see what i have tried. anyways. went to gnome website. grabbed gnome-panel 2.16.2 copiled and installed / rebooted. waitting for problem to repeat. hopefully it does not,

---

### Post by raffytaffy on 2007-02-12
problem persists. im out of options

---

### Post by shareMenaPeace on 2007-02-12
If the new kernel is to buggy boot with the old kernel from GRUB boot loader.

---

### Post by raffytaffy on 2007-02-12
reason i use custom kernel is because the one that came with 6.10 lags real bad on my install. im thinking of maybe using garnome to install gnome 2.17 ... do u guys think that would solve anything?

---

### Post by aidanr on 2007-02-12
sorry didn't read through the whole thread but removing ~/.recently-used.xbel fixed this for me when i tried extracting an iso a while back

---

### Post by ksenos on 2007-02-13
I had the same problem and I can confirm that removing the ~/.recently-used.xbel works. Thanks.

---

### Post by ghetto2ivy on 2007-02-13
Yup, the command:
```
# rm -rf .recently-used.xbel 
```
did the trick.

You must use that exact command, I had tried renaming the file with mv to no avail.

Still many questions unanswered:
Why was it crashing?
Why didn't renaming it work?
What is xbel?

I was a few hours away from doing a complete reinstall. I even installed KDE to get some desktop to work. 

Steven
-Trying to quit my abusive relationship with windows.

---

### Post by tribble222 on 2007-02-13
That command works for me as well, but I just did

```

$ mv .recently-used.xbel .recently-used.xbel.bak

```

and problem solved!

---

### Post by jkzubu on 2007-02-16
> **brk3 said:**
> hi this started happening to me also after an automatic update last night. very frustrating. however i have found the solution!

rm -rf .recently-used.xbel 

hope it works for you too, ubuntu should think twice before putting out dodgy updates this is not the first time something like this has happened. peace

This command works, indeed.  Thank you. -J

---

### Post by kelbizzle on 2007-02-18
Yea this just happend to me a couple hours ago. All I was trying to do is burn the Feisty alt cd. I right clicked on the iso, and selected write to disk. and it's when it started. I was getting the same backtrace as ghetto2ivy. Fortunately the 
```
# rm -rf .recently-used.xbel
```
 Worked for me or I'd still be here scratching my head . Thanks alot. I'll file a bug report in a minute.

---

### Post by maddog39 on 2007-02-24
I already filed a bug report in the GNOME bugzilla.

---

### Post by unebaguettesvp on 2007-03-10
FYI

I had the same exact problem BUT I was NOT working with ISO images. I was working with Archive Manager.

Removing the .recently-used.xbel solved the problem. Thank you for this quick fix!!!

---

### Post by Mike_SMD on 2007-03-15
Same problem for me and the same fix worked.
I was working with an .iso at the time.

Thanks folks, for helping out us new guys!

Mike_SMD

---

