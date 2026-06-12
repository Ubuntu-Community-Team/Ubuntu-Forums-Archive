---
title: "Firefox Won't Load."
date: 2009-08-16
forum: Desktop Environments
---

### Post by andrew13321 on 2009-08-16
I get to "Starting up Firefox..." then nothing happens. I tried to load it in Terminal and I get this error.
```
/usr/bin/firefox: 22: Syntax error: word unexpected
```
Also, it appears that Flash freezes randomly on some sites.

---

### Post by Brandon Williams on 2009-08-17
It sounds like one of two things has happened ... either you are not using dash as your /bin/sh program, or your /usr/bin/firefox script has gotten corrupted.

What is the output of this command?
```
ls -l /bin/sh
```
Does it indicate that /bin/sh is a symlink pointing to dash?

What is the output of this command?
```
ls -l /usr/bin/firefox
```
Does it indicate that /usr/bin/firefox is a symlink pointing to some specific version of firefox (e.g. firefox-3.0)?

And finally, run the following two commands:
```
md5sum /usr/bin/firefox
grep firefox.sh /var/lib/dpkg/info/firefox-*.md5sums
```
Does the md5sum output from the first command match the md5sum for firefox.sh displayed by the second command?

---

