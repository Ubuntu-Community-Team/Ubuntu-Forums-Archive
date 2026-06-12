---
title: "SNES9X GTK+ Packages"
date: 2008-02-19
forum: Gaming &amp; Leisure
---

### Post by stevejesus on 2008-02-19
**Update, this package is temporarily broken.  Please do not download.**

Ok guys, I saw that a few of you guys have been oohing and aahing over this new SNES9X GTK+ interace, so...  I took the SNES9X source code, and patched it with the authors GTK+ code and made some packages.

So, if anyone is using AMD64 you can try my package now.  Get it here [http://www.myfootinyourass.com/Ubuntu/64/]("http://www.myfootinyourass.com/Ubuntu/64/")

Later tonight when I can make my way upstairs, I will get the 32-bit package together.  And shortly after that, I will have a PPC one too!

[IMG]http://www.myfootinyourass.com/Ubuntu/screens/snesgtk17.png[/IMG]
:popcorn:

---

### Post by RemmyLee on 2008-02-19
Small Problem. There is no binary in the Deb.

---

### Post by stevejesus on 2008-02-19
hmmm...  thats a big problem.  I built the package a second time, and again, no binary.  I'll have to get with bear0so...  In the meantime, no one download this.

---

### Post by RemmyLee on 2008-02-19
Understandable. Checkinstall can be wonky at times. I'm bashing my head in trying to get OpenGL to work in it. It's driving me nuts. Configured for it, compiled with, but it's completely greyed out in the menu.

---

### Post by stevejesus on 2008-02-19
Thats bizarre...  are you using v.17?  I saw your post over at snes9x forums.  It seems to work ok for me...  there are other issues beyond that though...
Would you recommend using anything else to build a package with?  Honestly, checkinstall is the only thing that I know how to use...

---

### Post by DoktorSeven on 2008-02-20
I believe it's the way the makefile pretty much completely ignores the "install" path that is normally passed to it by configuration scripts, so checkinstall and the way I build (using dh_make and dpkg-buildpackage) doesn't exactly work.

The binary's self-contained (just the executable) so simply distributing it (as the person on the snes9x forum did) and telling people the dependencies should suffice, though I know it's not as easy as just building the package.

---

### Post by stevejesus on 2008-02-20
DoktorSeven,
    it would be handy for users is they could install a .deb, and then have the binary installed to a logical location...  Can you help me with this DoktorSeven?

---

### Post by DoktorSeven on 2008-02-20
That's what I tried to do last night and couldn't because of that problem.  I just ended up building from source normally (./configure / make; not even make install worked without hacking on the Makefile) and copying the binary to /usr/local/bin on my machine... 
:(

---

### Post by RemmyLee on 2008-02-20
Yeah. That's where the problem stems from. Checkinstall along with most other auto packagers require an install target in the makefile to generate the proper targets in the rules file.

---

### Post by grossaffe on 2008-03-18
I've been looking into learning how to build a .deb package, i'll see if i can make a 64-bit package of this; you know, try to give back the the comunity that's helped with all my no0b linux needs.  no promises though, i'm still pretty much a novice.

---

