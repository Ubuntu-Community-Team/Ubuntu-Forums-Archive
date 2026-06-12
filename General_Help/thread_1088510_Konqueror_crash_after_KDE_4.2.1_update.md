---
title: "Konqueror crash after KDE 4.2.1 update"
date: 2009-03-06
forum: General Help
---

### Post by ashwinhgtx on 2009-03-06
Hi guys,
I updated my Intrepid KDE 4.2.0 to 4.2.1 yesterday. Now whenever i start Konqueror through the Kickoff menu I get this error

A Fatal Error Occurred
The application Konqueror (konqueror) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc


When I run it from Konsole, I get this;

ashwin@TWINTURBOV8:~$ konqueror
konqueror(6767) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: searchproviders/.desktop not found"
KCrash: Application 'konqueror' crashing...
sock_file=/home/ashwin/.kde/socket-TWINTURBOV8/kdeinit4__0


There is a plasmoid for choosing which profile Konqueror should use while launching. When I use that plasmoid to launch Konqueror, I am able to do so in all the profiles like File Management, KDE Development, Tabbed browsing etc. but not Web Browsing. Konqueror works fine after this.

Oh yeah and when I click on show details in the KDE crash handler dialogue which pops up after the Konqueror crash I get this;

Unable to create a valid backtrace.


This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

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
[New Thread 0xb5f6aaf0 (LWP 7002)]
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
(no debugging symbols found)
(no debugging symbols found)
0xb7f7d430 in __kernel_vsyscall ()
[Current thread is 0 (process 7002)]

Thread 1 (Thread 0xb5f6aaf0 (LWP 7002)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb6559f10 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6559d4e in sleep () from /lib/tls/i686/cmov/libc.so.6
#3  0xb78b7e92 in ?? () from /usr/lib/libkdeui.so.5
#4  0xb78b8854 in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
#5  <signal handler called>
#6  0xb75d40fd in KSycocaEntry::property () from /usr/lib/libkdecore.so.5
#7  0xb3bcd0ed in ?? () from /usr/lib/kde4/konq_aboutpage.so
#8  0xb3bd42e0 in ?? () from /usr/lib/kde4/konq_aboutpage.so
#9  0xb7eab1a6 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#10 0xb7efc739 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#11 0xb7eb2539 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#12 0xb7eb26b1 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#13 0xb7eb318a in ?? () from /usr/lib/libkdeinit4_konqueror.so
#14 0xb7eb3d29 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#15 0xb7eb8c12 in ?? () from /usr/lib/libkdeinit4_konqueror.so
#16 0xb7f3240e in kdemain () from /usr/lib/libkdeinit4_konqueror.so
#17 0x080486f2 in _start ()
#0  0xb7f7d430 in __kernel_vsyscall ()




Anyone out there knows how to fix this?

Thanks in advance.

---

### Post by abn91c on 2009-03-06
same thing happened to me, the easiest fix is open an email with website links, it will launch Konqueror then go to Setings>configure konqueror and chage in "[COLOR="Blue"]when konqueror starts[/COLOR]" from [COLOR="Red"]show information page[/COLOR] to [COLOR="blue"]show my home page or show blank page[/COLOR]

---

### Post by ashwinhgtx on 2009-03-06
I changed my homepage and it's ok now. Any idea why this is happening??

---

### Post by abn91c on 2009-03-06
> **ashwinhgtx said:**
> I changed my homepage and it's ok now. Any idea why this is happening??
No Idea, it's a fix I googled. it is broken with yesterdays upgrade, my guess that introduction page with all the shortcuts to home, trash, network is broken in the latest upgrades.

---

