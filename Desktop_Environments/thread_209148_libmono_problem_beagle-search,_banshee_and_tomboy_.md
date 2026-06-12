---
title: "libmono problem: beagle-search, banshee and tomboy nonfunctional"
date: 2006-07-04
forum: Desktop Environments
---

### Post by cptnapalm on 2006-07-04
A couple of days ago, I noticed that beagle-search was not working.  It gave the following output when run from the commandline:
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x400a243f]
        /usr/lib/libmono.so.0 [0x4006403e]
        /lib/libpthread.so.0 [0x4029d5ca]
        [0xffffe440]
        [0x407bc58a]
        [0x407bc529]
        [0x407bc173]
        [0x407b2816]
        /usr/lib/libmono.so.0 [0x40081438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e3eed]
        /usr/lib/libmono.so.0(mono_runtime_class_init+0x13f) [0x400e612f]
        /usr/lib/libmono.so.0 [0x4008116e]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0x400e4225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0x400b8b1f]
        [0x4053a032]
        [0x407bbe12]
        [0x407bbdb1]
        [0x407b9ecc]
        [0x407b9e3e]
        [0x407b941c]
        [0x407b208d]
        [0x407b1823]
        /usr/lib/libmono.so.0 [0x40081438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e3eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0x400e6a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x400e9bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x40093b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0x4009454f]
        /lib/libc.so.6(__libc_start_main+0xa3) [0x4032c31f]
        beagle-search [0x8048459]


Today, I went to run tomboy and it did the same thing:

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x400a243f]
        /usr/lib/libmono.so.0 [0x4006403e]
        /lib/libpthread.so.0 [0x4029d5ca]
        [0xffffe440]
        [0x407c0ee2]
        [0x407c0e81]
        [0x407c0acb]
        [0x407bc456]
        /usr/lib/libmono.so.0 [0x40081438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e3eed]
        /usr/lib/libmono.so.0(mono_runtime_class_init+0x13f) [0x400e612f]
        /usr/lib/libmono.so.0 [0x4008116e]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0x400e4225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0x400b8b1f]
        [0x4053a032]
        [0x407c075a]
        [0x407c06f9]
        [0x407be4f4]
        [0x407be466]
        [0x407bd16c]
        [0x407bbaa9]
        [0x407bb823]
        /usr/lib/libmono.so.0 [0x40081438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e3eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0x400e6a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x400e9bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x40093b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0x4009454f]
        /lib/libc.so.6(__libc_start_main+0xa3) [0x4032c31f]
        mono [0x8048459]
Aborted


I had intended to use tomboy to take some notes on an odd idea i had to have apache2 accesible to zeroconf/avahi.

Banshee does the same thing.

The output does nothing to help me identify the problem outside of the obvious: something is wrong with libmono.so.0

Anyone have any ideas?

---

### Post by Ptero-4 on 2006-07-04
Have you updated mono? Or the apps that fail? I ask b/c it sounds like an incompatibility there.

---

### Post by cptnapalm on 2006-07-04
Synaptic reports that the installed version of libmono0 is 1.1.13, which is the most recent version available from Ubuntu's repositories.

Tomboy, beagle and banshee are the most up-to-date versions, with tomboy also coming from Ubuntu's reps.

I tried out tomboy and beagle on a fresh account, just to see if perhaps it was something in my configuration, but that was a no go as well.

---

### Post by darge0flex on 2006-07-07
Same problem here, also with f-spot. A few days ago was an update of some (dont remember exactly) *cil*-libraries.

---

### Post by rwabel on 2006-07-08
same for me, after the mono update a few days ago

---

### Post by eljaco on 2006-08-22
Anybody get this fixed? I can't run Banshee because of the same problem:
```
~$ banshee 

** (/usr/lib/banshee/banshee.exe:10086): WARNING **: The following assembly referenced from /usr/lib/banshee/banshee.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=14)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:10086): WARNING **: The class DBus.Connection could not be loaded, used in dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKeyToken=9eef2692033670f5

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:

in Banshee.BansheeEntry:DetectInstanceAndDbus () <0xffffffff>
in Banshee.BansheeEntry:DetectInstanceAndDbus () <0x12>
in Banshee.BansheeEntry:Startup (string[]) <0x4fd>
in Banshee.BansheeEntry:Main (string[]) <0xa>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0x656c3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e7443f]
        /usr/lib/libmono.so.0 [0xb7e3603e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7e32338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7e52094]
        /usr/lib/libmono.so.0 [0xb7e5304d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7eb6225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e8ab1f]
        [0xb7abe032]
        [0xb77fcf86]
        [0xb77fc89b]
        [0xb77fc823]
        /usr/lib/libmono.so.0 [0xb7e53438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7eb5eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7eb8a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7ebbbf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e65b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e6654f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7bedea2]
        banshee [0x8048459]
Aborted

```

---

### Post by louis_nichols on 2006-09-18
is this issue not fixed yet? I have the same problem...

---

### Post by cptnapalm on 2006-09-18
Eventually what I did was purge the libmono packages (and just uninstalled the apps) and then reinstalled everything.  It worked.

Stupid.  But it worked.

---

### Post by bovine on 2006-09-18
I also re-installed libmono packages plus beagle and tomboy and all are working now.

---

### Post by louis_nichols on 2006-09-19
I've tried re-installing libmono plus libc6 and libglib-2 (following a thread) and it didn't work. I'll try your suggestions too. thanks for the reply.

---

### Post by ButteBlues on 2006-09-19
> **louis_nichols said:**
> I've tried re-installing libmono plus libc6 and libglib-2 (following a thread) and it didn't work. I'll try your suggestions too. thanks for the reply.
If you installed BMPX, the BMPX repo has a customized version of mono that breaks Tomboy and other mono apps.

---

### Post by louis_nichols on 2006-09-20
> **a simple façade said:**
> If you installed BMPX, the BMPX repo has a customized version of mono that breaks Tomboy and other mono apps.

Oh! come to think of it, i did install mpx at one point. i uninstalled it, but i don't think i removed the repo from sources.list.

the above methods didn't work for me :( so this is kinda my last hope...

---

### Post by ButteBlues on 2006-09-21
> **louis_nichols said:**
> Oh! come to think of it, i did install mpx at one point. i uninstalled it, but i don't think i removed the repo from sources.list.

the above methods didn't work for me :( so this is kinda my last hope...
Yeah, remove the repo, rollback your mono to the earliest deb in /var/cache/apt/archives, and then try to $ sudo apt-get dist-upgrade

---

### Post by louis_nichols on 2006-09-22
It did indeed work. Thanx you all!

---

### Post by kochab on 2006-09-24
Hi,
I've the same problem on dapper with tomboy and f-spot
here is the error of f-spot

```
** (/usr/lib/f-spot/f-spot.exe:8250): WARNING **: The following assembly referen
ced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=8)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MO
NO_PATH environment variable, or in the location of the executing assembly (/usr
/lib/f-spot).


** (/usr/lib/f-spot/f-spot.exe:8250): WARNING **: The class DBus.Connection coul
d not be loaded, used in dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKe
yToken=9eef2692033670f5

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:

in FSpot.Driver:Main (string[]) <0xffffffff>
in FSpot.Driver:Main (string[]) <0x298>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,i
ntptr,intptr,intptr) <0xbcdc3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e6543f]
        /usr/lib/libmono.so.0 [0xb7e2703e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7e23338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7e43094]
        /usr/lib/libmono.so.0 [0xb7e4404d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7ea7225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e7bb1f]
        [0xb7ac3032]
        [0xb7276823]
        /usr/lib/libmono.so.0 [0xb7e44438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7ea6eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7ea9a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7eacbf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e56b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e5754f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7bf2ea2]
        mono [0x8048459]

```

could someone help?
thanks

---

### Post by kochab on 2006-09-24
SOLVED
I've purged libmono and all its dependancies.
reinstalled f-spot and now it works

---

### Post by mazirian on 2006-09-25
@kochab: What did you purge other than libmono0?  I purged libmono0, whereupon apt also removed beagle, beagle-backend-evolution, cowbell, f-spot, libgconf2.0-cil, libgnome2.0-cil, libmono-dev, and mono-jit.  Thereafter, I install f-spot cowbell and the beagle related stuff (and all their dependancies).  But I still get segfaults when running any mono apps.

---

### Post by mazirian on 2006-09-25
Btw, I later ran:

```

sudo aptitude purge libmono0 mono-classlib-1.0 mono-common

```

Which removed libmono0 mono-classlib-1.0 mono-common beagle beagle-backend-evolution cowbell f-spot libdbus-1-cil libevolution-cil libgconf2.0-cil

After reinstalling the above, no joy.  All of the above packages are installed from the dapper repositories according to apt-cache policy.

Any other ideas?  Here is the stack trace:

```

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

	/usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0x400a643f]
	/usr/lib/libmono.so.0 [0x4006803e]
	/lib/libpthread.so.0 [0x402a15ca]
	[0xffffe440]
	[0x408b20fa]
	[0x408b2099]
	[0x408b1ce3]
	[0x408ae84e]
	/usr/lib/libmono.so.0 [0x40085438]
	/usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e7eed]
	/usr/lib/libmono.so.0(mono_runtime_class_init+0x13f) [0x400ea12f]
	/usr/lib/libmono.so.0 [0x4008516e]
	/usr/lib/libmono.so.0(mono_compile_method+0x24) [0x400e8225]
	/usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0x400bcb1f]
	[0x4053e032]
	[0x408b1972]
	[0x408b1911]
	[0x408af70c]
	[0x408af67e]
	[0x408ae2f4]
	[0x408ad3cd]
	[0x408ac823]
	/usr/lib/libmono.so.0 [0x40085438]
	/usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0x400e7eed]
	/usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0x400eaa88]
	/usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0x400edbf0]
	/usr/lib/libmono.so.0(mono_jit_exec+0x90) [0x40097b5e]
	/usr/lib/libmono.so.0(mono_main+0x962) [0x4009854f]
	/lib/libc.so.6(__libc_start_main+0xa3) [0x4033031f]
	mono [0x8048459]
/usr/bin/f-spot: line 8:  7943 Aborted                 mono $MONO_OPTIONS /usr/lib/f-spot/f-spot.exe "$@"

```

---

### Post by mazirian on 2006-09-25
n/m. Just needed to reinstall libc6.

---

### Post by kbro237 on 2006-10-11
the bmpx repos were the problem for me as well. all i did was get rid of the repos and the use aptitude to remove libdbus-1-cil, which downgraded to the previous libdbus

---

