---
title: "dual booting with Vista/"
date: 2006-08-06
forum: Desktop Environments
---

### Post by beckyh on 2006-08-06
Has anyone managed to dual boot Vista and Dapper?

I have a problem which I do not know how to fix.  Please bear in mind currently I have no Ubuntu install on my machine and I am researching this with a view to installing it again.  

Right, the situation is XP is installed first and is my main OS. Second I put on Vista and it dual boots fine.

When I go to install Ubuntu 6, it installs fine but GRUB somehow messes with my Vista boot and I am not able to boot into Vista anymore (gives an error about missing winload.exe)

Several times I try this, and each time I get the same corrupted boot.  I know it is possible to boot Vista and Ubuntu as I have seen people who have done it.  

I am sure this is a grub issue but I cannot seem to install Ubuntu 6 without grub - it now does it automatically.  

Can anyone please help?

---

### Post by seshomaru samma on 2006-08-12
Hi
I'm dual booting Vista and Dapper
You need to edit your grub menu
```
sudo geit /boot/grub/menu.lst
```
add this at the bottom
```
title vista 
rootnoverify (hd0,2) 
chainloader +1
```
I have Vista installed first (physically) on my harddisk , though Dapper is chronologicaly earlier. If you have two hard disks or has a slightly different setting you might need to modify the second line ( "rootnoverify (hd0.2)") 
It seems that every once in a while this entry disppears from Grub , probably due to some updates or something, so you will need to fix it everytime.
Good luck

---

### Post by Ramses de Norre on 2006-08-12
> **seshomaru samma said:**
> It seems that every once in a while this entry disppears from Grub , probably due to some updates or something, so you will need to fix it everytime.

This shouldn't happen if you put the lines below 
```
### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by seshomaru samma on 2006-08-12
Thanks
I'll try that...

---

