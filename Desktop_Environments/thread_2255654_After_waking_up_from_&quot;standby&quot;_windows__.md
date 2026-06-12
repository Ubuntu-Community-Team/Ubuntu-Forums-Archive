---
title: "After waking up from &quot;standby&quot; windows / icons not clickable."
date: 2014-12-06
forum: Desktop Environments
---

### Post by xunill2 on 2014-12-06
Hello forum. Have Ubnutu 14.10 64bit installed.

 I have a big problem with my laptop and Ubuntu. If I may awake my computer from standby, then clicking on windows no longer goes. For example, if a firefox window is in the foreground and I click "minimize" in order to display another window in the foreground, nothing happens. Firefox window stays in the foreground. It can also be a Gimp, a VLC window or Chromium window,  does not matter. I have to switch every time the window by "Alt-Tab".
 The icons in each window, which is in the foreground, do not respond to mouse clicks. The icons of Unity are also more not clickable.

 What can you do?

NEDD HELP

```
lspci -nnk | grep "VGA\|'Kern'\|3D\|Display" -A2 00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) Subsystem: Fujitsu Limited. Device [10cf:16c3] Kernel driver in use: i915
```
```
uname -a
Linux 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

