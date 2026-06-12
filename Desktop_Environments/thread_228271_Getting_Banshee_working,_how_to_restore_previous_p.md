---
title: "Getting Banshee working, how to restore previous packages?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Robvdl on 2006-08-02
I have just found out about the Banshee music player program, for the Mono framework and it looked really awesome, so I'd thought I'd give it a go, however the program won't start.

I do have a fair idea why this might be I think, the other week I was looking for a suitable source code editor for my Pascal stuff and found a gnome program "Geany", nothing wrong with the Geany program, however it was not in the Dapper repository by default, so I went over to the Geany download page and was recommended to add a Dapper repository for it, great I thought! So I added it...

[http://geany.uvena.de/Download/Releases](http://geany.uvena.de/Download/Releases) (This site has the info on it, which repository I added)

I downloaded the Geany program and it's perfect for what I need, however... ever since I added that repository and did a "sudo apt-get upgrade", it downloaded all this other cutting edge stuff from that repository, that I did not even ask to update, such as a later version of the Mono framework and a later version of XChat just to name a few.

I did not think much of it at the time, even though I never asked for these updates, I expected later versions to be a bonus anyway. However, coming to try out Banshee now, the program crashes upon first launch, and I... think... it could be because my Mono framework was upgraded to a cutting edge version from that same repository I got Geany. When I run Banshee from the command line, I get the error I have pasted at the end of this message.

Now my question is, if I remove this repository where I got Geany from (and remove Geany too if I have to), is there any way to tell the package manager to downgrade any packages such as Mono framework, to the correct versions that are in the standard Ubuntu repositories?

```

Stacktrace:

in Banshee.BansheeEntry:DetectInstanceAndDbus () <0xffffffff>
in Banshee.BansheeEntry:DetectInstanceAndDbus () <0x12>
in Banshee.BansheeEntry:Startup (string[]) <0x4fd>
in Banshee.BansheeEntry:Main (string[]) <0xa>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0x64fc3f>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7dc443f]
        /usr/lib/libmono.so.0 [0xb7d8603e]
        [0xffffe440]
        /usr/lib/libmono.so.0(mono_compile_create_var+0xae) [0xb7d82338]
        /usr/lib/libmono.so.0(mini_method_compile+0xfe8) [0xb7da2094]
        /usr/lib/libmono.so.0 [0xb7da304d]
        /usr/lib/libmono.so.0(mono_compile_method+0x24) [0xb7e06225]
        /usr/lib/libmono.so.0(mono_magic_trampoline+0x1f) [0xb7ddab1f]
        [0xb7a11032]
        [0xb7753f86]
        [0xb775389b]
        [0xb7753823]
        /usr/lib/libmono.so.0 [0xb7da3438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e05eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0x67) [0xb7e08a88]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7e0bbf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7db5b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7db654f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7b40ea2]
        banshee [0x8048459]
Aborted

```

---

### Post by Robvdl on 2006-08-03
Found the info myself, it may not be because of what I thought. It looks like it is a quite common problem with mono, and it needs to be compiled on my machine.

[http://www.ubuntuforums.org/archive/index.php/t-186028.html](http://www.ubuntuforums.org/archive/index.php/t-186028.html)
[http://ubuntuforums.org/showthread.php?t=167749](http://ubuntuforums.org/showthread.php?t=167749)
[http://ubuntuforums.org/showthread.php?t=137621&highlight=killed+mono](http://ubuntuforums.org/showthread.php?t=137621&highlight=killed+mono)

Well, can only give it a shot, rebuilding mono...

---

### Post by Robvdl on 2006-08-03
Edit:

I compiled mono from source, latest ver, 1.1.16.1 and installed it, I can confirm it is using this version, because it shows the version when I type:

mono --version

However, mono applications still crash. Some others have suggested re-installing libc6 libglib2.0-0 and libmono, I had already done this and it didn't work, mono still crashes. Maybe it's because I am running a 686-smp kernel , who knows, but I give up - back to rhythmbox, it's pretty good anyway. I will have to wait 'till mono becomes more stable, maybe by the time Ubuntu 6.10 comes out it may be resolved.

---

