---
title: "can't boot into ubuntu | Read-only filesystem error"
date: 2009-06-20
forum: General Help
---

### Post by mongoose_za on 2009-06-20
Hi all,

I'm running Ubuntu 9.04.
Dual partitioned with Windows Vista.

Everything used to work and to my knowledge I hadn't done anything out of the ordinary to cause this error. It's quite severe because _I can't boot in at all_.

When I try boot up my Ubuntu tells me there was an **Unclean shut-down** and wants to scan for errors. At **93% it always fails** then puts me into a terminal mode telling me to run **FSCK manually**. I do this and just push <y> every time to fix every error(I have tried pushing <n> everytime too). Eventually it tells me the that ***MODIFICATIONS MADE*** ***REBOOT REQUIRED*** or something like that. I type REBOOT and then get a **blue screen**. Something about failing **GDM**.

When I reset the machine I land up back at square one :(

---

### Post by pontuz on 2009-06-20
I had exactly the same problem with my Ubuntu 9.04. But i used 64-bit and on a ext4 filesystem so i did reinstall with Ubuntu 32-bit and on a ext3 filesystem and now it works for me...

---

### Post by mongoose_za on 2009-06-20
Ola pontuz,
I'm using 32bit and I'm on ext2... Would prefere not to reinstall :(

---

### Post by hyperdude111 on 2009-06-20
Try any other kernel options on your grub. Tf that fails try the recovery modes.

---

### Post by mongoose_za on 2009-06-20
I'm tried the Recovery mode and it leads to the same error.

---

### Post by mongoose_za on 2009-06-21
Because I'm dual booting I decided to bootup into Windows and run a Scandisk on all my drives. This solved the error I was having with booting into Ubuntu and now it's all working :-D

---

### Post by st0rmcr0vv on 2009-08-18
Doh!! You mean in order to fix my Linux I have to install Windows!?!?!... Does not compute... This seems to be somewhat common. Just recently two of my 9.04 machines decided to upchuck their brains and got some weird filesystem errors out of the clear blue. Thinking about backing up and downgrading to 8.10. 
Ran 8.10 from release to 9.04 release with no issues.

---

