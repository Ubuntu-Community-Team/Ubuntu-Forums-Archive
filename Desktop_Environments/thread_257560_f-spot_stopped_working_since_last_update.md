---
title: "f-spot stopped working since last update"
date: 2006-09-14
forum: Desktop Environments
---

### Post by dietrying on 2006-09-14
f-spot doesn't start anymore on my system

---

### Post by Ramses de Norre on 2006-09-14
Whats the error when you start it from terminal? (the command is f-spot)

---

### Post by dietrying on 2006-09-14
got this:

** (/usr/lib/f-spot/f-spot.exe:6109): WARNING **: The following assembly referen ced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=8)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:6109): WARNING **: The class DBus.Connection coul d not be loaded, used in dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKe yToken=9eef2692033670f5

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in FSpot.Driver:Main (string[]) <0xffffffff>
in FSpot.Driver:Main (string[]) <0x298>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,i ntptr,intptr,intptr) <0xbd8c3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7dfe43f]
        /usr/lib/libmono.so.0 [0xb7dc003e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7dbc338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7ddc094]
        /usr/lib/libmono.so.0 [0xb7ddd04d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7e40225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e14b1f]
        [0xb7a54032]
        [0xb7204823]
        /usr/lib/libmono.so.0 [0xb7ddd438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e3feed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7e42a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7e45bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7defb5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7df054f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7b8cea2]
        mono [0x8048459]



could this maybe have something to do with the installation of bmpx? anyway i kicked out the bmpx sources of my apt- sources.list and tried to reinstall either f-spot and mono....doesn't change anything? any idea?

---

### Post by dietrying on 2006-09-15
anyone with a good idea? Or am I the only one with the problem?:rolleyes:

---

### Post by fantan on 2006-09-15
Hi, 

Also exactly the same error message appears on my system after update. I sent a notification to developers by Bug Buddy.

Now I'll wait the fix.

fantan

---

### Post by nikkiana on 2006-09-15
I'm having problems with f-spot as well... but I'm getting a totally different set of errors when I run via console. 

Found active FSpot server: FSpot.Core.Proxy
DBus.DBusException: No reply within specified time
in <0x0011c> DBus.Message:SendWithReplyAndBlock ()
in <0x00062> FSpot.Core.Proxy:Organize ()
in <0x00628> FSpot.Driver:Main (System.String[] args)
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: No such file or directory

---

### Post by CodyJarrett on 2006-11-12
also got the SIGSEGV error. Tried re-installing everything with no luck. Installed the [CVS version]("http://f-spot.org/How_To_Build_from_CVS") with no problems. Anyone know why this error occurs?

---

### Post by pwaller on 2006-11-12
Also seeing the same problem here.

---

### Post by pwaller on 2006-11-12
I moved .gnome2/f-spot away then it started nicely. (Though I don't have any old photo archives, if you want to retain them see this bug [https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910](https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910) )

---

### Post by WA4MOE on 2007-10-08
I also have f-spot errors.  f-spot has encountered and error and must close. It occurs when I am deleting some of the hundreds of jpgs that I imported in error.
Any ideas?
Moses

---

### Post by underdog512 on 2007-10-24
F-spot is not starting for me either.  However this is all I am getting in the terminal.


Initializing Mono.Addins
Found active FSpot server: /org/gnome/FSpot/Core

then its just kinda hangs there.

---

