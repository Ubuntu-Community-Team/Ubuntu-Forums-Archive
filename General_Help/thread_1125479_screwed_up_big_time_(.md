---
title: "screwed up big time :("
date: 2009-04-14
forum: General Help
---

### Post by georgec32 on 2009-04-14
I'm a newbie to linux, but am trying to do something for work that is best done in linux (plus I'd just like to learn).  I installed Ubuntu 8.10 on my desktop and it worked just fine.  I played around with it for about 3 days .. then I shut down (used the 'shut down' icon) and everything started shutting down normally but I went back into the room about 10-15 minutes later & the screen was dark but my computer was still running (warp speed, judging by the increased noise).  I couldn't get anything to show on the screen, so I foolishly just turned the power off.  Now I can't boot into Ubunto anymore .. I tried to re-install, but it tells me I can't partition the disk now.  I'd like to totally wipe ubunto from my system & start over but I'm not sure how to do that, and I'm very cautious not to trash my entire computer.  I'm running M$ Windows XP (I think SP2).  ANy advice on how to proceed troubleshooting/fixing this?

---

### Post by fooman on 2009-04-14
you say you are running windows xp? ...is that installed on the same hard drive as ubuntu? ...or on a separate drive?

how are you able to boot into windows? ...does it boot right into xp automatically? ...or do you get a "grub" (ubuntu's bootloader) boot menu with ubuntu and windows xp listed as choices?

---

### Post by wpshooter on 2009-04-14
Boy, I hope that this is not a work computer that you did not have permission to install Ubuntu on and even more I hope that you have a XP installation disk, so that you can recover the MBR !!!

---

### Post by georgec32 on 2009-04-14
> **fooman said:**
> you say you are running windows xp? ...is that installed on the same hard drive as ubuntu? ...or on a separate drive?

how are you able to boot into windows? ...does it boot right into xp automatically? ...or do you get a "grub" (ubuntu's bootloader) boot menu with ubuntu and windows xp listed as choices?

they're on the same hard drive.  I get a choice when booting, XP or ubuntu.  When I pick ubuntu, I get a grub prompt but can't get any farther ..

---

### Post by georgec32 on 2009-04-14
not a work computer :)  Also, my XP boots & runs just fine.  THat's one reason I'm being pretty cautious in trying to fix the ubuntu problem .. I want to KEEP my XP running :)

---

### Post by LowSky on 2009-04-14
sounds like a bad Ubuntu install.

How did you install ubuntu, LiveCD or Wubi?

---

### Post by georgec32 on 2009-04-14
> **LowSky said:**
> sounds like a bad Ubuntu install.

How did you install ubuntu, LiveCD or Wubi?

I downloaded the ISO to a CD and installed it from that.  I also used the same CD to install it on my work laptop, but I can't touch that one for fear of screwing it up :)

---

### Post by Alekz_ on 2009-04-14
Can you tell "when" the ubuntu boot stops? You're able to select ubuntu for boot up.. But it stops just after you hit Enter?? Or maybe it start booting and crashes?

[]'s

Alekz_

---

### Post by georgec32 on 2009-04-14
> **Alekz_ said:**
> Can you tell "when" the ubuntu boot stops? You're able to select ubuntu for boot up.. But it stops just after you hit Enter?? Or maybe it start booting and crashes?

[]'s

Alekz_

forgive me if I use the wrong terminology .. I'm quite the newbie at linux.  When my computer boots & I select 'ubuntu' instead of Windows XP, it goes directly to the 'grub' prompt .. I tried all the menu options but no good.  I can boot just fine from the CD, but when I try to re-install on my HD, it gets to the partition option & tells me it can't perform the partition ..

---

### Post by durand on 2009-04-14
The grub prompt is the menu which you select which OS to boot to. Everything after that is ubuntu unless it gives you a grub error like "Partition not found" or something to that effect?

---

### Post by Alekz_ on 2009-04-14
ok.. So, you have two boot loaders? One of windows and the grub? That's it?

If so, the MBR is on your Win partition and you can do whatever you want with your Linux patition.. If it's not like this, please, try to explain again, becouse it isn't clear yet...

---

### Post by georgec32 on 2009-04-14
> **durand said:**
> The grub prompt is the menu which you select which OS to boot to. Everything after that is ubuntu unless it gives you a grub error like "Partition not found" or something to that effect?

I get a grub prompt like:  grub>

I didn't get that when it was working.  From the grub prompt, I press esc to get the menu, but it's mostly 'find' this & that (I tried all of them .. none worked).  There is a re-boot item in the menu, but that only re-boots my computer.  There is also a halt command that shuts me down.

---

### Post by georgec32 on 2009-04-14
> **Alekz_ said:**
> ok.. So, you have two boot loaders? One of windows and the grub? That's it?

If so, the MBR is on your Win partition and you can do whatever you want with your Linux patition.. If it's not like this, please, try to explain again, becouse it isn't clear yet...

apparently true re 2 boot loaders, windows & grub.  But I can't figure out how to delete the linux partition or scrub it somehow so that I can re-install from the CD  ...

---

### Post by georgec32 on 2009-04-14
> **georgec32 said:**
> apparently true re 2 boot loaders, windows & grub.  But I can't figure out how to delete the linux partition or scrub it somehow so that I can re-install from the CD  ...

My boot.ini has the following two lines:

multi(0)disk(0)rdisk(0)partition(1)WINDOWS="Microsoft Windows XP Home 
Edition" /fastdetect /NoExecute=OptIn

C:\wubldr.mbr="Ubuntu"

---

### Post by georgec32 on 2009-04-15
> **georgec32 said:**
> My boot.ini has the following two lines:

multi(0)disk(0)rdisk(0)partition(1)WINDOWS="Microsoft Windows XP Home 
Edition" /fastdetect /NoExecute=OptIn

C:\wubldr.mbr="Ubuntu"

got it fixed :)   I booted from the Ubuntu CD, then -updated- Ubuntu, then I was able to remove it & re-install.  This time, I installed it on an external drive so I can use it for my laptop and my desktop ..

Thanks to all who offered me great advice!

georgec32

---

