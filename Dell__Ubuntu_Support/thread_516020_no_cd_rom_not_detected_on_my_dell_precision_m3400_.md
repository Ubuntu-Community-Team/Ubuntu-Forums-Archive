---
title: "no cd rom not detected on my dell precision m3400 after the installation"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by moresun on 2007-08-02
I am running kubuntu 7.04 (2.6.20-16-generic) on my dell precision m3400 laptop.
The installation was a little bit tricky because I got always on the LIVE CD start the following message "can't access tty". I fixed this problem by using the approach of [https://bugs.launchpad.net/ubuntu/+bug/99757](https://bugs.launchpad.net/ubuntu/+bug/99757)

But now I am facing an other problem, I can not access my CD Rom.

Does somebody have a similar problem? or even a solution

Thx

MAx

---

### Post by moresun on 2007-08-05
I figured it out.
Because of the workaround on the installation I had do mount the ata driver manually with

modprobe piix

By

---

