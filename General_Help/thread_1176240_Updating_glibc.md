---
title: "Updating glibc"
date: 2009-06-02
forum: General Help
---

### Post by DiscipleRayne on 2009-06-02
I'm on Ubuntu hardy 8.04.

Today I tried to build the 1.0 RC2 version of VLC and I got this error:
```

configure: error: Buggy GNU/libc (version 2.5 - 2.7) present. VLC would crash; there is no viable
work-around for this. Check with your distribution vendor on how to update the
glibc run-time. Alternatively, build with --disable-nls --disable-mozilla and
be sure to not use LibVLC from other applications/wrappers.

```

How would I go about updating glibc? The lastest version in the repos is too old.

Also as a side question if anyone has the answer, thank you:

I'm going to be upgrading to Intrepid and Jaunty eventually, and I was wondering... I have no choice, where I live, but to connect to the internet via dial up. I use AOL, because I've yet to find another dial up provider that has as far as I can tell 24 hour session limits, and allows you to hold a continuous connection without ever nuking your account. I use penggy to connect to AOL. Penggy is not in the Jaunty repositories, does this mean it doesn't work with Jaunty? Or that they just didn't put it on the repositories? Thanks in advance!

---

### Post by Arup on 2009-06-02
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

Add this to your repos, it has the latest vlc for Hardy.

---

