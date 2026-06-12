---
title: "Double Volume Icons"
date: 2012-11-02
forum: Desktop Environments
---

### Post by hg21 on 2012-11-02
Hi,

Since moving to 12.10 I find any CD drive or USB stick I add shows 2 icons on the desktop.  It also applies to an unmounted partition on the hdd.

---

### Post by Uncle Spellbinder on 2012-11-02
Same here. Very weird. My mounted volumes show twice each in file manager and on the desktop.

---

### Post by Elfy on 2012-11-02
It's a bug - waiting for the fix to turn up in proposed.

There is apparently a [workround]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375/comments/20") which I've not bothered with.

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375)

---

### Post by Uncle Spellbinder on 2012-11-02
Found a workaround. It's some sort of bug:

[http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition](http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition)


EDIT:
Elfy beat me to it. :)

---

### Post by Elfy on 2012-11-02
Actually the desktop is seperate - [https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1072137](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1072137)

---

### Post by verymadpip on 2012-11-03
I have 2 machines running Xubuntu 12.10.
Only one of them exhibits this behaviour.
I think that's interesting.

---

### Post by Elfy on 2012-11-03
Do they both have unmounted partitions?

---

### Post by verymadpip on 2012-11-04
> **Elfy said:**
> Do they both have unmounted partitions?

Elfy; no they don't.  I was thinking that may have something to do with this "issue".

The machine that behaves this way has a second HDD (XP Pro) in there & the floppy drive (yes, floppy drive!) is still connected up - although it's rarely, if ever, used.
Both devices display doubled up on the desktop & in the Thunar side pane, as does a USB flash drive when it's plugged into the machine.

The settings editor GUI "fix" for the desktop  works until the machine is rebooted, it then needs to be set again.

The box with the single xubuntu HDD works pretty well, (apart from a couple of bugs which are irrelevant here).

---

### Post by verymadpip on 2012-11-04
Ok, weirdly, the duplicates in the Thunar side pane have just vanished; desktop duplicates remain.

As far as I'm aware I've done nothing to correct this, nor do I recall any updates happening.
I have installed one or two applications though...

Edit: Nope, I still have duplicates all over the place.

---

### Post by LewisTM on 2012-11-09
The latest Thunar update fixed the side pane problem. As for the desktop, a prompt F5 straightens things out instantly.

Cheers!

---

### Post by whoya on 2012-11-24
Hello all

Pressing F5 worked good for me too.

thanks lewis

---

