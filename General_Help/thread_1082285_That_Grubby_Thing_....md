---
title: "That Grubby Thing ..."
date: 2009-02-27
forum: General Help
---

### Post by Eyore15 on 2009-02-27
I came home to find my surge protector tripped.  I have an IBM Thinkcenter P4 2.8 running Windows and Wubi Ubuntu.  When I rebooted the machine into Ubuntu after re-setting the surge protector I got as far as the GRUB > menu; then everything stopped.

The machine boots just fine into Windows XP.  The Wubi installation is 8.10 - Intrepid Ibex.

If I'm reading "The Practical Guide to Ubuntu Linux" by Mark Sobell correctly, there is likely a problem with the Master Boot Record (MBR).  I can say MBR -- that doesn't mean I really know much about it.

Is there a way to repair my installation, or should I uninstall and then reinstall?

I am/was using Thunderbird for email -- I really don't want to lose all my addresses, saved mails, etc.

Thanks for your help

mcm

---

### Post by jwbrase on 2009-02-27
> **Eyore15 said:**
> I came home to find my surge protector tripped.  I have an IBM Thinkcenter P4 2.8 running Windows and Wubi Ubuntu.  When I rebooted the machine into Ubuntu after re-setting the surge protector I got as far as the GRUB > menu; then everything stopped.

The machine boots just fine into Windows XP.  The Wubi installation is 8.10 - Intrepid Ibex.

If I'm reading "The Practical Guide to Ubuntu Linux" by Mark Sobell correctly, there is likely a problem with the Master Boot Record (MBR).  I can say MBR -- that doesn't mean I really know much about it.

Is there a way to repair my installation, or should I uninstall and then reinstall?

I am/was using Thunderbird for email -- I really don't want to lose all my addresses, saved mails, etc.

Thanks for your help

mcm

I've heard that Wubi is exceptionally vulnerable to hard shutdowns, because of the fact that it's hard drive is a virtual one inside of Windows' NTFS partition. (That's why it's recommended for trying out Ubuntu to see if you like it, but not as a permanent install). You may be able to do a disk defrag or something from within Windows to repair it, but you'd want to ask others about the exact procedure for doing that.

---

### Post by thtrgremlin on 2009-02-27
Well, if you can boot to windows then your "MBR" is fine. Need a little more information about what is going on.

I've setup wubi for a few people before. So if I remember correctly, you startup, and you get the "Windows Bootloader" where you pick either XP or Ubuntu. You say windows will start up fine. What happens if you select Ubuntu? Did it give the grub boot menu after that? Does it just freeze with a blank screen? Need to know more about what you are seeing or not seeing that you usually see.

---

### Post by FraggedLocust on 2009-02-27
I've had a bunch of problems with Wubi. Even on a regular restart in both Windows and Ubuntu, it still manages a kernel panic.

---

### Post by Tek-E on 2009-02-27
I dont know of a way myself how to "fix" the problem other than just un-installing and re-installing.  But I do know for a fact you should be able to access all of your saved files that were on ubuntu from inside your windows partition.  And even if you can't Find your ubuntu files then grab a linux live cd and boot into it and then you should be able to access those important files and save them.  and then you could re-install.

---

### Post by avtolle on 2009-02-27
Eyeore15: Take a look at [http://ubuntuforums.org/showthread.php?t=959686](http://ubuntuforums.org/showthread.php?t=959686) and see if there's anything there that might help you out.

---

### Post by caljohnsmith on 2009-02-27
Probably the first place I would start if I were you would be to do a "chkdsk" on the Windows partition that has Grub. If you open a command window in Windows (Start > Run > "cmd"), then type:
```
chkdsk /r
```
And on the next reboot it should do a chkdsk on the Windows partition. That might be all it takes to get Ubuntu going again after a hard shutdown, but let me know if that works or not.

---

### Post by thtrgremlin on 2009-02-28
If the virtual disk was actually corrupted by the hard shutdown, I think that is just one of the major disadvantages of NTFS. However, I still think that is worthy of a bug report, even if there isn't much that can be done. Include a link to this thread.

---

