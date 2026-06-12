---
title: "Why do desktop effects run noticable faster using a live CD than on my install?"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2008-01-20
I've tested both Linux Mint and the Hardy alphas; The desktop effects run much smoother/faster using their live CDs than my actual install of Gutsy. Why does this happen?

---

### Post by tgalati4 on 2008-01-21
Do you use the same resolution on your installed version vs Live CD?

The Live CD tends to use a "safe" resolution and rendering effects can be quicker on a smaller resolution graphics space.

Try saving and printing out the /etc/X11/xorg.conf from both and comparing.  There may be differences.

The Live CD runs entirely in RAM and thus doesn't have hard disk I/O's to process.  It's possible that the desktop effects are constantly quering the hard disk.  The other difference is that the Live CD doesn't do system logging while the installed version constantly writes log files which could interrupt the bus and slow the graphics down.

Let us know what you find.

---

### Post by Saint Angeles on 2008-01-21
there is a way to reduce your computer's "swapiness"... meaning it wont use the swap partition as much, it would use your ram more...

im not sure where i read that though.

---

### Post by rainwalker on 2008-01-21
> **tgalati4 said:**
> Do you use the same resolution on your installed version vs Live CD?

The Live CD tends to use a "safe" resolution and rendering effects can be quicker on a smaller resolution graphics space.

Try saving and printing out the /etc/X11/xorg.conf from both and comparing.  There may be differences.

The Live CD runs entirely in RAM and thus doesn't have hard disk I/O's to process.  It's possible that the desktop effects are constantly quering the hard disk.  The other difference is that the Live CD doesn't do system logging while the installed version constantly writes log files which could interrupt the bus and slow the graphics down.

Let us know what you find.

The only live CDs that I'm able to use desktop effects with are the Hardy alphas...the Linux Mint and Gutsy ones don't let me use the effects (even with SKIP_CHECKS=yes)
With the Hardy CDs, though, the size of my window title bars is out of whack, so would it still work to compare the xorg.conf files?

---

### Post by tgalati4 on 2008-01-21
Don't know the answer.  I think Hardy uses an newer xorg (7.3) so that may have some optimization over gutsy.  I have a Linux Mint 4 CD, but I never tried desktop effects from the Live CD so I'm mistaken.

Understanding the details in xorg.conf is not a bad thing.

You can try swappiness:

add to bottom of /etc/sysctl.conf (make a backup first)

# possible performance improvement using 5 or 10
vm.swappiness=5

Post the output of Xorg -version from Hardy

Here's mine from Minty4

tgalati4@minty4:~$ Xorg -version

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux minty4 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

---

