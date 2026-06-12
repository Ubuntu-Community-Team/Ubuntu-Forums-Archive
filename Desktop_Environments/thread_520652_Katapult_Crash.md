---
title: "Katapult Crash"
date: 2007-08-08
forum: Desktop Environments
---

### Post by wired98 on 2007-08-08
Hello all,

I have one nasty of a problem which annoys me since I installed Feisty on my IBM T42p some month ago. Katapult cannot be launched by pressing ALT+SPACE even though the Keyboard shortcut is set properly. Then when I try to open the options dialogue Katapult crashes.

The KDE Crash Manager shows the following debug message:

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
[Thread debugging using libthread_db enabled]
[New Thread -1232935216 (LWP 5563)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0x08057b4c in ?? ()
#7  0x0813fba8 in ?? ()
#8  0xb7f3c300 in ?? () from /lib/ld-linux.so.2
#9  0xb7ecedd4 in KComboBox::setCurrentItem () from /usr/lib/libkio.so.4
#10 0x0805965e in ?? ()
#11 0x081b2c78 in ?? ()
#12 0xffffffff in ?? ()
#13 0x00000003 in ?? ()
#14 0x00000006 in ?? ()
#15 0x00000000 in ?? ()

```

Does anyone of you have the same problem and knows a solution to it???

Thanks for your help in advance...

---

### Post by Happy_Man on 2007-08-08
Open up Konsole and start katapult from there with the command ```
katapult
```. See what errors it gives if it crashes.

---

### Post by wired98 on 2007-08-09
I tried your suggestion but unfortunately there is not much of an information:

```

wired98@box:~$ katapult
Ignored duplicate item: The Mozilla Organization
Ignored duplicate item: Documentation
Ignored duplicate item: Kate
KCrash: Application 'katapult' crashing...
wired98@box:~$

```

When I press ALT+SPACE nothing happens. The katapult launcher window does not open and there is no output on the console as well. And again if I open up the option menu of Katapult the application crashes and you see 'KCrash: Application 'katapult' crashing...' coming up on the console. The KCrash error message is the same then above. However all the other menu entries of Katapult (about, Shortcut configuration) work without crashing Katapult.
The funny thing is I tried the same stuff on another Feisty box I have (completely different hardware) and I get the same result.

I am really lost with this one... :(

---

### Post by wired98 on 2007-09-16
If there is somebody with the same problem:

It helped to delete the configurarion file of katapult which is situated at

~/.kde/share/config/katapultrc

Afterwards when I start katapult I can use ALT+SPACE properly to use katapult. However, the small tray icon is gone, and the configuration file is not regenerated. But at least I can use my beloved katapult again.

:)

---

