---
title: "Wubi Bootloader won't install in Windows 7 x64"
date: 2009-01-27
forum: General Help
---

### Post by Niktavalos on 2009-01-27
I used Wubi to install Kubuntu 8.10, and the installation went smoothly...except I can't boot into it.  It seems like C:\ubuntu\winboot\wubildr.exe is the proper program to fix it, but it fails with the error message "This program is not compatible with your version of windows" that appears with some programs.  Does Wubi have a known incompatibility with 64-bit windows?  This error message looks like the standard one that's shown when running 16-bit DOS programs, is there any way to manually edit the bootloader?

---

### Post by marnell on 2009-01-28
FYI - I installed ubuntu (wubi) fine in Win 7 x64 beta (build 7000).  Which build are you using?

But, I'm also trying to restore my wubi mbr since I'm migrating my virtual disk install (i.e., wubi) to it's own partition and my mbr entries for both windows and ubuntu were faulty after using Partition Manager to resize my windows partition (should have used a win-based tool, I know...).

So, we have the need to know the answer to the same question: How can we, as Win 7 users, restore our wubi mbr entry in the windows boot loader?

---

### Post by cheapsaket on 2009-01-28
I have successfully installed 8.10 as well in win7 x64 but there is no option to boot into ubuntu on reboot.
Most likely the needed entries did not get added for me.
Is there some guide to manually edit boot entries to make this happen? Its been a while since I did something like this and want to make sure I am not making any errors.

---

### Post by cheapsaket on 2009-01-29
FWIW, I resolved my issue.
I am sure there is a more straight forward way but this sufficed for me.
I downloaded EasyBCD and added an entry for Linux.
Then from the command prompt, I edited the entry using bcdedit /set {ID} path to point it to the right path.
Then I was able to boot into Ubuntu from Win7 boot menu.
HTH someone.

---

### Post by chenxiaolong on 2009-07-22
I know the problem has already been solved, but there is an easier solution to problem.

Before you install, just change the compatibility mode to Windows Vista (no service pack) because both W7 and Vista use a BCD based bootloader, so it will work fine. 

By the way, I tested this on Windows 7 RC (x86 and x64) and Windows 7 build 7600 (x64).

Hope this helps anyone who has this problem!

---

### Post by trail.blazer on 2010-03-02
> **chenxiaolong said:**
> I know the problem has already been solved, but there is an easier solution to problem.

Before you install, just change the compatibility mode to Windows Vista (no service pack) because both W7 and Vista use a BCD based bootloader, so it will work fine. 

By the way, I tested this on Windows 7 RC (x86 and x64) and Windows 7 build 7600 (x64).

Hope this helps anyone who has this problem!

thanks @chenxiaolong it seems to be working. I've confirmed boot loader entries using bcdedit.exe

---

### Post by chenxiaolong on 2010-03-03
You're welcome. I'm glad you got it working.

---

### Post by kaotixx on 2010-09-19
[B]You wont believe it:
But the Idiots forgot to mark the ROOT-file (/).Simply forgot it.
Ubuntu grows worse and worse, sorry[/B]

---

### Post by vevel on 2010-09-27
> **kaotixx said:**
> [B]You wont believe it:
But the Idiots forgot to mark the ROOT-file (/).Simply forgot it.
Ubuntu grows worse and worse, sorry[/B]

What do you mean by not marking the root file?  The root directory is not auto-determined, or something else?  Are you talking about some deficiency in the wubi install, or something with a particular version of 'buntu? 
If so, what version? 
Anyway, I'm not sure what this has to do with your allegation that Ubuntu is getting worse.
More light, less heat, please.

---

