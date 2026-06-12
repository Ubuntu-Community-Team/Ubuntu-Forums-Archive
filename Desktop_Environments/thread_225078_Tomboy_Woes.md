---
title: "Tomboy Woes"
date: 2006-07-29
forum: Desktop Environments
---

### Post by ButteBlues on 2006-07-29
I'm having many issues getting Tomboy working. I've installed/uninstalled several times from the repos to no sort of satisfaction.

I cannot even so much as START Tomboy before it crashes unexpectedly. :/

Running Kubuntu Dapper 6.06 LTS with ubuntu-desktop installed.

---

### Post by sethmahoney on 2006-07-29
Do you get any error messages when you start tomboy from the terminal?

---

### Post by Ziox on 2006-07-29
remove tomboy and try:

sudo aptitude install tomboy

what kinds of error do you get when starting tomboy?

---

### Post by ButteBlues on 2006-07-29
Here's a copy and paste of what happens when I run it in a terminal:

> ************$ tomboy
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (Tomboy:31959): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=4)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy).


** (Tomboy:31959): WARNING **: The class DBus.Service could not be loaded, used in dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKeyToken=9eef2692033670f5

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in Tomboy.Tomboy:Main (string[]) <0xffffffff>
in Tomboy.Tomboy:Main (string[]) <0x117>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xae0c3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e7d43f]
        /usr/lib/libmono.so.0 [0xb7e3f03e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7e3b338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7e5b094]
        /usr/lib/libmono.so.0 [0xb7e5c04d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7ebf225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e93b1f]
        [0xb7ada032]
        [0xb737b823]
        /usr/lib/libmono.so.0 [0xb7e5c438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7ebeeed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7ec1a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7ec4bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e6eb5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e6f54f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7c0aea2]
        mono [0x8048459]
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Which results in the Gnome pop-up asking for a bug report (which doesn't work anyways).

---

### Post by ButteBlues on 2006-07-29
Bump.

---

### Post by Ziox on 2006-07-29
i think you need to install mono...do

sudo aptitude install mono

---

### Post by ButteBlues on 2006-07-29
I've tried uninstalling and reinstalling tomboy and mono a few times. For kicks, here's the terminal readout for the installation of mono and tomboy:

> ~$ sudo aptitude install mono
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libgdiplus
The following NEW packages will be installed:
  libgdiplus mono
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 248kB of archives. After unpacking 631kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main mono 1.1.13.6-0ubuntu3 [1208B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libgdiplus 1.1.13.6-0ubuntu2 [246kB]
Fetched 248kB in 2s (100kB/s)
Selecting previously deselected package libgdiplus.
(Reading database ... 123435 files and directories currently installed.)
Unpacking libgdiplus (from .../libgdiplus_1.1.13.6-0ubuntu2_i386.deb) ...
Selecting previously deselected package mono.
Unpacking mono (from .../mono_1.1.13.6-0ubuntu3_i386.deb) ...
Setting up libgdiplus (1.1.13.6-0ubuntu2) ...
Setting up mono (1.1.13.6-0ubuntu3) ...

~$ sudo aptitude install tomboy
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  tomboy
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/148kB of archives. After unpacking 1061kB will be used.
Writing extended state information... Done
Selecting previously deselected package tomboy.
(Reading database ... 123444 files and directories currently installed.)
Unpacking tomboy (from .../tomboy_0.3.5-1ubuntu3_i386.deb) ...
Setting up tomboy (0.3.5-1ubuntu3) ...

** (process:7691): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

$

---

### Post by ButteBlues on 2006-07-29
Any help would be immensely appreciated - I'm stuck using horrid items like kNotes and Zim until this is resolved. :/

---

### Post by metalheart on 2006-07-29
run
```
sudo apt-get update
```
and then
```
sudo apt-get install libdbus-1-cil
```
Maybe that helps

---

### Post by ButteBlues on 2006-07-29
```
~$ sudo apt-get install libdbus-1-cil
Reading package lists... Done
Building dependency tree... Done
libdbus-1-cil is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And trying to run tomboy again:

```
~$ tomboy
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.

[B]** (Tomboy:5847): WARNING **: The following assembly referenced from /usr/lib/to
mboy/Tomboy.exe could not be loaded:
     Assembly:   dbus-sharp    (assemblyref_index=4)
     Version:    0.60.0.0
     Public Key: 9eef2692033670f5
The assembly was not found in the Global Assembly Cache, a path listed in the MO
NO_PATH environment variable, or in the location of the executing assembly (/usr
/lib/tomboy).


** (Tomboy:5847): WARNING **: The class DBus.Service could not be loaded, used i
n dbus-sharp, Version=0.60.0.0, Culture=neutral, PublicKeyToken=9eef2692033670f5[/B]

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in Tomboy.Tomboy:Main (string[]) <0xffffffff>
in Tomboy.Tomboy:Main (string[]) <0x117>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,i
ntptr,intptr,intptr) <0xae0c3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e2f43f]
        /usr/lib/libmono.so.0 [0xb7df103e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7ded338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7e0d094]
        /usr/lib/libmono.so.0 [0xb7e0e04d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7e71225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7e45b1f]
        [0xb7a8c032]
        [0xb732d823]
        /usr/lib/libmono.so.0 [0xb7e0e438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e70eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7e73a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7e76bf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e20b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e2154f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7bbcea2]
        mono [0x8048459]

```

---

### Post by ButteBlues on 2006-07-30
Help?

---

### Post by ButteBlues on 2006-07-30
/el sigh.

---

### Post by Ziox on 2006-07-30
look...it's not that we dont want to help you, its just the most knowledgable person has not read your thread yet.  Most of the time, many threads are unanswered or let open is because that no one (very few people) knows HOW to solve the problem...

here's something to work with: if TOMBOY is installed then do tis:

sudo aptitude purge tomboy

and maybe you should purge mono as well...

sudo aptitude purge mono

after that...

sudo aptitude install tomboy

i'm not sure if this would work, but its worth a try.

---

### Post by kaput on 2006-07-30
If the purge does not work, I'd recommend filing a bug. 

Generally, I always try to find an answer to the problem in the forums first as the developers/maintainers are generally busy enough. I'd also recommend trying out the Ubuntu IRC channels, though I've often not had luck finding any help there.

However, you may be experiencing an actual bug. If so, help out yourself *and* the community, and file a bug report. Taking the time to do so and keeping up with developers' requests for info may get your problem solved and help make Ubuntu a better distrobution.

[https://launchpad.net/distros/ubuntu/+bugs/](https://launchpad.net/distros/ubuntu/+bugs/)

---

