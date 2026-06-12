---
title: "Total freeze with 9.10"
date: 2009-05-05
forum: General Help
---

### Post by sevcsik on 2009-05-05
Hi folks,

Linux freezes randomly on my notebook. I can still move the mouse for a few seconds, and then the mouse freezes too (capslock and the power button (short press) doesn't work either). It occours totally random, since an upgrade to 9.04.

I tried the following configurations, and still have the freeze:
Kubuntu 9.04 64bit
Kubuntu 9.04 32bit
Ext4 root
Ext3 root
Gentoo (fresh install, ~x86 and ~amd64)
KDE4/Enlightenment
Compositing on/off

I've also tried downgrading nvidia drivers with no success. Windows and FreeBSD don't freeze, only Linux. The Ubuntu 9.10 liveCD doesn't freeze either. Ubuntu 8.10 worked fine before the upgrade, altough I haven't tested it since I have this problem.

It seems that this is not related to X, since I had a freeze twice during boot (with Kubuntu 9.04 64bit).

It also seems like that it isn't caused by a practicular app, it look totally random.

I've ran memtest and fsck with no errors on all partitions.
I have an ext2 Home partition.

I've looked at kernel.log and Xorg.log.old (maybe filenames aren't exact, I'm on Windows currently) and there are no errors in them.

Can anyone confirm this?

Thanks for the help,
Sevcsik

---

### Post by hagantic42 on 2009-05-07
Yeah I have a very similar problem but just pulling my G5 from the pc puts it all back in order and everything just goes back to normal and the way it freezes with the mouse plugged in is entirely random.

---

### Post by salvachn on 2009-05-07
@ [sevcsik]("http://ubuntuforums.org/member.php?u=213881") and [hagantic42]("http://ubuntuforums.org/member.php?u=553422"):
Why are you using Ubuntu 9.10? Are you testing it for bugs? If you're using Ubuntu on your primary desktop/laptop, then choose Jaunty Jackalope 9.04, or Intrepid Ibex, 8.10. The alpha version of Karmic Koala 9.10 is not meant for production systems. :)

---

### Post by sevcsik on 2009-05-07
Ahhh, sorry, I meant 9.04. I installed the stable version :)

Could someone change the topic please?

---

### Post by sevcsik on 2009-05-07
@hagantic42: My freeze doesn't seem to be linked to the mouse, altough I haven't tested it perfectly. I use an USB mouse.

---

### Post by sevcsik on 2009-05-11
It turned out that it's a CPU cooling issue. Sorry for the unnessecary topic :) Thanks for the comments.

---

### Post by azray on 2009-06-02
Can you elaborate on the cpu cooling issue?

---

