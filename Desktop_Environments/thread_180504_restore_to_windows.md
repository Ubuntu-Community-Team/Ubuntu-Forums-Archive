---
title: "restore to windows"
date: 2006-05-22
forum: Desktop Environments
---

### Post by matt4 on 2006-05-22
Hi,

Im a newbie to linux and i installed my unix onto a partition. I dont get the option to dual boot or anything. Can someone help me?

I would just like to get back to windows.

Thanks :)

---

### Post by louis_nichols on 2006-05-22
do you want to get back to win keeping ubuntu (a dual boot) or just want your win back and no ubuntu?

what exactly do you see when you boot? don't you see the grub screen? the one with a rectangle and a countdown timer, listing 2 instances of ubuntu, one of memtest and maybe some other stuff?

---

### Post by matt4 on 2006-05-22
[QUOTE=louis_nichols]do you want to get back to win keeping ubuntu (a dual boot) or just want your win back and no ubuntu?

what exactly do you see when you boot? don't you see the grub screen? the one with a rectangle and a countdown timer, listing 2 instances of ubuntu, one of memtest and maybe some other stuff?[/QUOTE]

Hi,

Thanks for the fast response.

I just want my win back on this machine... I removed a partition through dos and now it keeps telling me its missing the operating system. Im using the live cd now. I did see the grub screen :(. All my data is on the other partitions. i hope i dont lose them.

Can you help me here?

thanks a lot :)

---

### Post by matt4 on 2006-05-22
Can anyone help here? It's getting pretty urgent :???:

---

### Post by louis_nichols on 2006-05-22
well, if I understood your situation right, then it is easily solved this way (I'm assuming you have winXP, here; It might be the same with other win editions, but I'm not sure):

1. Boot your pc from a win XP install disk.
2. at the option screen, press R for rescue mode, then follow the instructions to log in to your (assumimingly existent) windows instalation. It should be there, unless you explicitlly deleted it by mistake.
3. When you get the command prompt, issue the next 2 commands, in no particular order:

```
fixboot
fixmbr
```


After this, you should be fine and, on next reboot, be able to log in to your win installation  again, then regain the space you had used for ubuntu (by re-formatting that space as fat or ntfs).

If something has happened and the install cd doesn't see your win partition, then please don't do anything. Your data is still quite likely recoverable, but we'll get to that if we need to.

I might mot answer very quickly, as I'll be a little busy for the next couple of hours.

---

### Post by bigken on 2006-05-22
Hi if fixboot and fdiskmbr fail try **bootcfg /rebuild** thats if your windows xp partion still exists if it dont all is still not lost you could reinstall windows and use ontrack data recovery software I have a used this software numerous time with great sucess ;)

---

