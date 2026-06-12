---
title: "[SOLVED] mini 9 custom kernel wireless"
date: 2008-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iggykoopa on 2008-12-16
I just got my mini 9 in last night and compiled a new kernel for it(2.6.28-rc8) everything works great except for wireless. The wl driver that it uses by default hasn't been patched for it yet. My question is what would you guys recommend, going with fwcutter for now or ndiswrapper? just wondering which one performs better with these cards.

---

### Post by anjilslaire on 2008-12-17
The wireless should work fine by itself after a full update from the repo's via a wired connection.

---

### Post by iggykoopa on 2008-12-17
I'll give it a try tonight when I get home.

---

### Post by cmspider on 2008-12-17
You can download broadcom's wl driver from here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

My understanding is that the fwcutter solution doesn't support the wireless in the mini 9.

One unrelated issue I've noticed with the 2.6.28-rc kernels is that the disk gets stuck in udma2 (rather than udma5) after a suspend/resume cycle.

I have a bug open ([http://bugzilla.kernel.org/show_bug.cg1?id=12202](http://bugzilla.kernel.org/show_bug.cg1?id=12202)) on this, and it does appear getting attended to.  There is a workaround too - see the bug there for details.

---

### Post by gavron on 2008-12-25
The version provided by Broadcom does not build on kernel 2.6.28.

Try the patch at [http://www.myehud.com/mini9/wl.patch](http://www.myehud.com/mini9/wl.patch)

Full instructions at [http://www.myehud.com/mini9](http://www.myehud.com/mini9)

Ehud
P.S. When I say "Try the patch" it's been working since I wrote it 20 minutes ago ;)

P.P.S. FWCUTTER won't help you.  The b43 RE team hasn't yet reverse engineered that device (BCM4312 PCI ID ...4315)

---

### Post by iggykoopa on 2008-12-25
Thank you very much, I've been trying every way I can think of to get it to compile, I'll give it a spin in a few minutes.

---

### Post by iggykoopa on 2008-12-26
Thanks again, I just tried compiling, it works great. I've been trying to get this working for days.

---

### Post by gavron on 2008-12-26
> **iggykoopa said:**
> Thanks again, I just tried compiling, it works great. I've been trying to get this working for days.

You bet :)  As you can probably tell from my page, I love Ubuntu on the Mini 9.  I just don't like being locked into Dell's build.  

I also can't wait until the b43 team reverse engineers the 4315, so that we will have a working in-kernel driver (and not a binary blob that taints the kernel).

Best regards,

Ehud

---

### Post by iggykoopa on 2008-12-26
I know what you mean, I used the dell version for about 10 minutes before I installed crunchbang linux. Now I just need to get one of the international keyboards, much better layout.

---

### Post by armandh on 2008-12-26
I used the latest Ubuntu 8.10
live from a USB mem stick
the wlan works

---

### Post by gavron on 2008-12-28
> **armandh said:**
> I used the latest Ubuntu 8.10
live from a USB mem stick
the wlan works

The question was how to use a custom kernel.  The kernel you have from Ubuntu is old.

Ehud

---

### Post by fedleo on 2009-01-21
> **gavron said:**
> The version provided by Broadcom does not build on kernel 2.6.28.

Try the patch at [http://www.myehud.com/mini9/wl.patch](http://www.myehud.com/mini9/wl.patch)

Full instructions at [http://www.myehud.com/mini9](http://www.myehud.com/mini9)

Ehud
P.S. When I say "Try the patch" it's been working since I wrote it 20 minutes ago ;)

P.P.S. FWCUTTER won't help you.  The b43 RE team hasn't yet reverse engineered that device (BCM4312 PCI ID ...4315)Can make it work on 2.6.28.1-ultimate...
```
effe@effe-netbook:~/wl$ sudo patch -p1 < wl.patch
patching file src/wl/sys/wl_iw.c
Hunk #1 FAILED at 943.
Hunk #2 FAILED at 964.
Hunk #3 FAILED at 976.
Hunk #4 FAILED at 1001.
Hunk #5 FAILED at 1013.
Hunk #6 FAILED at 1028.
Hunk #7 FAILED at 1046.
Hunk #8 FAILED at 1059.
8 out of 8 hunks FAILED -- saving rejects to file src/wl/sys/wl_iw.c.rej
```and if I modify the file with #if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,28) ) to #ifdef PATCH_2628 and at the top add a    #define PATCH_2628:
```
effe@effe-netbook:~/wl$ sudo patch -p1 < wl.patch
patching file src/wl/sys/wl_iw.c
patch: **** malformed patch at line 24:  			iwe.cmd = SIOCGIWMODE;
```Any help?

---

