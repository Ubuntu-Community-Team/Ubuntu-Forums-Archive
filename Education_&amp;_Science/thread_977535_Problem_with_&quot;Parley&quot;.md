---
title: "Problem with &quot;Parley&quot;"
date: 2008-11-10
forum: Education &amp; Science
---

### Post by Kompost on 2008-11-10
Hi, i've got a small problem with the vocable learning program "parley".
If I push "Start practice" the program crashes...

```
A Fatal Error Occured
The application Parley (parley) crashed and caused the signal 6 (SIGABRT).
Please help us improve the software you use by filing a report at http://bugs.kde.org. Useful details include how to reproduce the error, documents that were loaded, etc.

Details:
Application: Parley (parley), signal SIGABRT
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
[New Thread 0xb61398d0 (LWP 5384)]
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
#5  0xb809b430 in __kernel_vsyscall ()
#6  0xb6850880 in raise () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6852248 in abort () from /lib/tls/i686/cmov/libc.so.6
#8  0xb75a5795 in qt_message_output () from /usr/lib/libQtCore.so.4
#9  0xb75a5872 in qFatal () from /usr/lib/libQtCore.so.4
#10 0xb75a58cc in qt_assert_x () from /usr/lib/libQtCore.so.4
#11 0xb8037c8f in KEduVocDocument::identifier ()
   from /usr/lib/libkeduvocdocument.so.4
#12 0x08090189 in _start ()
#0  0xb809b430 in __kernel_vsyscall ()
```

I already removed- and reinstalled the program but that wasnÄt the solution. I hope you can help me :)

(I'm using Ubuntu 8.10)

---

### Post by paulymorph on 2009-01-10
I also receive the same error - for me it occurs when I have completed all the questions in the multiple choice quiz.

---

### Post by LaserJock on 2009-01-11
Could you guys do me a huge favor and file a bug report about this? The URL for filing a bug would be:

[https://bugs.launchpad.net/ubuntu/+source/kdeedu/+filebug](https://bugs.launchpad.net/ubuntu/+source/kdeedu/+filebug)

You can also read [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) if you need help on filing a bug.

-LaserJock

---

### Post by paulymorph on 2009-01-11
I have reported this bug [https://bugs.launchpad.net/bugs/316256](https://bugs.launchpad.net/bugs/316256)

---

