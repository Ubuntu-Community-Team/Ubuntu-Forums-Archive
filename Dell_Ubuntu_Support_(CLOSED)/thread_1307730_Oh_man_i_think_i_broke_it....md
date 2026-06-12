---
title: "Oh man i think i broke it..."
date: 2009-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GuitarG20 on 2009-10-31
trying to hibernate in 9.10...
working fine till right after got image...
then capslock and scrollLock lights on keyboard start flashing??? and freezes...
I think i turned it off eventually using the hold power button feature.

Now it won't load off bios...i try and it just restarts bios...
so i figured i'd load xp pro and I get this message...
"cannot load windows: the following file is corrupt: <root>\system32\ntoskrnl.exe"

I know the two are related...now, what do i do???

(Dell Latitude D400)

---

### Post by Jackyboy86 on 2009-10-31
Owch - the flashing lights are a Kernel Panic.

It's not broken per se - but have you tried looking at the MBR/GRUB?
Stick in the Ubuntu CD to boot from and check it out...
Sorry, I can't remember the commands - and somebody may come and contradict me, but without any more info, I can't think of anything other than a mounting issue!

EDIT: It seems from other posts that people have been having trouble with GRUB2 - it could be that. Try reinstalling GRUB2 using the liveCD.

---

### Post by GuitarG20 on 2009-10-31
Haha, yeah...if I had the cd...I think i'm gonna try and fix windows 1st using the XP cd, according to windows:

[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)


AND: what is this? "MBR/GRUB"   "GRUB2"

---

### Post by viper250 on 2009-10-31
1st mbr is the master boot record on the hard drive it is where grub is installed.
grub is graphical universal boot loader.
 here you select the os.
you can get the cd two ways you can buy the cd for around 1 to 3 $ online or you can download the iso file and burn it to cd using infra recorder 
infra recorder is a free iso burning software.
If you cannot download it a friend can do it for you.

---

