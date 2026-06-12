---
title: "ristretto ignores command line options?"
date: 2012-01-19
forum: Desktop Environments
---

### Post by Kilarin on 2012-01-19
I must be doing something stupid.
ristretto --help shows that there are commandline options for:
  -f, --fullscreen         Start in fullscreen mode
  -s, --slideshow          Start a slideshow

But when I try to use these options, the app seems to just ignore them.

ristretto pic1.jpg pic2.jpg pic3.jpg 
will bring up ristretto showing pic 1 of 3 just like I expected.
BUT
ristretto -s pic1.jpg pic2.jpg pic3.jpg 
behaves exactly the same as the command without the -s.  Same for --slideshow.  pic 1 of 3 shows, but no slideshow begins.

also:
ristretto -f pic1.jpg
does NOT start in fullscreen mode.  (--fullscreen either)

Am I missing something obvious?

Running ubuntu 11.04 converted into Xubuntu xfce 4.8.0

---

### Post by Toz on 2012-01-19
According to this closed bug report, [https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/607473]("https://bugs.launchpad.net/ubuntu/+source/ristretto/+bug/607473"), the fullscreen issue is fixed for version 0.3 (precise (12.04)). Nothing there, however, about the slideshow functionality. You could create a bug report for it.

---

### Post by LewisTM on 2012-01-19
Looking at the man page
```
man ristretto
```
we don't see the -f and -s switches. They were probably removed but  still appear in the --help output.

If you want those functions your can substitute ristretto for gthumb which does support the -s and -f command line options.

Cheers!

---

### Post by Kilarin on 2012-01-19
thanks, I looked at --help and not at man.

I'll give gthumb a try.

---

