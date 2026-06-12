---
title: "Second-life and 12.10"
date: 2012-11-02
forum: Gaming &amp; Leisure
---

### Post by carbatrol on 2012-11-02
Has anyone else been having problems running SL on 12.10?  I have tried Linden, Phoenix, and Firestorm viewers and they all crash on start-up with an error message complaining about lack of space.

---

### Post by Ashtonford on 2012-11-02
> **carbatrol said:**
> Has anyone else been having problems running SL on 12.10?  I have tried Linden, Phoenix, and Firestorm viewers and they all crash on start-up with an error message complaining about lack of space.

 I have been having a problem also not sure if its a bug or what?

---

### Post by TimK01 on 2012-11-02
> **carbatrol said:**
> Has anyone else been having problems running SL on 12.10?  I have tried Linden, Phoenix, and Firestorm viewers and they all crash on start-up with an error message complaining about lack of space.

Yes same here after neither Firestorm, Phoenix or LL's viewer load

---

### Post by cppdeveloper on 2012-12-04
Regarding the fontconfig issue:

I figured a way to make Second Life client run in Ubuntu / Xubuntu / Lubuntu 12.10 32-bit, by fixing the fontconfig issue, until Linden Lab fixes the client:

[http://freesoftwaredeveloper.blogspot.gr/2012/12/how-to-run-second-life-in.html](http://freesoftwaredeveloper.blogspot.gr/2012/12/how-to-run-second-life-in.html)

---

### Post by sabersong on 2013-01-06
I tried the fix on Kubuntu, but it didn't work. Still can't get in. The problem is with libfontconfig 2.9. Several people on other distros have said that rolling back to libfontconfig 2.8 fixes it, but I haven't tried that yet.

---

### Post by sabersong on 2013-01-06
I found [these instructions]("http://bostonpeng.wordpress.com/2012/08/20/howto-fixing-the-problem-with-secondlifelinux-crashing-on-launch/") to fix the problem. They are in effect the same as the suggestions posted here by cppdeveloper, so I'm not sure why these worked for me but cpp's didn't, but I can confirm they work for me on Kubuntu 12.10.

---

