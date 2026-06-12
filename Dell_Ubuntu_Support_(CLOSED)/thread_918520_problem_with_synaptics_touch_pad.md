---
title: "problem with synaptics touch pad"
date: 2008-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by parvathy on 2008-09-13
hi all,

i have a dell xps m1530 system . i have ubuntu (64 bit) installed. now i'm facing a problem with the touch pad.


i made the following changes but it is working. may for one boot, it will work,and during the next boot everything goes wrong.

i made the following change in the xorg.conf


Option "SHMConfig" "on"

and after logging out i restarted thexserver by ctrl+alt+backspace



 i tried to run synclient -l

 then it shows an error that shm is not enabled.


can anybody please suggest any thing to be done for my touch pad to work!!!!

---

### Post by zansatsu0 on 2008-09-15
:mrgreen:This problem has been covered several times. Be sure to exhaust the 'Search' feature. You will find it. :mrgreen:

I had the same problem and I found the below pages in the forum. You will have to edit your '/boot/grub/menu.lst' file with:
```
sudo gedit /boot/grub/menu.lst
```

To add:
```
i8042.nomux=1
```

To the end of the 'kernel' line to look like:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=446ea0c-57b1-4112-939c-3f1d74be9f5f ro quiet splash [COLOR="Red"]i8042.nomux=1[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic quiet
```

EDIT: Don't forget to reboot... That's kinda important.

Check these posts for more details:
[http://ubuntuforums.org/showthread.php?t=763043]("http://ubuntuforums.org/showthread.php?t=763043")
[http://ubuntuforums.org/showthread.php?t=737060]("http://ubuntuforums.org/showthread.php?t=737060")

Good luck.

---

