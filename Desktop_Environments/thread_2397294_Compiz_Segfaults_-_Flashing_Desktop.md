---
title: "Compiz Segfaults - Flashing Desktop"
date: 2018-07-27
forum: Desktop Environments
---

### Post by MaccyDG on 2018-07-27
Hello,

I'd be grateful for some help on this. Starting a couple of months ago, I began having issues in Firefox related to something called "r300_dri.so". I disabled Webgl on the "about:config" page in Firefox and that stopped the crashing. However, as of around 2 weeks ago, whenever I log in to Ubuntu, I now just see my desktop background, with flashing icons, Unity launcher and top bar. I can right-click to get to a terminal. I think Compiz is crashing (logs posted below). The Firefox issue and the desktop issue may be completely unrelated, but I have a hunch that there's a common cause.

**System**
Ubuntu 16.04 64-bit
AMD Turion 64
4 GB RAM
PATA IDE HDD
Graphics: VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200]

[B]Things I have Tried
[/B]
[LIST]
[*]Upgrading all packages to latest releases 
[*]The process described in "UPDATE APRIL" and "UPDATE March 2018" here: [https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults](https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults) 
[*]Reinstalling libglib2.0-0 
[/LIST]
None of the above solved the issue.

I have read lots of posts on the issue, but lots sound like they're different to what I'm experiencing. Nevertheless, apologies if I've missed an obvious avenue before seeking help here!

[B]Paste from /var/log/syslog (starting from first instance of the segfault):
[/B]```
Jul 27 18:30:19 HAPPY kernel: [  669.687946] compiz[2543]: segfault at 738 ip 00007f813c01c2c9 sp 00007fff02f61ea0 error 4
Jul 27 18:30:20 HAPPY gnome-session[2156]: (unity-fallback-mount-helper:2488): GLib-GIO-CRITICAL **: g_dbus_proxy_call_finish_internal: assertion 'G_IS_DBUS_PROXY (proxy)' failed
Jul 27 18:30:20 HAPPY gnome-session[2156]: (unity-fallback-mount-helper:2488): GLib-CRITICAL **: g_variant_get_va: assertion 'value != NULL' failed
Jul 27 18:30:20 HAPPY gnome-session[2156]: (unity-fallback-mount-helper:2488): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Jul 27 18:30:20 HAPPY gnome-session[2156]: ** (unity-fallback-mount-helper:2488): WARNING **: Can't call IsLocked() on the Unity.Session object: Cannot invoke method; proxy is for a well-known name without an owner and proxy was constructed with the G_DBUS_PROXY_FLAGS_DO_NOT_AUTO_START flag
Jul 27 18:30:21 HAPPY org.gnome.zeitgeist.Engine[2019]: ** (zeitgeist-datahub:2766): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Jul 27 18:30:23 HAPPY kernel: [  673.386286] compiz[2740]: segfault at 328 ip 00007fbb600272c9 sp 00007ffc75bf8da0 error 4
Jul 27 18:30:23 HAPPY gnome-session[2156]: ** (unity-fallback-mount-helper:2488): WARNING **: Can't call IsLocked() on the Unity.Session object: Cannot invoke method; proxy is for a well-known name without an owner and proxy was constructed with the G_DBUS_PROXY_FLAGS_DO_NOT_AUTO_START flag
```

[B]Paste from /var/crash/_usr_bin_compiz.1000.crash
[/B]```
ProblemType: Crash
Architecture: amd64
CrashCounter: 1
CurrentDesktop: Unity
Date: Thu Jul 26 22:13:47 2018
DistroRelease: Ubuntu 16.04
ExecutablePath: /usr/bin/compiz

<snip>

SegvAnalysis:
 Segfault happened at: 0x7f19500522c9:    movdqu (%r8,%rbx,1),%xmm9
 PC (0x7f19500522c9) ok
 source "(%r8,%rbx,1)" (0x00000320) not located in a known VMA region (needed readable region)!
 destination "%xmm9" ok
SegvReason: reading NULL VMA
SourcePackage: compiz
Stacktrace:
 #0  0x00007f19500522c9 in ?? ()
 No symbol table info available.
 #1  0x0000000000000000 in ?? ()
 No symbol table info available.
StacktraceTop:
 ?? ()
 ?? ()
Tags:  xenial xenial ubuntu compiz-0.9
ThreadStacktrace:
 .
 Thread 6 (Thread 0x7f19297bc700 (LWP 2252)):
 #0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
 No locals.
 #1  0x00007f1956c7dcfa in g_cond_wait_until () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007f1956c0d999 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007f1956c0dfbb in g_async_queue_timeout_pop () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x00007f1956c6060a in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007f1956c5fbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #6  0x00007f19565ca6ba in start_thread (arg=0x7f19297bc700) at pthread_create.c:333
         __res = <optimised out>
         pd = 0x7f19297bc700
         now = <optimised out>
         unwind_buf = {cancel_jmp_buf = {{jmp_buf = {139746046887680, 2698625152003350009, 0, 140732259479199, 139746046888384, 139746491836624, -2647795865437594119, -2647591021518381575}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
         not_first_call = <optimised out>
         pagesize_m1 = <optimised out>
         sp = <optimised out>
         freesize = <optimised out>
         __PRETTY_FUNCTION__ = "start_thread"
 #7  0x00007f195841641d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109
 No locals.
 .
 Thread 5 (Thread 0x7f1942859700 (LWP 2244)):
 #0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
 No locals.
 #1  0x00007f194343670b in ?? () from /usr/lib/x86_64-linux-gnu/dri/r300_dri.so
 No symbol table info available.
 #2  0x00007f1943436427 in ?? () from /usr/lib/x86_64-linux-gnu/dri/r300_dri.so
 No symbol table info available.
 #3  0x00007f19565ca6ba in start_thread (arg=0x7f1942859700) at pthread_create.c:333
         __res = <optimised out>
         pd = 0x7f1942859700
         now = <optimised out>
         unwind_buf = {cancel_jmp_buf = {{jmp_buf = {139746466961152, 2698625152003350009, 0, 140732259485039, 139746466961856, 0, -2647566498614731271, -2647591021518381575}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
         not_first_call = <optimised out>
         pagesize_m1 = <optimised out>
         sp = <optimised out>
         freesize = <optimised out>

```
The report carries on in a similar fashion: lots of the same errors.

I am currently booting off a live USB (Unetbootin) of 16.04 and it seems to be working absolutely fine. The Ubuntu .iso image was downloaded some months ago, though, before I had any of these problems.

Many thanks for any help you can give!

Liam

---

### Post by MaccyDG on 2018-12-29
Workaround solution outlined in bug report here: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1798868](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1798868)

---

