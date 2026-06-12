---
title: "Trouble Installing Ubuntu 9.04"
date: 2009-04-30
forum: General Help
---

### Post by okwhen on 2009-04-30
Hi
new to ubuntu, very knowledgeable winxp.  i have installed ubuntu 9.04 twice and after updating and rebooting the system locks.  installed on a single boot drive maxtor.  the software works fine after installing except after rebooting. MY system x86 and thanks in advance for any help

---

### Post by freonchill on 2009-04-30
when does it lock-up?
bios, grub, ubuntu load, before x login, after x login, before gui load?

---

### Post by Bucky Ball on 2009-04-30
That sounds like something in your updates that's making it choke. It could well be a known problem as 9.04 was only just released and will have it's teething problems. There is a chance it might fix itself in a forthcoming update, but until then ...

Just to double check, everything works dandy until ***after*** the update and reboot???

If so, you could re-boot into recovery and try some of the options: fix broken packages, drop to a root shell and type:

```
dmesg
```Check the last few events for an error(s). Keep an eye out through all of this for any error messages, including when recovery is booting (and possibly where it's stopping).

When the machine locks, can you hit ctl/alt/F1 and drop to a shell? If so, run 'dmesg' there and you will get closer to what is causing the crash. 

Last resort; you could try loading 8.04 LTS and see if you have the same issue after update, perhaps? 

Good luck with it and welcome to the forums. :)

---

### Post by okwhen on 2009-04-30
ASUS bios the system locks after installing, running update manager then reboot.
Thanks [Bucky Ball]("http://ubuntuforums.org/member.php?u=504316") I will install version 8

---

### Post by Bucky Ball on 2009-04-30
Pleasure. Also, this from another post:

> **taurus said:**
> At the initial screen (from Ubuntu LiveCD), pick F4 and use the safe graphics mode to boot/install Jaunty on your machine.

Another option: The Alternate install sometimes works where the Desktop doesn't. It is a text based install and if you have some computer experience, easy.

---

### Post by okwhen on 2009-05-01
I installed ubuntu 8.04 and everything is working OK.  I will wait until 9.04 is revised and try it again.

---

### Post by Bucky Ball on 2009-05-01
Good news. You might like to try 9.04 again in a month or so. Rule of thumb is download the iso, make the disk, stick it in a drawer for a couple of weeks and then install. By that time some of the bugs might be fixed with the new updates rather than causing them, as appears to be the case here.

:)

---

### Post by okwhen on 2009-05-06
I have discovered the reason for the lockup.  I am using an ATI X800 and under add/remove I had selected ATI binary X.Org driver.  Just by selecting this to load will cause the system to lockup on rebooting.

---

