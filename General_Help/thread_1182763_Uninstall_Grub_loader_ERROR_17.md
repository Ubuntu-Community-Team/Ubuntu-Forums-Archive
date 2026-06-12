---
title: "Uninstall Grub loader ERROR 17"
date: 2009-06-09
forum: General Help
---

### Post by GooseLegs on 2009-06-09
I have a serious problem. I am not a Linux user but it was installed on my girlfriends computer and we both want it removed. I did research and everything and now I am stuck. 
 
I get this message grub loading stage 1.5 error 17.
 
I know its looking for the partition but that has been deleted.
 
The bios system is very limited to what you can change. its Phoenix BIOS v3.23
 
The recovery disk is software that does not allow you to type or edit anything. The laptop is an acer with its erecovery thing.
 
I just want to use vista in peace. Please help.

---

### Post by zvacet on 2009-06-09
If I understand you correctly you can not boot Windows.If that is right then read [this.]("http://members.iinet.net.au/~herman546/p15.html#17")To make these changes in menu list you have to boot your Ubuntu live CD and go to the applicastions>accessories>terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

Then make changes from link above.

---

