---
title: "Firefox not starting"
date: 2008-12-21
forum: General Help
---

### Post by dummyhead3 on 2008-12-21
When I try to start firefox, ubuntu trys to load it for a few seconds, then aborts.
I tried atrting it from command line, it says that it is a Segmentation Error vbut does not echo any other details. I tried installing Epiphany browser, it worked a few times but then  stopped working as well.
Please help!

---

### Post by chrisamiller on 2008-12-21
90% of the time, this is a problem caused by an extension.  Try starting it in safe mode:

> firefox -safe-mode

If that works, close it and try it again normally.  Be sure to create a new session, rather than trying to restore your old one.  

If either of these fails, try creating a new profile:

> firefox -P

If the new profile works, you can transfer your bookmarks, history, etc over and then install addons one at a time until you figure out which one is causing th problem.

---

### Post by Hyper Tails on 2008-12-21
I have the same issue to
when I was on my laptop it did the same thing

---

### Post by dummyhead3 on 2008-12-22
I'm afraid it is not en extension that is causing the error. I tried running firefox in safe mode, tried running firefox -P and also tried renaming the ~/.mozilla directory to backaup-mozilla. It doesn't work... It didn't create a new mozilla folder when I ran firefox. It must be something else. It is not the GUI if it is possible, because I installed Xfce and it still doesn't work.
Thanks!

---

### Post by dummyhead3 on 2008-12-22
If this can help, i performed strace firefox, these are the last few lines that I got:
```

open("/usr/share/pixmaps/default/cursors/bottom_right_corner", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/X11R6/lib/X11/icons/default/cursors/bottom_right_corner", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/egor/.icons/DMZ-White/cursors/bottom_right_corner", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/egor/.icons/DMZ-White/index.theme", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/icons/DMZ-White/cursors/bottom_right_corner", O_RDONLY) = 38
fstat(38, {st_mode=S_IFREG|0644, st_size=15776, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe677b2b000
read(38, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0"..., 4096) = 4096
lseek(38, 0, SEEK_SET)                  = 0
read(38, "Xcur\20\0\0\0\0\0\1\0\3\0\0\0\2\0\375\377\30\0\0\0004\0"..., 4096) = 4096
close(38)                               = 0
munmap(0x7fe677b2b000, 4096)            = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=35, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 9, 0) = 1
read(18, "\372", 1)                     = 1
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3477, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3477, ...}) = 0
futex(0x203789c, 0x85 /* FUTEX_??? */, 1) = 1
futex(0x203789c, 0x85 /* FUTEX_??? */, 1) = 1
write(19, "\372", 1)                    = 1
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3477, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3477, ...}) = 0
brk(0x3449000)                          = 0x3449000
futex(0x203789c, 0x85 /* FUTEX_??? */, 1) = 1
futex(0x203789c, 0x85 /* FUTEX_??? */, 1) = 1
brk(0x346b000)                          = 0x346b000
select(4, [3], [3], NULL, NULL)         = 2 (in [3], out [3])
read(3, "\34\356\235\4\355\0\0\5\n\1\0\0\275\227e\0\0\0\0\0\0\0"..., 4096) = 96
writev(3, [{"<\2\2\0n\1\0\5\232\4\5\0o\1\0\5m\1\0\5P\1\0\0\0\0\0\000"..., 3348}, {"H\2\6\1}\1\0\5~\1\0\5\20\0\20\0\0\0\0\0\0\30\1\0\312\\"..., 1048}], 2) = 4396
stat("/usr/lib/xulrunner-1.9.0.5/components/txmgr.xpt", {st_mode=S_IFREG|0644, st_size=1318, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.5/components/txmgr.xpt", O_RDONLY) = 38
read(38, "XPCOM\nTypeLib\r\n\32\1\2\0\5\0\0\5&\0\0\0\"\0\0\0\351"..., 1318) = 1318
close(38)                               = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/egor/.mozilla/firefox/fppug3v3.default/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(9581, 9581, SIGSEGV)             = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 9581 detached

```

---

### Post by Trochaic on 2008-12-23
I am having the same problem.

In particular, here's the end of my strace:

```
stat64("/usr/lib/xulrunner-1.9.0.5/components/xpconnect.xpt", {st_mode=S_IFREG|0644, st_size=7745, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.5/components/xpconnect.xpt", O_RDONLY|O_LARGEFILE) = 16
read(16, "XPCOM\nTypeLib\r\n\32\1\2\0,\0\0\36A\0\0\0\"\0\0\4\361"..., 7745) = 7745
close(16)                               = 0
stat64("/usr/lib/xulrunner-1.9.0.5/components/xpcom_io.xpt", {st_mode=S_IFREG|0644, st_size=7420, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.5/components/xpcom_io.xpt", O_RDONLY|O_LARGEFILE) = 16
read(16, "XPCOM\nTypeLib\r\n\32\1\2\0*\0\0\34\374\0\0\0\"\0\0\4\271"..., 7420) = 7420
close(16)                               = 0
stat64("/usr/lib/xulrunner-1.9.0.5/components/dom_xul.xpt", {st_mode=S_IFREG|0644, st_size=7408, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.5/components/dom_xul.xpt", O_RDONLY|O_LARGEFILE) = 16
read(16, "XPCOM\nTypeLib\r\n\32\1\2\0&\0\0\34\360\0\0\0\"\0\0\4I"..., 7408) = 7408
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/jgk/.mozilla/firefox/a3v6ivjo.Jeremy/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(18025, 18025, SIGSEGV)           = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 18025 detached
```

---

### Post by Trochaic on 2008-12-23
I shoudl add that I have tried this with moving my ~/.mozilla directory to a new name and starting over; segfaulting still happens.  Also with -safe-mode, also with -ProfileManager .

The issue seems to emerge (per the strace) in some part of the xulrunner loading.

---

### Post by dummyhead3 on 2008-12-23
I think you're right, I tried reinstalling xulrunner, but that just messed things way more. I had got this bug: [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/276431](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/276431). Unfortunatley, the workaround didn't work... I then tried to reinstall firefox again and it didn't work because xulrunner was't configured. I'm stuck with Opera for now....:(:(

---

### Post by dummyhead3 on 2008-12-24
rebump

---

### Post by dummyhead3 on 2008-12-26
... anyone?

---

### Post by dummyhead3 on 2008-12-28
I was trying to debug using apport (wich didn't work).
Now the error has changed and says 
```
Segmentation fault (core dumped)
```
instead of just Segmentation fault.
The strace firefox is now the following (Last few lines)
```
WRITE, 4, 0x38000) = 0x7f255cfca000
mmap(0x7f255cfcd000, 7520, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f255cfcd000
close(4)                                = 0
mprotect(0x7f255cfca000, 4096, PROT_READ) = 0
mprotect(0x7f255d1d2000, 4096, PROT_READ) = 0
mprotect(0x7f255d3d6000, 4096, PROT_READ) = 0
mprotect(0x7f255d681000, 8192, PROT_READ) = 0
munmap(0x7f255e7ae000, 90426)           = 0
open("/usr/lib/xulrunner-1.9.0.5/libxul.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\246B\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=18206112, ...}) = 0
mmap(NULL, 20386368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f255ba20000
mprotect(0x7f255c9cf000, 2097152, PROT_NONE) = 0
mmap(0x7f255cbcf000, 1761280, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xfaf000) = 0x7f255cbcf000
mmap(0x7f255cd7d000, 82496, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f255cd7d000
close(4)                                = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 11695 detached

```
Hope this helps. Also, I tried reinstalling firefox, and now that xulrunner-1.9 remains unconfigured, so do all the firefox files that depend upoun it (firefox, ubufox, xulrunner-gnome-support-1.9, firefox-3.0, etc...)

This is what Synaptic gives me every time I try to install anything:
```

E: xulrunner-1.9: subprocess post-installation script returned error exit status 127
E: yelp: dependency problems - leaving unconfigured
E: gnome-user-guide: dependency problems - leaving unconfigured
E: ubuntu-docs: dependency problems - leaving unconfigured
E: firefox-3.0: dependency problems - leaving unconfigured
E: firefox-3.0-branding: dependency problems - leaving unconfigured
E: firefox: dependency problems - leaving unconfigured
E: xulrunner-1.9-gnome-support: dependency problems - leaving unconfigured
E: firefox-3.0-gnome-support: dependency problems - leaving unconfigured
E: firefox-gnome-support: dependency problems - leaving unconfigured
E: ubufox: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured


```

---

### Post by Trochaic on 2008-12-28
Two full reboots later and this problem has vanished. I no longer have segfaults with starting Firefox.

---

### Post by dummyhead3 on 2008-12-28
Two consecutive reboots? As in reboot, log in, reboot, log in?

---

### Post by Trochaic on 2008-12-28
> **dummyhead3 said:**
> Two consecutive reboots? As in reboot, log in, reboot, log in?
No, my reboots were not consecutive -- I did plenty of other things between reboots -- but that seems like the most salient thing that has changed in the mean time, and I thought it only fair to mention that this problem went away for me, so other sufferers (you!) would know that it may not be as widespread as it seemed.

---

### Post by dummyhead3 on 2008-12-28
Humm, it still persists for me even after several reboots... any help would be very appreciated.

---

### Post by dummyhead3 on 2008-12-30
I'm guessing the first thing I need to tackle is xulrunner, is there any way to make xulrunner work???

---

### Post by madmaxnj on 2008-12-31
Agghhh!!  I'm having the same problem.  Here is my post on a thread I started (that nobody replied to)
xulrunner 1.9 - Bus error, exit status 135, now no Firefox 

--------------------------------------------------------------------------------

Well it was telling met that there were a bunch of updates that I needed so I clicked to install them all. Something failed during the installation of the updates. It flagged and crash error, but I didn't write down what it was. After that I rebooted and Firefox wouldn't launch. It would start to, I would see it start on the status bar, but then would just go away. I went into Synaptic Package Manager and tried to reload Firefox. Here i get an error:
E: xulrunner-1.9:subprocess post-installation script returned error
exit status 135
E:firefox-3.0:dependency problems - leaving unconfigured (and a bunch more of these 'leaving unconfigured messages).

Digging into the detailed printout it starts to go south with:
Setting up xulrunner-1.9 (1.9.0.5+nobinonly-0ubuntu0.8.10.1)...
bus error
dpkg: error processing xulrunner-1.9 (--configure):
subprocess post-installation script returned exit status 135


So I tried to reload xulrunner and get the same thing.

I've gone through this now in a couple of different orders include deletes and new installs to no avail.

Any ideas? Can I go back a version on xulrunner and Firefox somehow? I don't see older versions in the Synaptic Package Manager.

Help? I configured this box to be a web surfer and now I can't surf the web. Thanks!

---

### Post by dummyhead3 on 2009-01-01
I think we should file a bug report, but when I try to reprouduce the xulrunner installation error, by using APT, it displays this message concerning apport: 
No apport report written because the error message indicates its a followup error from a previous failure.

---

### Post by dummyhead3 on 2009-01-05
bbbbbbbbbbbbbbbuuuuuuuuuuuuummmmmmmmmmmmmmmmmppppppppppppppp
[COLOR="Red"]XULRUNNER IS THE CURRENT PROBLEM!![/COLOR]

---

### Post by madmaxnj on 2009-01-06
dummyhead,
Do you get the bus error 135 when you click on details when xulrunner fails to install?

---

### Post by madmaxnj on 2009-01-07
I completely uninstalled xulrunner 1.9 and ff3 and related components a few days ago.  Tonight I first install xulrunner 1.9, and it went successfully.  I rebooted and then installed ff3 and then rebooted again and now ff3 is working okay.

---

### Post by dummyhead3 on 2009-01-10
No I don't think so.. in my case it says this:
E: xulrunner-1.9: subprocess post-installation script returned error exit status 127

---

### Post by SunnyRabbiera on 2009-01-15
Now I have this issue...
Come on people are there answers????

---

### Post by SunnyRabbiera on 2009-01-15
keeping this on the front page, as I think its critical!!!!!

---

### Post by dummyhead3 on 2009-01-15
me too

---

### Post by hs4e on 2009-01-31
Hey guys, just created an account here on ubuntuforums.org in order to post a reply here :D
I had the same problem last night, with Firefox not starting because of some xulrunner problem, so I did what some of you also did, reinstall xulrunner (just everything I've found in synaptic under "xulrunner"), and it works now. So I really suggest you try the same. Hope this helps :D

---

### Post by dummyhead3 on 2009-01-31
Reinstalling XULRunner doesn't work as I previously mentioned.

---

