---
title: "Return to Castle Wolfenstein, no sound"
date: 2008-09-07
forum: Gaming &amp; Leisure
---

### Post by chungy on 2008-09-07
So I just installed RTCW, but I can't get sound to work, plus the plain "wolf" launcher is broken:
$ wolf
./wolf.x86: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Running wolfsp works, but there's absolutely no sound whatsoever... the official RTCW FAQ points over to the Q3A FAQ for the issue, but it was of no help.

---

### Post by curvedinfinity on 2008-09-07
You know what, I tried it seems three or four different ways of getting Wolf ET's sound to work and I never did. However, I just recently started using [http://www.playdeb.net](http://www.playdeb.net) ... and they have ET ... and get this ... the sound works.

I highly recommend using playdeb!

---

### Post by chungy on 2008-09-07
I'm talking about RTCW, not Wolf: ET.

Well anyway, the Windows version seems to work fine enough in Wine, I'll use that for now...

---

### Post by Dave_Jackson on 2009-07-28
Hi all.

I found out how to get sound working in Return to Castle Wolfenstein and Enemy Territory.

I tested these steps on Jaunty 64 bit edition, but they should work for any architecture.

> In the terminal, change to the directory containing the installation. In my case, cd /usr/local/games/wolfenstein.

sudo -i
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "wolfsp.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit 

If you wish to see my original post on this matter, here is a link:
[http://ubuntuforums.org/showthread.php?p=7691130#post7691130](http://ubuntuforums.org/showthread.php?p=7691130#post7691130)

Here is the guide which proved very helpful in arriving at this conclusion.
[https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues]("https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues")

Hopefully I've helped someone enjoy these great games on Linux.

---

### Post by betterhands on 2009-11-14
> **Dave_Jackson said:**
> Hi all.

I found out how to get sound working in Return to Castle Wolfenstein and Enemy Territory.

I tested these steps on Jaunty 64 bit edition, but they should work for any architecture.



If you wish to see my original post on this matter, here is a link:
[http://ubuntuforums.org/showthread.php?p=7691130#post7691130](http://ubuntuforums.org/showthread.php?p=7691130#post7691130)

Here is the guide which proved very helpful in arriving at this conclusion.
[https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues]("https://help.ubuntu.com/community/EnemyTerritory#Sound%20Issues")

Hopefully I've helped someone enjoy these great games on Linux.

thanks a ton--was suffering with this issue forever and this took care of it.

---

### Post by thanius on 2010-07-18
Here's a small tutorial I wrote for 10.04 Lucid Lynx:

[http://ubuntuforums.org/showthread.php?p=9604242#post9604242](http://ubuntuforums.org/showthread.php?p=9604242#post9604242)

---

