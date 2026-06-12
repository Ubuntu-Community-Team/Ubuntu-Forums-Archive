---
title: "Kwin crashes after upgrading to KDE 3.5.4"
date: 2006-08-08
forum: Desktop Environments
---

### Post by heikki on 2006-08-08
After I upgraded my KDE from 3.5.3 to 3.5.4 from Kubuntu's reporsities, kwin started to crash. Usually, after a few (2 to 10) hours after starting up the kde kwin crashes and I get that KDE's dialog which tells me that kwin has reseived the SEGFAULT (11) signal and I can see debug information (which isn't useful, because I havn't debug-build). It seems that crashes arn't up to what I do (it has crashed when I have took a screenshot with ksnapshot and when I have read a pdf-file in Konqueror).

Do you have had similar problem? Have you got a solution for it? Or is there any way to start kwin from tty (I think it may be possible with some line like DISPLAY="foo" kwin, but I don't know how).

I have the following lines in my /etc/apt/sources.list
```

deb http://kubuntu.org/packages/kde-354 dapper main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.4/kubuntu dapper main

```

And there is nothing to be upgraded after apt-get update && apt-get dist-upgrade.

Some other specs...
Kernel 2.6.15-26-386
Ubuntu 6.06 and kubuntu-desktop-package
Nvidia GeForce FX 5700 and nvidia's binary driver from reporsities

If somebody think that debug information might be helpfull I can post it when kwin crashes next time.

---

### Post by apakatt on 2006-08-20
I have got the same problem. Just noticed.
Maybe its better to stick to the Ubuntu-mirrors with the older packages? Is there any way to down-grade or do we have to wait for a better release from Kde / Kubuntu?

---

### Post by kuja on 2006-08-20
Strange, KDE 3.5.4 hasn't given me even the slightest bit of trouble.

If you think it'd be useful to downgrade to KDE 3.5.3... I forget, but see if this works.

First, change the line in your /etc/apt/sources.list file to have [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) instead of kde-354 or kde-latest
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

That might force the downgrade, though, to be honest, I forget if it will or not.

---

### Post by apakatt on 2006-08-21
Ok, i'll check it out.
Here is some info if it will help in any way.
```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[Thread debugging using libthread_db enabled]
[New Thread -1232652608 (LWP 5454)]
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
[KCrash handler]
#6  0xb66febdf in KWinInternal::Client::screen ()
   from /usr/lib/libkdeinit_kwin.so
#7  0xb6739dce in KWinInternal::Workspace::activateNextClient ()
   from /usr/lib/libkdeinit_kwin.so
#8  0xb67480be in KWinInternal::Workspace::workspaceEvent ()
   from /usr/lib/libkdeinit_kwin.so
#9  0xb6748114 in KWinInternal::Application::x11EventFilter ()
   from /usr/lib/libkdeinit_kwin.so
#10 0xb7129457 in qt_set_x11_event_filter () from /usr/lib/libqt-mt.so.3
#11 0xb713674c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#12 0xb71504db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#13 0xb71c4947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#14 0xb71c486a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#15 0xb71aa965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#16 0xb6749a63 in kdemain () from /usr/lib/libkdeinit_kwin.so
#17 0xb7f1f4f0 in kdeinitmain () from /usr/lib/kde3/kwin.so
#18 0x0804e173 in ?? ()
#19 0x00000003 in ?? ()
#20 0x08143ca0 in ?? ()
#21 0x00000001 in ?? ()
#22 0x00000000 in ?? ()

```

---

### Post by kuja on 2006-08-21
I'm no expert, but I do believe for that backtrace to be more useful you need the appropriate -dbg package installed to get the full thing.(ie, no lines saying "no debugging symbols found") I think it's kdebase-dbg in the case of kwin. Try installing the dbg package and filing a bug report at kdebugs.org or launchpad.net.

---

