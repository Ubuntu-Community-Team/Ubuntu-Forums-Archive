---
title: "2 hopefully quick questions...."
date: 2006-08-04
forum: Desktop Environments
---

### Post by ckasprzak on 2006-08-04
I'm running on a Athlon 64 and will be waiting to jump to 64bit, mainly because ease of use.  But I would like to get the best out of my non 64bit Ubuntu install.  I know there are several other kernels out there and was wondering which would run better on a K8.  Should I go with a 686 or a K7?  My common sense would say K7 but I just want to make sure that would perform the best.

Also just a little grip, I have a Logitech G5 mouse and I live for my back key on the mouse.  Is there a way to get this to work in Firefox on Ubuntu?

Thanks in advance! :)

---

### Post by rattlerviper on 2006-08-04
> **ckasprzak said:**
> I'm running on a Athlon 64 and will be waiting to jump to 64bit, mainly because ease of use.  But I would like to get the best out of my non 64bit Ubuntu install.  I know there are several other kernels out there and was wondering which would run better on a K8.  Should I go with a 686 or a K7?  My common sense would say K7 but I just want to make sure that would perform the best.

Also just a little grip, I have a Logitech G5 mouse and I live for my back key on the mouse.  Is there a way to get this to work in Firefox on Ubuntu?

Thanks in advance! :)

K7, but don't delete your previous kernal until you have used the K7 for awhile and know that it is not causing you any problems(that way you can always boot the 386 kernal.

---

### Post by RAOF on 2006-08-04
> **rattlerviper said:**
> ...
FYI most software is 32 bit in Linux, so it may act weird or nor run at all with the K7 kernal(not speaking from experience here, just what I have read).

I'm not sure what you're trying to say here, but just to clear it up: the -k7 kernel **is** an IA32 (aka: 32 bit aka: i386) kernel.  None of your software will blink an eyelid.

It is probably the best kernel for your Athlon64.  It **also** probably won't make much of a difference over the -386 kernel.

---

### Post by rattlerviper on 2006-08-04
> **RAOF said:**
> I'm not sure what you're trying to say here, but just to clear it up: the -k7 kernel **is** an IA32 (aka: 32 bit aka: i386) kernel.  None of your software will blink an eyelid.

It is probably the best kernel for your Athlon64.  It **also** probably won't make much of a difference over the -386 kernel.

I apoligize, I thought the k7 kernal was a 64 bit.

---

### Post by ckasprzak on 2006-08-04
Well the K7 SHOULD be 3dnow optimized where as the i386 wouldn't be, right?

Also any help with the mouse situation ?

---

### Post by RAOF on 2006-08-06
> **ckasprzak said:**
> Well the K7 SHOULD be 3dnow optimized where as the i386 wouldn't be, right?

Also any help with the mouse situation ?
The K7 kernel has the option of using 3dnow instructions, true.  On the other hand, I don't think the kernel's doing anything that would benefit from them, and gcc would need to be smart enough to use them without prompting from the programmers.

No idea on the mouse, sorry.

---

### Post by ckasprzak on 2006-08-07
Can anyone help me on the mouse situation please?

---

### Post by Mooie on 2006-08-07
I too have the Logitech G5, and it would be really nice to get the extra button working.  That button helps me more w/ gaming than anything, and it seems that the drivers for the mouse just dont do anything at all with it.  when i click the button (to bind it to somthing in a game) nothing happens, so thats why i guess its a driver issue, any info would be greatly appreciated :D

---

### Post by Mooie on 2006-08-07
oops, i forgot to mention that the game I tried it w/ was World of Warcraft, which i was emulating with cedega, which could have caused the problem (just thought of that, sorry).  When I get home i will try it with Quake4 and post my findings.

---

### Post by Mooie on 2006-08-07
ok, i'm at home now, and i just tested it w/ quake4, it calls the back button "mouse 8"  so i dont know what to tell you about firefox ](*,)

---

### Post by Crashmaxx on 2006-08-07
[http://ubuntuforums.org/showthread.php?t=44191&highlight=mouse+buttons](http://ubuntuforums.org/showthread.php?t=44191&highlight=mouse+buttons)

Step two should be all you need for firefox to work. The rest is only really needed to get it to work in nautilus. Works great for me with a Microsoft Intellimouse Explorer. Should work fine with any mouse though.

---

### Post by ckasprzak on 2006-08-18
Thanks I'll give it a whirl when I get home.

---

