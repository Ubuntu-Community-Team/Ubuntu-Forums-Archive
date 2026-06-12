---
title: "KWin crashes sometimes when browsing websites in Firefox that use flash"
date: 2007-02-02
forum: Desktop Environments
---

### Post by zazery on 2007-02-02
Sometimes when I am browsing flash websites using Firefox it crashes KWin which removes the title bar for all windows and prevents me from typing anything. Each time this happens I kill X and login again to resolve it. I don't understand how it would crash KWin and not Firefox. I've attempted to search the forums but I haven't found anything about a similar issues.

My Version of Flash (Happened in previous versions of 9 and even 7):
"You have version 9,0,21,78 installed"

Firefox Version:
2.0.0.1

Some misc information:
- Running dual monitor setup with ATI Radeon 9600 pro, Mesa drivers.
- Compiled the 2.6.16.1 kernel (occurs with the one pre installed also)
- Installed Kubuntu Dapper Drake

Here's the crash log:
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
[Thread debugging using libthread_db enabled]
[New Thread -1232689472 (LWP 30925)]
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
#9  0xb66efbdf in KWinInternal::Client::screen ()
   from /usr/lib/libkdeinit_kwin.so
#10 0xb672adce in KWinInternal::Workspace::activateNextClient ()
   from /usr/lib/libkdeinit_kwin.so
#11 0xb67390be in KWinInternal::Workspace::workspaceEvent ()
   from /usr/lib/libkdeinit_kwin.so
#12 0xb6739114 in KWinInternal::Application::x11EventFilter ()
   from /usr/lib/libkdeinit_kwin.so
#13 0xb7121457 in qt_set_x11_event_filter () from /usr/lib/libqt-mt.so.3
#14 0xb712e74c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#15 0xb71484db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#16 0xb71bca2f in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#17 0xb71bc952 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#18 0xb71a2a4d in QApplication::exec () from /usr/lib/libqt-mt.so.3
#19 0xb673aa63 in kdemain () from /usr/lib/libkdeinit_kwin.so
#20 0xb7f1d4f0 in kdeinitmain () from /usr/lib/kde3/kwin.so
#21 0x0804e173 in ?? ()
#22 0x00000003 in ?? ()
#23 0x0813ece8 in ?? ()
#24 0x00000001 in ?? ()
#25 0x00000000 in ?? ()

```

Help is appreciated, thanks.

---

### Post by zazery on 2007-02-06
I found a KDE bug report for the problem I am having. I'm currently in the process of updating my KDE which should fix it. Here's the bug report in case someone has the same issue.

[Click here for the Bug Report]("http://bugs.kde.org/show_bug.cgi?id=131905")

---

