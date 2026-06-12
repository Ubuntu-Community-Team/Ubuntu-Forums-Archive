---
title: "Akonadi does not start. Cannot get my email in Kmail"
date: 2016-04-08
forum: Desktop Environments
---

### Post by JulianLx on 2016-04-08
Kmail does not start. I get the following while running akonadictl start

Starting Akonadi Server... 
Unable to register service as "org.freedesktop.Akonadi.Control.lock" Maybe it's already running?
"[
0: /usr/bin/akonadi_control() [0x42a557]
1: /usr/bin/akonadi_control() [0x42a7b2]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x36d40) [0x7f6b73859d40]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x39) [0x7f6b73859cc9]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x148) [0x7f6b7385d0d8]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x102) [0x7f6b7488cc92]
6: /usr/bin/akonadi_control() [0x42c5dd]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xb0) [0x7f6b74927470]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x11ab3d) [0x7f6b74936b3d]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x31) [0x7f6b7493f721]
10: /usr/bin/akonadi_control() [0x40cdc9]
11: /usr/bin/akonadi_control() [0x4095fd]
12: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7f6b73844ec5]
13: /usr/bin/akonadi_control() [0x4098ef]
]
"
Error: akonadi_control was started but didn't register at D-Bus session bus.
Make sure your system is set up correctly!

Changing the name of ~/.config/akonadi and ~/.local/share/akonadi works helps to make Kmail running again, but cannot access to my mail.

---

