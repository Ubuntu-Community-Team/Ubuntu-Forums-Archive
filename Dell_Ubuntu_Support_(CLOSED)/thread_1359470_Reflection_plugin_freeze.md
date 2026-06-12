---
title: "Reflection plugin freeze"
date: 2009-12-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Albertint on 2009-12-19
I am currently having some major trouble using Ubuntu.

I've got an Inspiron 1525 (With GM965) and it is currently freezing instantly at the desktop with _[This bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532")_.

So, what the hell do I do? I'm currently pissed off about this problem, and the only thing I'd know to do is boot the system in shell, but I don't know how to do this.

Can I have some help quick please? I seem to have bad luck with getting replies to my questions.

(BTW, I'm on 9.10)

---

### Post by michael37 on 2009-12-20
> **Albertint said:**
> I am currently having some major trouble using Ubuntu.

I've got an Inspiron 1525 (With GM965) and it is currently freezing instantly at the desktop with _[This bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532")_.

So, what the hell do I do? I'm currently pissed off about this problem, and the only thing I'd know to do is boot the system in shell, but I don't know how to do this.

Can I have some help quick please? I seem to have bad luck with getting replies to my questions.

(BTW, I'm on 9.10)

Try disabling reflection plugin.

Alternatively, disable desktop effects (aka compiz) altogether and try gnome-shell instead.

---

### Post by Albertint on 2009-12-21
K, but how do I do that if:

A. It freezes instantly when booting into gnome.

B. I have no clue how to just load up the shell.

I have no way of reversing this problem since I cant get into my gnome settings, so your strategy is not helping in the least bit.

---

### Post by Albertint on 2009-12-21
Wait, I think I have an idea. When I boot the computer up, it says Grub Loading, so what key do I tap/hold to go to the grub select screen?

---

### Post by michael37 on 2009-12-21
> **Albertint said:**
> K, but how do I do that if:

A. It freezes instantly when booting into gnome.

B. I have no clue how to just load up the shell.

I have no way of reversing this problem since I cant get into my gnome settings, so your strategy is not helping in the least bit.

Reboot in recovery mode.  You will end up in a text console as root.

Get compiz (software that handles desktop effects) out of the way:
```
mv /usr/bin/compiz /usr/bin/compiz.does.not.work
```

Reboot again as normal.  GNOME will default to metacity, a windows manager with desktop effects disabled.

There are less invasive ways from your login screen, but you probably tried them before writing here being quite frustrated and not quite polite.

---

### Post by michael37 on 2009-12-21
> **Albertint said:**
> Wait, I think I have an idea. When I boot the computer up, it says Grub Loading, so what key do I tap/hold to go to the grub select screen?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Albertint on 2009-12-21
Hmm, I was a tad bit rude. I apoligize, as I had another problem and it put me in jerk mode, so I didn't mean to insult.

Anyway, it worked! :) Can't thank (or apologise to) you enough!

Guess I'll be on my way.

Also, on a second note, to get compiz working again, I just did the rename trick in reverse in your second to last post:
```
mv /usr/bin/compiz.does.not.work /usr/bin/compiz


```

---

### Post by michael37 on 2009-12-21
> **Albertint said:**
> Hmm, I was a tad bit rude. I apoligize, as I had another problem and it put me in jerk mode, so I didn't mean to insult.

Anyway, it worked! :) Can't thank (or apologise to) you enough!


You are welcome and apology accepted.

Please mark the thread solved :)

---

### Post by Albertint on 2009-12-21
Oh, almost forgot! :)

---

### Post by no_angst on 2010-03-22
Didn't work for me on 9.10...  Don't know why, but somehow compiz still came on and locked up.

Found another thread that helped me figure out a fix - [http://ubuntuforums.org/showpost.php?p=8186145&postcount=3](http://ubuntuforums.org/showpost.php?p=8186145&postcount=3)

---

