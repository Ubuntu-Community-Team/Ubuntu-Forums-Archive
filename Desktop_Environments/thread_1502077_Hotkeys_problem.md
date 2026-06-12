---
title: "Hotkeys problem"
date: 2010-06-05
forum: Desktop Environments
---

### Post by Farfurkis on 2010-06-05
Hello!

I have a very annoying problem: the hotkeys like Ctrl+C, Ctrl+A, Ctrl+Z and so on - all with "Ctrl" won't work in follow programs:

[LIST]
[*]Kate
[*]Keepassx
[*]IDEA
[*]some java programs
[/LIST]
In some programs the Ctrl+* works only when US language selected:

[LIST]
[*]OpenOffice
[*]Mozilla Thunderbird (sometimes, very strange)
[*]Eclipse
[/LIST]
Hotkeys with Alt+* works fine anywhere.
Also the Ctrl+C doesn't work in gnome terminal (but works fine in xterm)

The follow programs works fine:

[LIST]
[*]Mozilla Firefox
[*]gedit
[*]dia
[*]GIMP
[/LIST]
The Ubuntu 8 doesn't have these problems, I upgraded to Ubuntu 9 and later to Ubuntu 10.
[ ~ ] > uname -a                                  [farfurkis@farfurkis-desktop]
Linux farfurkis-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

### Post by Farfurkis on 2010-06-05
SOLVED! :guitar:
Ti fix the bug you must simply move the USA keyboard layout to the top of layouts list and that's all, taken from:
[http://forum.ubuntu.ru/index.php?topic=88286.msg713051#msg713051](http://forum.ubuntu.ru/index.php?topic=88286.msg713051#msg713051)

The bugfix illustration:
[ATTACH]159439[/ATTACH]

---

