---
title: "Team Fortress 2 Black blocky screen"
date: 2014-08-02
forum: Gaming &amp; Leisure
---

### Post by terrykiwi83 on 2014-08-02
Hey all,

Unusual problem since running Ubuntu 14.04 x64.

When I launch Team Fortess 2 the menu has lots of black blocks. The game play is also black and blocky.

Any ideas?

System specs:
Intel i7 3770
16GB RAM
Integrated Intel HD4000
```

terry@hades ~ $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)

```

Kernel
```

 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

Any advice appreciated.

---

### Post by oldrocker99 on 2014-08-02
The x-0swat PPA, [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/intel-graphics-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/intel-graphics-updates) will install the latest Intel open-source drivers. All Intel video drivers are open-source, which is a Good Thing that Intel is doing.

---

### Post by terrykiwi83 on 2014-08-02
Thanks for the reply, I current have the latest intel drivers installed. I used the Intel Graphics Installer to install version 1.05. Graphics still the same black blocky.
[IMG]http://i57.tinypic.com/6ehsu1.png[/IMG]
[IMG]http://i61.tinypic.com/2a7wua0.png[/IMG]

---

### Post by terrykiwi83 on 2014-08-02
yep I have the latest version installed. 1.05

---

### Post by oldrocker99 on 2014-08-03
This would seem to be a problem you should bring up with Steam, whose game it is. They have an interest in seeing that users can play their games, even the free-to-play ones.

---

### Post by mark156 on 2014-08-12
I'm having a similar problem, with my game looking exactly the same ^^

---

