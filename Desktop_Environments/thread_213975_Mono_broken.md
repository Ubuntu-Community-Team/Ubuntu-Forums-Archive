---
title: "Mono broken?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by vaskark on 2006-07-12
Several mono apps are not working for me anymore, like banshee and muine. Here is the Banshee console output:

> ** (/usr/lib/banshee/banshee.exe:18385): WARNING **: The following assembly referenced from /usr/lib/banshee/banshee.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=14)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee).


** (/usr/lib/banshee/banshee.exe:18385): WARNING **: The class DBus.Connection could not be loaded, used in dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKeyToken=9eef2692033670f5

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
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0x65ac3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e4243f]
        /usr/lib/libmono.so.0 [0xb7e0403e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7e00338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7e20094]
        /usr/lib/libmono.so.0 [0xb7e2104d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7e84225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e58b1f]
        [0xb7a88032]
        [0xb77c6f86]
        [0xb77c689b]
        [0xb77c6823]
        /usr/lib/libmono.so.0 [0xb7e21438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e83eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7e86a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7e89bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e33b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e3454f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7bb7ea2]
        banshee [0x8048459]
Abort 
Anyone else seeing this? I tried re-installing mono but that didn't do the trick.

-- vaskark

---

### Post by jordilin on 2006-07-12
This is not normal. If you have the original mono provided by a fresh Dapper installation there should not be any problem. Did you upgraded mono or did you do an update of the mono packages?

---

### Post by vaskark on 2006-07-12
> **jordilin said:**
> This is not normal. If you have the original mono provided by a fresh Dapper installation there should not be any problem. Did you upgraded mono or did you do an update of the mono packages?
Not sure what you mean by that last part. All mono packages I have are from the dapper repos, and I reinstalled them in synaptic (by searching for packages with 'mono' in the name). Things were fine a few days ago :-?

---

### Post by jordilin on 2006-07-12
I mean that Ubuntu provides updates for its packages and perhaps you are installing an updated version of the original Dapper repos, that may crash with some sort of dependency. Perhaps is something related to the message:
Assembly: dbus-sharp (assemblyref_index=14)
Version: 0.60.0.0
I think there must be any incompatibility between package versions. Try to make sure you install from the main restricted universe and multiverse and not from the updates source. I don't know if there are any updates from the mono packages, I'll have a look at home later. Meanwhile, let's see if there is someone who has run into the same problem.

---

### Post by RAOF on 2006-07-12
What is the result of running **aptitude show libdbus-1-cil**?  It should be installed, and version 0.6.*something*-ubuntu*something*.  If it isn't installed, try installing it :)

---

### Post by rwabel on 2006-07-13
I do have the same issue and did not install any other mono packages. About 1 week ago mono packages got updated.
Here is the output:
> rwabel@ubuntu:~$ aptitude show libdbus-1-cil
Package: libdbus-1-cil
State: installed
Automatically installed: no
Version: 0.62-1ubuntu1
Priority: optional
Section: libs
Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Uncompressed Size: 299k
Depends: cli-common (>= 0.4.0), mono-classlib-1.0 (>= 1.0), libdbus-glib-1-2
Conflicts: libdbus-cil
Replaces: libdbus-cil
Description: CLI binding for D-BUS interprocess messaging system
 D-BUS is a message bus, used for sending messages between applications. Conceptually, it fits somewhere in
 between raw sockets and CORBA in terms of complexity.

 This package provides a CLI binding to D-BUS, for use with Mono or other ECMA CLI implementations.

 See the dbus description for more information about D-BUS in general.


---

### Post by rwabel on 2006-07-13
as RAOF said before we have a newer version. The one I've is from: > Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>


Just downgrade to the 0.60 and everything works fine then.

---

### Post by vaskark on 2006-07-18
This is my output:

aptitude show libdbus-1-cil
Package: libdbus-1-cil
New: yes
State: installed
Automatically installed: no
Version: 0.62-bmp1ubuntu1
Priority: optional
Section: libs
Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Uncompressed Size: 299k
Depends: cli-common (>= 0.4.0), mono-classlib-1.0 (>= 1.0), libdbus-glib-1-2
Conflicts: libdbus-cil
Replaces: libdbus-cil
Description: CLI binding for D-BUS interprocess messaging system
 D-BUS is a message bus, used for sending messages between applications.
 Conceptually, it fits somewhere in between raw sockets and CORBA in terms of
 complexity.

 This package provides a CLI binding to D-BUS, for use with Mono or other ECMA
 CLI implementations.

 See the dbus description for more information about D-BUS in general.

I currently am using a repo for bmpx (svn), along with the dapper updates repo + multiverse + universe. This prob was there before I subscribed to the bmpx repo though. So how do I proceed from here? Should I deactivate the dapper updates repo? I'm kinda in unfamiliar territory right now.:-?

---

### Post by rwabel on 2006-07-18
you can force to upgrade/downgrade to another version. choose the correct version and the lock that version in synaptic.

---

### Post by RAOF on 2006-07-18
> **vaskark said:**
> ...
Version: 0.62-bmp1ubuntu1
...

There's your problem. It's a BMP packaged newer version of dbus-sharp.  To revert, try
```
sudo aptitiude libdbus-1-cil=0.60-6ubuntu8
```

---

### Post by Confuse on 2006-07-25
I have the same problem, bmp unknowingly (by me) installed a new dbus and friends. When I try to revert back, it wants to uninstall a ton of other apps. Is there anything I can do? Suggestions are higly appreciated!

P.S. Also, I received a dbus 0.62 update via the official dapper repos and they broke my compiled banshee and other compiled mono apps. Even if I recompile it, it still looks for dbus 0.60. Does this occur with the apps in the official dapper repos too?

---

### Post by RAOF on 2006-07-25
> **Confuse said:**
> ...
P.S. Also, I received a dbus 0.62 update via the official dapper repos and they broke my compiled banshee and other compiled mono apps. Even if I recompile it, it still looks for dbus 0.60. Does this occur with the apps in the official dapper repos too?

Really?  I've got the dapper-updates repository enabled, and I've still got libdbus-1-cil 0.60-6ubuntu8 installed.  What's the version of your libdbus-1-cil?  I'd suspect that the new DBUS has come from some other repository.

---

### Post by Confuse on 2006-07-26
You're probably right. I had one repo I didn't recognize and it might have been from debian unstable or something else to download the w32 codecs. Has anyone found a solution to this?

---

### Post by rwabel on 2006-07-26
either remove the repo or downgrade to the correct version and then lock that version, so next time it won't get upgraded again

---

### Post by Confuse on 2006-07-27
I tried reverting all dbus and mono related packages but I still get an error that does not mention mono. Grrrrr!

---

### Post by rwabel on 2006-07-27
what kind of error? no more dbus error then?

---

