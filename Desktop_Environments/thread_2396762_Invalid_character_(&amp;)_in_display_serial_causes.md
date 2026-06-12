---
title: "Invalid character (&amp;) in display serial causes libmutter crash"
date: 2018-07-20
forum: Desktop Environments
---

### Post by severinson on 2018-07-20
Hey everyone,

I've found a bug that I'd like to report. However, I don't know where and how to do so. Perhaps someone here can point me in the right direction?

Summary based on my understanding of the problem:
My display has a serial number containing the & character.

This serial number gets stored in "./config/monitors.xml", causing the resulting xlm file to be malformed. The relevant section of the file is:
```
        
<monitorspec>
          <connector>DP-2</connector>
          <vendor>BNQ</vendor>
          <product>BenQ BL2710</product>
          <serial>59D00729SL0& </serial>
</monitorspec>

```

The xml file is read when logging in which causes the login to fail. Instead of logging in the user is thrown back to the login screen. The following error message appears in dmesg: 
```
[   77.466768] gnome-shell[2638]: segfault at 0 ip 00007f374835aa44 sp 00007ffdacfb1e20 error 4 in libmutter-2.so.0.0.0[7f37482fb000+156000]
```

Cheers,

---

### Post by Holger_Gehrke on 2018-07-20
Have you read the [sticky thread on bug reporting in the General Help]("https://ubuntuforums.org/showthread.php?t=1011078") forum ? Should contain most of the information you need.

Holger

---

