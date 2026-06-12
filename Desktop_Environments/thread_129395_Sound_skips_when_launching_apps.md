---
title: "Sound skips when launching apps"
date: 2006-02-13
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-02-13
My music skips on my computer when I do things like launch an application (or type this message quickly!!). I've tried amaroK, kaffeine, mpg123 - they are all the same. This makes me think maybe its a driver problem?

I've been using linux since redhat 9.0, and this is the first time I've had this kind of hardware problem. But kubuntu is also the first distro to support my wireless nic out of the box so I'm happy :)

If anyone can give me a pointer I'd appreciate it.

Regards,

jaralth

---

### Post by hollywoodb on 2006-02-13
you could try adding  

```
elevator=cfq
```

to your kernel line in /boot/grub/menu.list

for example, mine: 

```
kernel          /boot/vmlinuz root=/dev/sda3 ro quiet splash elevator=cfq

```

This helped in my situation, although it doesn't sound like my sound skipping problem was nearly as severe as yours.

[About Linux IO Schedulers]("http://www.wlug.org.nz/LinuxIoScheduler")

---

### Post by QwUo173Hy on 2006-02-15
Thanks hollywoodb. I'm having more problems now so I'm going to do a clean install, and maybe not upgrade to kde 3.5.1 this time. 

Thanks,

jarlath

---

### Post by thesnowysoviet on 2006-02-16
[QUOTE=jarlath]Thanks hollywoodb. I'm having more problems now so I'm going to do a clean install, and maybe not upgrade to kde 3.5.1 this time. 

Thanks,

jarlath[/QUOTE]

Check the CPU usgae when playing media with amaroK ("top -d 2")... I'm running on a 600MHz P3, and amaroK was using 60-70% of the CPU for sustained amounts of time.  I switched to juK, and I recommend the same to you, if you don't mind missing all the lovely album art-retrieval stuff from amaroK.  juK, by comparison, uses about 6% of my processor time, comparable to XMMS' performance back when I had Gentoo on my system.

---

