---
title: "Vostro V13 randomly powers off during boot"
date: 2010-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arjun.shankar on 2010-09-05
Hi,

I have Dell Vostro V13 (Came with an Intel SU7300 ULV and Windows 7).

I've installed 10.04 (32 bit) on it and updated the distro right after install and installed the PAE kernel as well (RAM=4G).

Every once a while during boot (say, one in 10 times), the computer powers off. It happens with 10.04 x86 & 10.04 x86_64 AND with Archlinux x86_64 (another distribution which I also tried out).

While booting, I am seeing the boot screen one moment ('Ubuntu' with the blinking LEDs), and the next, my computer is simply, OFF.

So my question is: How do I figure out what is going wrong? Where can I read logs that show me what went wrong during the last boot?

*[EDIT Note: I had asked this question earlier in what I think was a very inefficient way. Hence the rewrite. Unfortunately, after re-wording myself, I think this thread no more fits the 'Dell Support' page, and I don't know how to move it. But I do not want to cross post, so here it stays for now!]*

---

### Post by loftux on 2010-09-17
This is just a "me too" reply. 
Only thing I can add is that it seem to always happen if I do a reboot instead of a shutdown/power up after upgrading software in Ubuntu that suggests a reboot.
Running 10.04 64-bit, A04 bios. There is a A05 bios version out that is "recommended" by dell. Will try that shortly and see if it makes a difference.

---

### Post by firebird89 on 2010-09-30
It's the same for me. Has anyone figured out the reason yet? I'm running 10.04 64bit.

At first there was a problem with mounting a windows partition which made the laptop power off quite often, I fixed this. The power off now occurs not as frequent as before - but still sometimes, that's annoying.

I would be grateful for any advise!

---

### Post by codedash on 2010-10-03
Try 10.10 and let me know. I m interested for this laptop. How is battery life with normal use?

---

### Post by loftux on 2010-10-03
Im now running 10.10, with A05 bios version. This still happens, randomly when trying to boot it powers off. Sometimes I have to try booting 3-4 times before is actually boots.
This has been the same since 10.04 (originally installed version).

But once it has booted it works ok. I like the V13, due to booting problems I rarely turn it off and instead use sleep. And sleep worked fine in 10.04, in 10.10 I've had some power offs on resume. But it is still not a released version so I hope that gets fixed.

Bug report for power off boot problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588194](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588194)

---

### Post by codedash on 2010-10-03
Maybe its a hardware issue. I hope you solve it soon. This random thing reminds me a motherboard problem.

---

### Post by otaviofcs on 2010-11-02
this is a +1 post.

I've just experienced the problem and this time it was tuff. I try to boot 5 times in a row and it was not working. Then I decide to change some boot options. I don't know if this has something to do with having win7 as a dual boot (I had to resize the ntfs partition).

The thing is:

- I already try to disable bluetooth
- Right now I get back to work when I disabled the card reader in the boot options (this note has no card reader entry)

I saw the bug at launchpad and it's exactly this.

I'm currently running:

- Ubuntu 10.10
- Kernel 2.6.35-22-generic

---

### Post by fscodelaro on 2011-02-11
Anyone had any luck solving this problem? I am having the same issue with Ubuntu 10.04.

---

### Post by gertsy on 2011-02-22
Same problem on HP Omnibook 6100 with Ubuntu 10.10. System gets to the point where the speakers usually pop(lightly) and the splash screen would appear and powers off. Turn on and you have to choose an os.  If I boot in ts mode it seems to work...?  This is on an Ubuntu 10.10 dedicated machine.  No dual boot.

Sorry not a dell so out of category but on topic..

---

### Post by arjun.shankar on 2011-04-29
This problem vanished on its own after some updates.

---

