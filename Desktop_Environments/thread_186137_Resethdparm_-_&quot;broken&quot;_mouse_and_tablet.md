---
title: "Reset/hdparm - &quot;broken&quot; mouse and tablet"
date: 2006-06-01
forum: Desktop Environments
---

### Post by jurgnn on 2006-06-01
Hi,

I just got Dapper final installed and fully working. Then I decided to break everything by trying to speed harddrive up with hdparm and instructions I got from [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

I did 'hdparm -X66 -m16 -c3 /dev/hdc', then mouse stopped moving and I thought that system hang since there was no movement on screen, I pressed ctrl+alt+backspace and got black screen.
- Reset

Got Into desktop, mouse didn't work, luckily I have drawing tablet (volito2) and it still worked, I checked hdparm settings and they were back to normal,I changed mouse from /dev/input/mouse1 to mouse0 in xorg.conf.
- Logout

Mouse works, but tablet doesn't. Tablet used event1 before this, now it uses event3, ts1 and mouse0, none of those works.
Any ideas what is broken?

Harddrive is older maxtor that supports udma mode 5 and those settings should have worked, but I dont really care about hd performance anymore.

---

### Post by jurgnn on 2006-06-02
Fixed problem with re-install, but atleast I learned something.

---

### Post by stanz on 2006-06-25
[quote=jurgnn]Fixed problem with re-install, but atleast I learned something.[/quote] as most of us do! ](*,)
I also have older maxtor, udma5...setting is **X69** .

[quote=LinuxDevCenter.com::]...Of course, **enabling these gets riskier.** (Why is it always a trade-off between freedom and security?)
 The man page mentions trying Multiword DMA mode2, so:    hdparm -X34 -d1 -u1 /dev/hda  [LEFT]...Unfortunately this seems to be **unsupported** on this particular box (it hung like an NT box running a [Java]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2#") app.)  
So, after rebooting it (again in single-user mode), I went with this: hdparm -X66 -d1 -u1 -m16 -c3 /dev/hda[/LEFT]
   [/quote] I worked this info also, and checked it with another, that confirmed the **X69** setting, for udma-5.
Give it another try...with using single user boot, to make adjustments! :rolleyes:

---

