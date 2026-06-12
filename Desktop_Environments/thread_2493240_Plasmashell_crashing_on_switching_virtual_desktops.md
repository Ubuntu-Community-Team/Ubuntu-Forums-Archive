---
title: "Plasmashell crashing on switching virtual desktops (and other window actions)"
date: 2023-12-07
forum: Desktop Environments
---

### Post by pgratz on 2023-12-07
Hi all,
So I purchased a shiny new 2023 Razer Blade 16, this has nVidia 4090 mobile GPU with Optimus switching between that and the integrated GPU on the intel processor.  I installed Kubuntu 23.10 on this and everything but the speakers seems to work so far.   That said I'm having one problem that keeps popping up.  I  like to use multiple virtual desktops in KDE plasma but it seems that about 50% of the time when switching from one desktop to another the plasma shell will crash and restart.  Sometimes it also crashes on window closing and other window actions like closing a window and things like that.  It seems to persist regardless of Wayland or X11, also in both full integrated GPU as well as discrete.

Can anyone give me some pointers on debugging the issue?
Thanks!
Paul

---

### Post by #&amp;thj^% on 2023-12-07
Lacking Info here, could you run the system-info script found in my signature, it might shed some light to help you.
Please run it with the "--details" flag added, and post the link it gives you when done here in your thread.

---

### Post by pgratz on 2023-12-07
Thanks for the quick reply.  Nice script.  Here is the output:
[FONT=monospace][COLOR=#000000]https://paste.ubuntu.com/p/56rZfwgNgd/[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]
Thanks!
[/COLOR]
Edit:reran with --details.[/FONT]

---

### Post by #&amp;thj^% on 2023-12-07
One possible here is this, "SecureBoot enabled"
This is new to me on your CPU "Upgrade: <OUT OF SPEC>"
And another possible, I'm not sure if you really need "vt.handoff=7" but maybe you do, what happens without it on "/etc/default/grub"?

And I see no nVidia Driver installed.....have you an option in your Bios for switchable graphics?

I'm still reading it though.

---

### Post by pgratz on 2023-12-07
> **1fallen said:**
> One possible here is this, "SecureBoot enabled"


I can disable this, I didn't think it mattered much so I left it on.  TBH, if I have to blow away windows to make this work in Linux I can do that too (but I think I can disable SecureBoot and still have windows work).

> 
This is new to me on your CPU "Upgrade: <OUT OF SPEC>"

Got me on that one.  Googling a bit and it seems like this isn't a showstopper in other systems .
> 
And another possible, I'm not sure if you really need "vt.handoff=7" but maybe you do, what happens without it on "/etc/default/grub"?

Will remove and try it.
> 
 And I see no nVidia Driver installed.....have you an option in your Bios for switchable graphics?

Yeah, at the moment I have prime_select set to intel but it doesn't seem to matter, both intel and nvidia have the same behavior.
> 
 I'm still reading it though.

I'll try the above when I get to work tomorrow morning (I don't have the laptop at home at the moment).
Thanks!

---

### Post by #&amp;thj^% on 2023-12-08
Windows should boot Ok with secure boot disabled.
let us know how things are coming along with those changes.
In you report I never seen where nVidia was installed?
```
nvidia-smi
Fri Dec  8 15:33:40 2023       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.113.01             Driver Version: 535.113.01   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off | 00000000:01:00.0  On |                  N/A |
| N/A   29C    P8               3W /  60W |    367MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      2067      G   /usr/lib/xorg/Xorg                          215MiB |
|    0   N/A  N/A      2988      G   xfwm4                                         2MiB |
|    0   N/A  N/A    181293      G   /usr/lib/firefox/firefox                    141MiB |
+---------------------------------------------------------------------------------------+

```

---

### Post by pgratz on 2023-12-09
Sorry, I was out of the office yesterday so I dropped by to grab the laptop and work on it this weekend.

Anyways, I've now disabled secure boot.  I don't see "vt.handoff=7" in /etc/default/grub, so I uncommented "GRUB_TERMINAL=console".

I ran prime_select nvidia so that I could run nvidia-smi.  Here is that output:
```
[FONT=courier new]pgratz@pgratz-Blade-16:~$ nvidia-smi[/FONT]
[FONT=courier new]Sat Dec  9 11:38:25 2023       [/FONT]
[FONT=courier new]+---------------------------------------------------------------------------------------+[/FONT]
[FONT=courier new]| NVIDIA-SMI 535.129.03             Driver Version: 535.129.03   CUDA Version: 12.2     |[/FONT]
[FONT=courier new]|-----------------------------------------+----------------------+----------------------+[/FONT]
[FONT=courier new]| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |[/FONT]
[FONT=courier new]| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |[/FONT]
[FONT=courier new]|                                         |                      |               MIG M. |[/FONT]
[FONT=courier new]|=========================================+======================+======================|[/FONT]
[FONT=courier new]|   0  NVIDIA GeForce RTX 4090 ...    Off | 00000000:01:00.0 Off |                  N/A |[/FONT]
[FONT=courier new]| N/A   43C    P4              28W /  50W |    535MiB / 16376MiB |     14%      Default |[/FONT]
[FONT=courier new]|                                         |                      |                  N/A |[/FONT]
[FONT=courier new]+-----------------------------------------+----------------------+----------------------+[/FONT]
[FONT=courier new]                                                                                         [/FONT]
[FONT=courier new]+---------------------------------------------------------------------------------------+[/FONT]
[FONT=courier new]| Processes:                                                                            |[/FONT]
[FONT=courier new]|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |[/FONT]
[FONT=courier new]|        ID   ID                                                             Usage      |[/FONT]
[FONT=courier new]|=======================================================================================|[/FONT]
[FONT=courier new]|    0   N/A  N/A     10394      G   /usr/lib/xorg/Xorg                          285MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10636      G   /usr/bin/kwalletd5                            4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10852      G   /usr/bin/ksmserver                            4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10854      G   /usr/bin/kded5                                4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10857      G   /usr/bin/kwin_x11                           104MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10883      G   /usr/bin/plasmashell                         63MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10898      G   ...c/polkit-kde-authentication-agent-1        4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     10900      G   ...-gnu/libexec/xdg-desktop-portal-kde        4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     11219      G   ...86_64-linux-gnu/libexec/kdeconnectd        4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     11244      G   /usr/bin/kaccess                              4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     11255      G   ...-linux-gnu/libexec/DiscoverNotifier        4MiB |[/FONT]
[FONT=courier new]|    0   N/A  N/A     11533      G   /usr/bin/konsole                              4MiB |[/FONT]
[FONT=courier new]+---------------------------------------------------------------------------------------+[/FONT]
[FONT=courier new]pgratz@pgratz-Blade-16:~$ [/FONT]
```


 I'm still getting the crashes from plasmashell.  One time it actually made a crash report.  Here is the output of that:

```
[FONT=monospace][COLOR=#54FF54]**pgratz@pgratz-Blade-16**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ cat plasmashell-20231209-114040.kcrash  [/COLOR]
Application: Plasma (plasmashell), signal: Segmentation fault

[KCrash Handler]
#4  0x00007f24096c62fd in ?? () from /lib/x86_64-linux-gnu/libtaskmanager.so.6
#5  0x00007f2410706312 in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007f2410663e42 in QAbstractItemModel::rowsAboutToBeRemoved(QModelIndex const&, int, int, QAbstractItemM
odel::QPrivateSignal) () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#7  0x00007f241066c679 in QAbstractItemModel::beginRemoveRows(QModelIndex const&, int, int) () from /lib/x86_64
-linux-gnu/libQt5Core.so.5
#8  0x00007f241069a9f8 in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#9  0x00007f241069f453 in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#10 0x00007f241069f88f in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#11 0x00007f24106a0a1e in QSortFilterProxyModel::invalidateFilter() () from /lib/x86_64-linux-gnu/libQt5Core.so
.5
#12 0x00007f24096c1888 in TaskManager::TaskFilterProxyModel::setVirtualDesktop(QVariant const&) () from /lib/x8
6_64-linux-gnu/libtaskmanager.so.6
#13 0x00007f2411e8ba32 in QQmlPropertyPrivate::write(QObject*, QQmlPropertyData const&, QVariant const&, QQmlCo
ntextData*, QFlags<QQmlPropertyData::WriteFlag>) () from /lib/x86_64-linux-gnu/libQt5Qml.so.5
#14 0x00007f2411ef307c in QQmlBinding::slowWrite(QQmlPropertyData const&, QQmlPropertyData const&, QV4::Value c
onst&, bool, QFlags<QQmlPropertyData::WriteFlag>) () from /lib/x86_64-linux-gnu/libQt5Qml.so.5
#15 0x00007f2411ef44c0 in ?? () from /lib/x86_64-linux-gnu/libQt5Qml.so.5
#16 0x00007f2411ef5dc6 in ?? () from /lib/x86_64-linux-gnu/libQt5Qml.so.5
#17 0x00007f2411ef3734 in QQmlBinding::update(QFlags<QQmlPropertyData::WriteFlag>) () from /lib/x86_64-linux-gn
u/libQt5Qml.so.5
#18 0x00007f2411ed059f in QQmlNotifier::emitNotify(QQmlNotifierEndpoint*, void**) () from /lib/x86_64-linux-gnu
/libQt5Qml.so.5
#19 0x00007f2410705a6c in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#20 0x00007f2410706312 in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#21 0x00007f2410706312 in ?? () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#22 0x00007f24127d2602 in KX11Extras::currentDesktopChanged(int) () from /lib/x86_64-linux-gnu/libKF5WindowSyst
em.so.5
#23 0x00007f24097bfe6c in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/kf5/kwindowsystem/KF5WindowSystemX11
Plugin.so
#24 0x00007f24106c9c8f in QAbstractEventDispatcher::filterNativeEvent(QByteArray const&, void*, long*) () from 
/lib/x86_64-linux-gnu/libQt5Core.so.5
#25 0x00007f240b6d1213 in QXcbConnection::handleXcbEvent(xcb_generic_event_t*) () from /lib/x86_64-linux-gnu/li
bQt5XcbQpa.so.5
#26 0x00007f240b6d28a6 in QXcbConnection::processXcbEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /lib/
x86_64-linux-gnu/libQt5XcbQpa.so.5
#27 0x00007f240b6f9f77 in ?? () from /lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
#28 0x00007f240f2efb2c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#29 0x00007f240f34b46f in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#30 0x00007f240f2edd20 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#31 0x00007f2410727daa in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /l
ib/x86_64-linux-gnu/libQt5Core.so.5
#32 0x00007f24106cb15b in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /lib/x86_64-linux-gnu
/libQt5Core.so.5
#33 0x00007f24106d3904 in QCoreApplication::exec() () from /lib/x86_64-linux-gnu/libQt5Core.so.5
#34 0x00005580542e2a34 in ?? ()
#35 0x00007f240fc280d0 in __libc_start_call_main (main=main@entry=0x5580542e1b50, argc=argc@entry=2, argv=argv@
entry=0x7ffe677603a8) at ../sysdeps/nptl/libc_start_call_main.h:58
#36 0x00007f240fc28189 in __libc_start_main_impl (main=0x5580542e1b50, argc=2, argv=0x7ffe677603a8, init=<optim
ized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7ffe67760398) at ../csu/libc-start.c:36
0
#37 0x00005580542e2b55 in ?? ()
[Inferior 1 (process 11900) detached]
```

Interestingly, I find that when I boot with nvidia enabled, the screen is pretty glitchy (hard to describe).

Thanks for the help!


[/FONT]

---

### Post by pgratz on 2023-12-09
Ah ha!  

So I ran plasmashell from the command line and this is what I got to STDOUT/STDERR:
[https://paste.ubuntu.com/p/crkTBNh8y6/](https://paste.ubuntu.com/p/crkTBNh8y6/)

Seeing all those BAT related errors in the logs I was wondering if maybe the plasma widget wattage monitor I installed in the panel might be the issue.  I removed that widget and so far no more plasmashell crashes.  I'll keep an eye on it but so far so good.

---

### Post by #&amp;thj^% on 2023-12-09
> **pgratz said:**
> Ah ha!  

So I ran plasmashell from the command line and this is what I got to STDOUT/STDERR:
[https://paste.ubuntu.com/p/crkTBNh8y6/](https://paste.ubuntu.com/p/crkTBNh8y6/)

Seeing all those BAT related errors in the logs I was wondering if maybe the plasma widget wattage monitor I installed in the panel might be the issue.  I removed that widget and so far no more plasmashell crashes.  I'll keep an eye on it but so far so good.

Nice detective work, I was going to ask you to file a bug against Plasma Shell, but you may have found the gremlin.
The VT-handoff is in 
```
cat /proc/cmdline
```
And I also noticed nVidia rendering in Mantic was glitchy coming out of suspend (An Ugly purplish tint covered the screen), I added The graphics PPA and that helped for me on LightDM XFCE4
Please keep us posted...:)

---

### Post by pgratz on 2023-12-09
Ooops accidental repost.

---

### Post by pgratz on 2023-12-09
> **1fallen said:**
> Nice detective work, I was going to ask you to file a bug against Plasma Shell, but you may have found the gremlin.
The VT-handoff is in 
```
cat /proc/cmdline
```


Ah, yeah I see that.  Must be coming in from somewhere else but I guess its fine.
> 

And I also noticed nVidia rendering in Mantic was glitchy coming out of suspend (An Ugly purplish tint covered the screen), I added The graphics PPA and that helped for me on LightDM XFCE4
Please keep us posted...:)

For me, it seems like the bottom half of the screen gets garbled every so often for a few milliseconds then its back to normal.  Kinda strange.  Interestingly as I type this I see it happening a couple times so maybe its something else.  Anyways, I'll try the PPA.

Thanks!

---

### Post by #&amp;thj^% on 2023-12-09
> **pgratz said:**
> Ah, yeah I see that.  Must be coming in from somewhere else but I guess its fine.
Thanks!
yep it's fine
```
cat /proc/cmdline
BOOT_IMAGE=/BOOT/ubuntu_1elkfk@/vmlinuz-6.5.0-9-generic root=ZFS=rpool/ROOT/ubuntu_1elkfk ro quiet splash vt.handoff=1

```
I'm just used to seeing 'vt.handoff=1'

---

