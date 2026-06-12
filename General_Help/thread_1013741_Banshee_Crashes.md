---
title: "Banshee Crashes"
date: 2008-12-17
forum: General Help
---

### Post by civillian on 2008-12-17
I just installed the latest version of Banshee from the banshee repos, and now, whenever I start it up, I get the following error message

> Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.


which is preceded by this

```
 [Info  10:59:53.515] Running Banshee 1.4.1
Add-in could not be loaded: The required addin 'Banshee.Core,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Banshee.Core,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  10:59:55.066] Caught an exception - The required addin 'Banshee.Core,1.0' is not installed. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  10:59:55.066] Extension `/Banshee/ServiceManager/Service/__nid_9' not started: The required addin 'Banshee.Core,1.0' is not installed.
Stacktrace:

  at (wrapper managed-to-native) Banshee.GStreamer.Service.gstreamer_test_pipeline (intptr) <0x00004>
  at (wrapper managed-to-native) Banshee.GStreamer.Service.gstreamer_test_pipeline (intptr) <0xffffffff>
  at Banshee.GStreamer.Service.TestPipeline (string) <0x00047>
  at Banshee.GStreamer.Service.OnTestMediaProfile (object,Banshee.MediaProfiles.TestProfileArgs) <0x00142>
  at Banshee.MediaProfiles.MediaProfileManager.OnTestProfile (Banshee.MediaProfiles.Profile) <0x0004a>
  at Banshee.MediaProfiles.MediaProfileManager.TestAll () <0x00044>
  at Banshee.GStreamer.Service.Banshee.ServiceStack.IExtensionService.Initialize () <0x00171>
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode) <0x00101>
  at Banshee.ServiceStack.ServiceManager.Run () <0x00119>
  at Banshee.ServiceStack.Application.Run () <0x00059>
  at Banshee.Gui.GtkBaseClient.Initialize (bool) <0x00193>
  at Banshee.Gui.GtkBaseClient..ctor (bool,string) <0x00026>
  at Banshee.Gui.GtkBaseClient..ctor () <0x00019>
  at Nereid.Client..ctor () <0x0000d>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[]) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[]) <0xffffffff>
  at System.Reflection.MonoCMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0007f>
  at System.Reflection.MonoCMethod.Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0001c>
  at System.Reflection.ConstructorInfo.Invoke (object[]) <0x00035>
  at System.Activator.CreateInstance (System.Type,bool) <0x00114>
  at System.Activator.CreateInstance (System.Type) <0x0000c>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00012>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00039>
  at Banshee.Gui.GtkBaseClient.Startup (string[]) <0x000a6>
  at Nereid.Client.Main (string[]) <0x0000a>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7fca410]
	/usr/lib/gstreamer-0.10/libgstaudioconvert.so [0xb3f1ffe3]
	/usr/lib/libgstbase-0.10.so.0 [0xb4c1f795]
	/usr/lib/libgstbase-0.10.so.0 [0xb4c231ed]
	/usr/lib/libgstreamer-0.10.so.0 [0xb4697ef7]
	/usr/lib/libgstreamer-0.10.so.0(gst_pad_link+0x4f8) [0xb469e6e8]
	/usr/lib/libgstreamer-0.10.so.0 [0xb46c557b]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_link_pads+0x5a1) [0xb46c6a61]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_link_pads_filtered+0x2ca) [0xb46c774a]
	/usr/lib/libgstreamer-0.10.so.0(_gst_parse_launch+0x7c5) [0xb46df525]
	/usr/lib/libgstreamer-0.10.so.0(gst_parse_launch_full+0xd7) [0xb46d0a77]
	/usr/lib/libgstreamer-0.10.so.0(gst_parse_launch+0x34) [0xb46d0af4]
	/usr/lib/banshee-1/libbanshee.so(gstreamer_test_pipeline+0x30) [0xb485e4b0]
	[0xb3f3650b]
	[0xb3f364a8]
	[0xb3f4a76b]
	[0xb3f4a5db]
	[0xb3f4a275]
	[0xb3f49c82]
	[0xb418915a]
	[0xb626c1f2]
	[0xb6268f12]
	[0xb6d188a4]
	[0xb6d18687]
	[0xb6d1864a]
	[0xb6d1861e]
	[0xb6d185a9]
	banshee-1(mono_runtime_invoke_array+0x2c3) [0x809e7c3]
	banshee-1 [0x80a6973]
	[0xb79508ad]
	[0xb7950648]
	[0xb79505bd]
	[0xb7950576]
	[0xb794f325]
	[0xb794f1fd]
	[0xb6d1854b]
	[0xb6d18453]
	[0xb6d1835a]
	[0xb6ef9d3f]
	[0xb6ef5f0b]
	[0xb6ef5e9b]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6ef5e45]
	[0xb6ef5d51]
	[0xb6ef5c4a]
	[0xb6ef5bf6]
	[0xb6ef5b6d]
	[0xb6ef5b2a]
	[0xb6ef4b9e]
	[0xb794e3b9]
	[0xb794e1be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d49685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d076d0 (LWP 7486)]
[New Thread 0xb38fcb90 (LWP 7500)]
[New Thread 0xb39fdb90 (LWP 7499)]
[New Thread 0xb3afeb90 (LWP 7498)]
[New Thread 0xb3bffb90 (LWP 7496)]
[New Thread 0xb42ffb90 (LWP 7494)]
[New Thread 0xb6035b90 (LWP 7490)]
[New Thread 0xb73c2b90 (LWP 7489)]
[New Thread 0xb73e6b90 (LWP 7487)]
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
0xb7fca430 in __kernel_vsyscall ()
  9 Thread 0xb73e6b90 (LWP 7487)  0xb7fca430 in __kernel_vsyscall ()
  8 Thread 0xb73c2b90 (LWP 7489)  0xb7fca430 in __kernel_vsyscall ()
  7 Thread 0xb6035b90 (LWP 7490)  0xb7fca430 in __kernel_vsyscall ()
  6 Thread 0xb42ffb90 (LWP 7494)  0xb7fca430 in __kernel_vsyscall ()
  5 Thread 0xb3bffb90 (LWP 7496)  0xb7fca430 in __kernel_vsyscall ()
  4 Thread 0xb3afeb90 (LWP 7498)  0xb7fca430 in __kernel_vsyscall ()
  3 Thread 0xb39fdb90 (LWP 7499)  0xb7fca430 in __kernel_vsyscall ()
  2 Thread 0xb38fcb90 (LWP 7500)  0xb7fca430 in __kernel_vsyscall ()
  1 Thread 0xb7d076d0 (LWP 7486)  0xb7fca430 in __kernel_vsyscall ()

Thread 9 (Thread 0xb73e6b90 (LWP 7487)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec4906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb73c2b90 (LWP 7489)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec1075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb6035b90 (LWP 7490)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d3013 in ?? ()
#7  0xb624197a in ?? ()
#8  0xb6241823 in ?? ()
#9  0xb62405c0 in ?? ()
#10 0xb7950901 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb42ffb90 (LWP 7494)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb3bffb90 (LWP 7496)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb4145ebf in ?? ()
#7  0xb4145b57 in ?? ()
#8  0xb414585f in ?? ()
#9  0xb4819f1e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb3afeb90 (LWP 7498)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb4145ebf in ?? ()
#7  0xb4145b57 in ?? ()
#8  0xb414585f in ?? ()
#9  0xb4819f1e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb39fdb90 (LWP 7499)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb4145ebf in ?? ()
#7  0xb4145b57 in ?? ()
#8  0xb414585f in ?? ()
#9  0xb4819f1e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb38fcb90 (LWP 7500)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7ec13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7ebd50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7e147ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d076d0 (LWP 7486)):
#0  0xb7fca430 in __kernel_vsyscall ()
#1  0xb7e0cc01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f4698b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f46d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817b565 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
#7  0x0ff1daf8 in ?? ()
#8  0xb3f1ffe3 in ?? () from /usr/lib/gstreamer-0.10/libgstaudioconvert.so
#9  0xb4c1f795 in ?? () from /usr/lib/libgstbase-0.10.so.0
#10 0xb4c231ed in ?? () from /usr/lib/libgstbase-0.10.so.0
#11 0xb4697ef7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0xb469e6e8 in gst_pad_link () from /usr/lib/libgstreamer-0.10.so.0
#13 0xb46c557b in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0xb46c6a61 in gst_element_link_pads () from /usr/lib/libgstreamer-0.10.so.0
#15 0xb46c774a in gst_element_link_pads_filtered ()
   from /usr/lib/libgstreamer-0.10.so.0
#16 0xb46df525 in _gst_parse_launch () from /usr/lib/libgstreamer-0.10.so.0
#17 0xb46d0a77 in gst_parse_launch_full () from /usr/lib/libgstreamer-0.10.so.0
#18 0xb46d0af4 in gst_parse_launch () from /usr/lib/libgstreamer-0.10.so.0
#19 0xb485e4b0 in gstreamer_test_pipeline ()
   from /usr/lib/banshee-1/libbanshee.so
#20 0xb3f3650b in ?? ()
#21 0xb3f364a8 in ?? ()
#22 0xb3f4a76b in ?? ()
#23 0xb3f4a5db in ?? ()
#24 0xb3f4a275 in ?? ()
#25 0xb3f49c82 in ?? ()
#26 0xb418915a in ?? ()
#27 0xb626c1f2 in ?? ()
#28 0xb6268f12 in ?? ()
#29 0xb6d188a4 in ?? ()
#30 0xb6d18687 in ?? ()
#31 0xb6d1864a in ?? ()
#32 0xb6d1861e in ?? ()
#33 0xb6d185a9 in ?? ()
#34 0x0809e7c3 in mono_runtime_invoke_array ()
#35 0x080a6973 in ?? ()
#36 0xb79508ad in ?? ()
#37 0xb7950648 in ?? ()
#38 0xb79505bd in ?? ()
#39 0xb7950576 in ?? ()
#40 0xb794f325 in ?? ()
#41 0xb794f1fd in ?? ()
#42 0xb6d1854b in ?? ()
#43 0xb6d18453 in ?? ()
#44 0xb6d1835a in ?? ()
#45 0xb6ef9d3f in ?? ()
#46 0xb6ef5f0b in ?? ()
#47 0xb6ef5e9b in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0xb6ef5e45 in ?? ()
#50 0xb6ef5d51 in ?? ()
#51 0xb6ef5c4a in ?? ()
#52 0xb6ef5bf6 in ?? ()
#53 0xb6ef5b6d in ?? ()
#54 0xb6ef5b2a in ?? ()
#55 0xb6ef4b9e in ?? ()
#56 0xb794e3b9 in ?? ()
#57 0xb794e1be in ?? ()
#58 0x0809cb76 in mono_runtime_exec_main ()
#59 0x0809d19b in mono_runtime_run_main ()
#60 0x0805af2e in mono_main ()
#61 0x0805a432 in ?? ()
#62 0xb7d49685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#63 0x0805a371 in ?? ()
#0  0xb7fca430 in __kernel_vsyscall ()

```

Can anyone shed any light on what might fix this? or at least what the error messages mean?

---

### Post by alternatealias on 2008-12-17
From the error log, at the very top I see:

<blockquote>Add-in could not be loaded: The required addin 'Banshee.Core,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Banshee.Core,1.0' is not installed.
</blockquote>

I suspect you don't have all of the Banshee packages properly installed.

---

