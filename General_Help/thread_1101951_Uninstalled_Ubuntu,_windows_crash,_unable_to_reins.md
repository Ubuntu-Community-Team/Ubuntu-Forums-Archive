---
title: "Uninstalled Ubuntu, windows crash, unable to reinstall Grub from LiveCD."
date: 2009-03-20
forum: General Help
---

### Post by Welek on 2009-03-20
The title basicly says it all, I uninstalled ubuntu, merged my partitions, crash on windows, only to find a grub error, I've already tried.

sudo grub
root (hd0,0)
setup (hd0)
exit

This all works until the end, seeing as I crashed on windows it has labeled it as a "Unclean shut-down" meaning, I can't access my windows partition  from this ubuntu liveCD.So, I can't reinstall Grub to my system, this leaving me on this LiveCD stuck. I have tried to reinstall, but the only option (Seeing as I merged my partitions is to install over windows) and I really don't want that, please if anyone knows a way to force access, please help.


Edit: I got the error: Error 17: Cannot Mount selected partition.

---

### Post by meierfra. on 2009-03-20
"root (hd0,0)" only works if ubuntu is the first partition in on the first hard disk. 

Try this (in a terminal in the LiveCD):

```
sudo grub 
```

and at the "grub>" prompt.

```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd0,4)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2')

Still at the "grub>" prompt:

```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")

Reboot. If you have more than one hard drive, make sure that the  bios are set to boot from the Ubuntu drive.

---

