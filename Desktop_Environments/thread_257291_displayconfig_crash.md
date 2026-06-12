---
title: "displayconfig crash"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Revan on 2006-09-14
Hi guys,

it's been a while since I was able to run displayconfig and change the resolution of my screen :(

If I run the command from Konsole, this is the output:

```
gildenlow@guardian:~$ displayconfig
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
kdeui (KAboutDialog): setPixmap (iconName): guidance
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = displayconfig path = <unknown> pid = 11024

```

And this is the code generated with gdb:
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210124064 (LWP 11024)]
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
[KCrash handler]
#6  0xb6f96f83 in QWidget::paletteBackgroundColor ()
   from /usr/lib/libqt-mt.so.3
#7  0xb50e3fd3 in DominoStyle::polish ()
   from /usr/lib/kde3/plugins/styles/domino.so
#8  0xb6ef7754 in QApplication::polish () from /usr/lib/libqt-mt.so.3
#9  0xb685f6aa in sipKApplication::polish ()
   from /usr/lib/python2.4/site-packages/kdecore.so
#10 0xb6f981d5 in QWidget::polish () from /usr/lib/libqt-mt.so.3
#11 0xb76cb03c in sipQVButtonGroup::polish ()
   from /usr/lib/python2.4/site-packages/qt.so
#12 0xb6ef1474 in QLayout::totalMinimumSize () from /usr/lib/libqt-mt.so.3
#13 0xb6ef2726 in QLayout::activate () from /usr/lib/libqt-mt.so.3
#14 0xb6ef2ada in QLayout::eventFilter () from /usr/lib/libqt-mt.so.3
#15 0xb6f60002 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#16 0xb6f60080 in QObject::event () from /usr/lib/libqt-mt.so.3
#17 0xb6f9d5aa in QWidget::event () from /usr/lib/libqt-mt.so.3
#18 0xb702772e in QGroupBox::event () from /usr/lib/libqt-mt.so.3
#19 0xb6ffbfec in QButtonGroup::event () from /usr/lib/libqt-mt.so.3
#20 0xb76cc53e in sipQVButtonGroup::event ()
   from /usr/lib/python2.4/site-packages/qt.so
#21 0xb6ef8e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#22 0xb6ef9bd6 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#23 0xb65b27ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#24 0xb685f755 in sipKApplication::notify ()
   from /usr/lib/python2.4/site-packages/kdecore.so
#25 0xb6e8a157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#26 0xb6efa4a7 in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#27 0xb6efa5ae in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#28 0xb6e9d42b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb6f11947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#30 0xb6ef7991 in QApplication::enter_loop () from /usr/lib/libqt-mt.so.3
#31 0xb711642c in QDialog::exec () from /usr/lib/libqt-mt.so.3
#32 0xb79a05ea in sipQDialog::sipEmit_destroyed ()
   from /usr/lib/python2.4/site-packages/qt.so
#33 0x080b62c7 in PyEval_EvalFrame ()
#34 0x080b771f in PyEval_EvalCodeEx ()
#35 0x080b7965 in PyEval_EvalCode ()
#36 0x080d94cc in PyRun_FileExFlags ()
#37 0x080d976c in PyRun_SimpleFileExFlags ()
#38 0x08055b33 in Py_Main ()
#39 0xb7e04ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#40 0x08054fa1 in _start ()

```

I'm running the 2.6.17.7 kernel (but it crashes also with 2.6.16.x) with an NVIDIA 6600GT, and I've installed the latest drivers from nvidia.com (1.0-8774). KDE 3.5.4.

Any ideas? :-|

By the way, my screensaver still doesn't lock up the session while starting. I thought it was fixed with the KDE 3.5.4 release, but it's not working :(

---

### Post by Revan on 2006-09-14
Is bumping a really bad thing here? I hope it's not... :-\"

---

### Post by FXWGBill on 2006-12-10
I see this was never answered, and I am having the same problem.  I have done all kinds of searches and not coming up with a thing. This is occuring in my shell, about every time I manually install something... If more info is needed let me know what would help and I'll be happy to post it.  This is the command I invoked: 

gksudo gedit /usr/share/applications/linuxdcpp.desktop


and this was the returned error:

X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

and the item WAS added to my menu system....

any ideas?

---

### Post by FXWGBill on 2006-12-10
Thinking I should add a bit more to that... gedit does come up and I can edit the file; paste in the info, type it in, whatever...  When gedit actually comes up, though, I get two of the X Errors....

sudo gedit /usr/share/applications/azureus.desktop
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


and upon close of gedit, I get my prompt back

---

### Post by blargh on 2007-05-02
Hello,

I recently installed Ubuntu 7.04 (never worked with linux before).
I have the same problem reported above. It happens every time I install something, although installation completes successfully every time.

Thank you! ;)

---

