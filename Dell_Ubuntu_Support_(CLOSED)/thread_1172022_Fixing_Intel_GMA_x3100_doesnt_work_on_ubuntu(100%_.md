---
title: "Fixing Intel GMA x3100 doesnt work on ubuntu(100% work)"
date: 2009-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chidokatoit on 2009-05-28
I got it working by commenting out a line in the /usr/bin/compiz file

T="$T 8086:2a02 " # Intel GM965

to

#T="$T 8086:2a02 " # Intel GM965

then you need to switch on the effects using the the system > preferences > appearance visual effects tab.

GOOD LUCK!

---

### Post by pormogo on 2009-05-28
I have an m1330n and I was under the impression that the GMA3100 (as shown below) was now supported under compiz. I remember editing the old blacklist file back in 7.04 when it was a blacklisted card. What issue is this in regaurds to? I am using the following version of the GMA3100

*VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)*

Aside from horrid performance without UXA enabled in 9.04 it's been working reasonably well for me for quite some time.

---

### Post by chidokatoit on 2009-05-29
I just surf the web and found it right here [http://benhay.blogspot.com/2009/04/five-minutes-of-ubuntu-904.html](http://benhay.blogspot.com/2009/04/five-minutes-of-ubuntu-904.html)

---

