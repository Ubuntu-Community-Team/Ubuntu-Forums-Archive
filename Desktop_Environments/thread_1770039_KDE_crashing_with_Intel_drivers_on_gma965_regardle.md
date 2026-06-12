---
title: "KDE crashing with Intel drivers on gma965 regardless if desktop effects are on or not"
date: 2011-05-28
forum: Desktop Environments
---

### Post by Topazkitty on 2011-05-28
Hi, I have been looking for a solution to this bug for a while and I just can't seem to find one. So if anyone can help me I'd really appreciate it.

First i have previously used 10.10 and none of these problems occurred.

My problem is that when I play games like Extreme tux racer and switch resolutions the xorg server will lockup and require a hard reboot and the game will crash.

Second if I run the computer for a while sometimes my Xorg will just black out but you can still here whatever sound I have at the background at the time.

The xserver can be rather unpredictable. I'd really like to find a solution because otherwise 11.04 is fine.

Thanks Topazkitty

---

### Post by Topazkitty on 2011-05-28
lspci | grep VGA


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

Complete lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Zorael on 2011-05-30
This sounds like a proper GPU hang, though I'm far from knowledgeable in that area. Have a look at the [current Intel video driver bugs over on Launchpad](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel) and see if any seem to match what you're experiencing.

You'll probably need more information to properly diagnose this though, such as the **dmesg** output when the screen has frozen. The easiest way of collecting that is to install [**openssh-server**](apt://openssh-server) on your machine, and then connecting to it with another computer (using [**openssh-client**](apt://openssh-client)) when the CPU has hanged. Then piping dmesg output to a text file and see what error messages it contains. Potentially attaching it to an existing or new bug report.

```
$ **ssh 10.0.0.22**
zorael@10.0.0.22's password:
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic i686)

 * Documentation:  https://help.ubuntu.com/

No mail.
Last login: Mon May 30 14:42:13 2011 from 10.0.0.3
zorael@lethe:~$ **[COLOR="Green"]dmesg > ~/dmesg.log[/COLOR]**
zorael@lethe:~$ exit
```

After rebooting your main machine ([Alt+SysRq REISUB](http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html)), you should now have that **dmesg.log** file sitting in your home directory for your perusal. The log is in chronological descending order so your error message should be at or near the end.

You need another computer for this, obviously. You *can* do it by cooking up a quick script if you don't have another available, so if you don't all is not lost.

---

### Post by Topazkitty on 2011-05-30
Thanks for trying to help me but I only have one computer with linux and I don't know that much about linux yet so any steps to help me get the dmesg information would be useful 

Thanks Topazkitty

---

### Post by Topazkitty on 2011-05-30
I also looked on the bug reports and nothing matched the symptoms my laptop is experiencing however, Kwin crashes sometimes before the resolution lockup and I wondered if this would help at all. Its a kwin segfault 11

p, li { white-space: pre-wrap; }  Application: KWin (kwin), signal: Segmentation fault
 [Current thread is 1 (Thread 0x7f68fc00d7a0 (LWP 3112))]
 
 Thread 3 (Thread 0x7f68e09c3700 (LWP 3119)):
 #0  0x00007f68fb855143 in select () from /lib/x86_64-linux-gnu/libc.so.6
 #1  0x00007f68f7c3332c in qt_safe_select(int, fd_set*, fd_set*, fd_set*, timeval const*) () from /usr/lib/libQtCore.so.4
 #2  0x00007f68f7c383d0 in  QEventDispatcherUNIXPrivate::doSelect(QFlags<QEven   tLoop::ProcessEventsFlag>, timeval*) () from /usr/lib/libQtCore.so.4
 #3  0x00007f68f7c3904a in  QEventDispatcherUNIX::processEvents(QFlags<QEventL   oop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #4  0x00007f68f7c0a882 in  QEventLoop::processEvents(QFlags<QEventLoop::Proce  ssEventsFlag>)  () from /usr/lib/libQtCore.so.4
 #5  0x00007f68f7c0aabc in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsF  lag>) () from /usr/lib/libQtCore.so.4
 #6  0x00007f68f7b21924 in QThread::exec() () from /usr/lib/libQtCore.so.4
 #7  0x00007f68f7becc2f in ?? () from /usr/lib/libQtCore.so.4
 #8  0x00007f68f7b24175 in ?? () from /usr/lib/libQtCore.so.4
 #9  0x00007f68f2217d8c in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #10 0x00007f68fb85d04d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #11 0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f68e01c2700 (LWP 3120)):
 #0  0x00007f68f221cbac in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/x86_64-linux-gnu/libpthread.so.0
 #1  0x00007f68fa6bc2a2 in ?? () from /usr/lib/libQtScript.so.4
 #2  0x00007f68fa6bc2d9 in ?? () from /usr/lib/libQtScript.so.4
 #3  0x00007f68f2217d8c in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #4  0x00007f68fb85d04d in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7f68fc00d7a0 (LWP 3112)):
 [KCrash Handler]
 #6  0x00007f68e370f0a0 in intel_region_buffer () from /usr/lib/dri/i965_dri.so
 #7  0x00007f68e37026c2 in intelClearWithBlit () from /usr/lib/dri/i965_dri.so
 #8  0x00007f68e3704d2a in ?? () from /usr/lib/dri/i965_dri.so
 #9  0x00007f68fbbd3ce7 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #10 0x00007f68fbbcb88f in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #11 0x00007f68fbbc8c7a in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #12 0x00007f68fbbe6f19 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #13 0x00007f68e28075a6 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #14 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #15 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #16 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #17 0x00007f68e27ae44d in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #18 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #19 0x00007f68e27c957b in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #20 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #21 0x00007f68e27dbe68 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #22 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #23 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #24 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #25 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #26 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #27 0x00007f68e27b2fbd in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #28 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #29 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #30 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #31 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #32 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #33 0x00007f68e279a365 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #34 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #35 0x00007f68e27ea256 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #36 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #37 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #38 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #39 0x00007f68e27cfb8f in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #40 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #41 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #42 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #43 0x00007f68e2793bad in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #44 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #45 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #46 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #47 0x00007f68e27e2d86 in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #48 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #49 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #50 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #51 0x00007f68f9ca6a18 in KWin::Effect::paintScreen(int, QRegion,  KWin::ScreenPaintData&) () from /usr/lib/libkwineffects.so.1
 #52 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #53 0x00007f68e27d939b in ?? () from /usr/lib/kde4/kwin4_effect_builtins.so
 #54 0x00007f68fbbe6fa3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #55 0x00007f68fbbcb0af in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #56 0x00007f68fbbdeef3 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #57 0x00007f68fbbc6396 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #58 0x00007f68f7c1f1c9 in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
 #59 0x00007f68f6fcc9e4 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
 #60 0x00007f68f6fd13aa in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
 #61 0x00007f68fb358866 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
 #62 0x00007f68f7c0b49c in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
 #63 0x00007f68f7c38f12 in ?? () from /usr/lib/libQtCore.so.4
 #64 0x00007f68f7c3905b in  QEventDispatcherUNIX::processEvents(QFlags<QEventL   oop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #65 0x00007f68f7074c0c in ?? () from /usr/lib/libQtGui.so.4
 #66 0x00007f68f7c0a882 in  QEventLoop::processEvents(QFlags<QEventLoop::Proce  ssEventsFlag>)  () from /usr/lib/libQtCore.so.4
 #67 0x00007f68f7c0aabc in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsF  lag>) () from /usr/lib/libQtCore.so.4
 #68 0x00007f68f7c0eecb in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
 #69 0x00007f68fbb641ec in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_kwin.so
 #70 0x00007f68fb795eff in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
 #71 0x0000000000400669 in _start ()

---

### Post by Zorael on 2011-05-31
That backtrace is not useful as you don't seem to have the needed debugging symbols installed. Doesn't it offer to install them for you?

Anyway, to get a dmesg dump without another computer available, open up a terminal and run the following command.
```
while true; do dmesg > ~/dmesg.log; cp /var/log/Xorg.0.log ~/Xorg.0.log; cp /var/log/kdm.log ~/kdm.log; sync; sleep 10; done
```
Afterwards just leave that terminal alone. It will dump various logs to your home directory once every 10 seconds. Now just wait for a GPU hang so it can gather the information.

Make sure to wait 10 seconds before you reboot so you don't catch it inbetween dumps.

---

### Post by Topazkitty on 2011-05-31
I have tried to command you have told to use and then I ran extreme tux racer and it started flickering I exited the game and kwin crashed. I tried install debugging symbols this time but it said that none were available. Then the gui hung. I have attached the logs as a zip from dmesg and application in the bug report was /usr/lib/kdeui.so5 I think because it wouldn't let me copy the text because of GPU hang. Also before the GPU hang kwin was really slow and the windows could barely move.

 

 Thanks for trying to help me this problem.

---

### Post by Zorael on 2011-05-31
Those logs don't seem to contain anything of interest, sadly.

Could this be hardware failure? For your next step I'd suggest you try running memtest off a live CD, and perhaps install Prime95 and run it via Wine to stress test your CPU too.

See [this wiki entry](https://wiki.archlinux.org/index.php/Stress_Test) for more information.

---

### Post by Topazkitty on 2011-05-31
I just finished the test of Memtest86 and no errors came up. I don't think my CPU is the problem because this kind of problem never happened in my previous windows 7 install. Any other ideas because I really like Linux and KDE? Do you think this is a Kwin or Xorg bug?

Edit: I have an intel core 2 duo mobile processor

---

### Post by Zorael on 2011-05-31
I would guess it's either a bug in the Intel X driver, or in the Mesa libraries. It could be something that KWin exposes without being KWin's fault per se.

At this point try adding the **xorg-edgers** ppa and update to the drivers there. They're not part of natty and are sort of bleeding edge.
```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```
Then reboot.

If this doesn't work, the next step is to manually install the debugging symbols so you get a useful backtrace when KWin crashes.

I got something similar to this on my laptop, and it disappeared with updated drivers. It also became a bit more stable if I disabled "Suspend desktop effects for fullscreen windows" in System Settings -> Desktop Effects -> Advanced tab.

---

### Post by Topazkitty on 2011-05-31
Thanks for the suggestion but I had tried Xorg Edgers before but I ppa-purged it because it made the crashes even more frequent. Now I have reinstalled ubuntu 11.04 with unity to use a different window manager as a test. I really appreciate your help though for trying to help me solve this problem.

Thanks Topazkitty

---

### Post by Topazkitty on 2011-05-31
I just tried the same steps with Unity and it still crashed and I now believe it is an Xorg bug with the intel driver where would I file a bug at?

---

### Post by Topazkitty on 2011-05-31
Hi, I have made the system hang again expect under unity and had it make more logs if that is helpful at all. Also disabling desktop effects had made the system more stable but had not gotten rid of problem completely.

Thanks for all your help.

---

### Post by Zorael on 2011-06-01
```
[...]
[   272.570] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.578] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.585] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.592] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.598] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.605] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.611] (WW) intel(0): first get vblank counter failed: Invalid argument
[   272.618] (WW) intel(0): first get vblank counter failed: Invalid argument
[...]
```

Could it be [this bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/757221)?

[quote=bug description]Howto reproduce:

1) lock the screen using ctrl+alt+L
2) press a button

expected behaviour:
3) screen unlock widget rendered
4) type in password, resume session

actual behaviour:
3) screen unlock widget is _not_ drawn
4) blind typing password and pressing enter I *think* unlocks screen, but still **no updates to the screen are rendered. I only see the old screen content** (screen saver images), mouse cursor however changes it's icon as I move it around the screen.[/quote]

If you were to report a new bug, I think you should target it toward the **xserver-xorg-video-intel** package. That's the Xorg Intel driver. But if you're running Ubuntu (and not Kubuntu or other flavors), use the **ubuntu-bug** tool to make it automatically gather information about your computer and help you file the bug.

---

### Post by Topazkitty on 2011-06-01
I tried reproducing the bug that you mentioned. However, the bug did not occur so I am going to try to fill out a bug report to xserver-xorg-video-intel

Edit: I just reported the bug if you want to see it is here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/791479:](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/791479:)

Thanks for helping me with this problem

---

