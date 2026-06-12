---
title: "siggen uses non existing /dev/dsp"
date: 2011-02-28
forum: Education &amp; Science
---

### Post by Humphreybas on 2011-02-28
I installed siggen ([http://packages.ubuntu.com/maverick/siggen](http://packages.ubuntu.com/maverick/siggen)) to use the signalgen but when I try to execute it gives me errors:

```
 siggen
[siggen] No such file or directory : /dev/dsp
bas@Toshu:~$ soundinfo
soundinfo Ver. 2.3.10 (May 2008)  (c) 1996-2008  Jim Jackson
[soundinfo] No such file or directory : /dev/mixer
[soundinfo] No such file or directory : /dev/dsp
bas@Toshu:~$ sinegen

```

How can I fix this?

---

### Post by Humphreybas on 2011-03-20
No solution yet, has probably something to do with the lack of oss and /dev/mixer as well.

I discovered that play can do the same trick so that's my salvation:
Example (check man for more options):
play -n synth 5 sine 300

---

