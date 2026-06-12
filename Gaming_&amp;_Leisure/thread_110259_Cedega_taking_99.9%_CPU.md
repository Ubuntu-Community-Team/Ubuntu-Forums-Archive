---
title: "Cedega taking 99.9% CPU"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by Luzbel on 2005-12-30
I'm running Breezy 64 bits on a Intel Pentium D. When I run cedega to play any game, it will run any game smoothly (although it is giving the following message):

XRender could not be loaded
        This is not necessarily a fatal error, however some
        applications require XRender to be installed and
        may not function or display text correctly otherwise.
        Please consult the Cedega Font FAQ for more details

However, when I enter Habbo Hotel (which uses Shockwave) with Hasefroch Firefox, CPU will get 99.9% of his capacity:

user@host:~$

9462 fanny     16   0  460m 140m  11m S 99.9 14.1   0:32.43 wine
 7250 root      16   0  306m  38m 7464 R  3.8  3.8  21:06.91 Xorg
 8082 fanny     16   0 58560  24m 4048 S  3.6  2.4  15:43.50 wish
 9469 fanny     16   0  7032 5136 4852 S  1.9  0.5   0:00.61 wineserver
 7581 fanny     15   0 78980  13m 8392 S  1.5  1.3   0:13.34 artsd
 9328 fanny     15   0 98056  23m  17m S  1.5  2.3   0:01.50 konsole

Now I'm going to try with Wine. Have you any solution to this problem anyway?

---

### Post by sesstreets on 2005-12-30
While cedega is a great program...there still may be some bugs.

Also, I do not think that english is your first language. Hence, could you explain a bit better your problem, like what game.:razz:

---

### Post by Luzbel on 2005-12-30
It's not me who's playing, but I need it to run if I want to keep my cousin using GNU ;)

[www.habbo.com](www.habbo.com) is an online game you need Macromedia's Shockwave to play. Since there are no native Shockwave players for Linux, I installed Firefox 1.5 for Windows platform with cedega so as to my cousin could play.

Cedega is running fine with real games. The usage of the CPU is normal when webbrowsing with Win Firefox, but whenever she enters Habbo, CPU load increases till 99.9%. This is the top command output:

9462 fanny 16 0 460m 140m 11m S 99.9 14.1 0:32.43 wine
7250 root 16 0 306m 38m 7464 R 3.8 3.8 21:06.91 Xorg
etc.

If she closes Habbo, or surf to other website, CPU load comes to a normal state.

Cedega version is 4.3.2, and I'm wrapping it with linux32 utility from repositories since she's using Ubuntu Breezy 5.10 for AMD64.

I hope I explained it better now ;)

---

### Post by ATAQ on 2005-12-30
there can be many bugs in the older cedega versions, maybe you should update the engine. I run cedega 5 on my Pentium D, 64-bit Breezy and It runs pretty well, cpu always stays fast with no errors.

---

### Post by Luzbel on 2005-12-30
Thanks! I'll try. Do you use the pre-debianized package or did you compiled it yourself? Are you using: 5.0, 5.0.1, 5.0.2 or 5.0.3?

---

