---
title: "Passing boot paramaters!"
date: 2005-07-28
forum: Desktop Environments
---

### Post by leslie on 2005-07-28
How would i go about  passing "nolapic" as kernel parameter at boot?

---

### Post by Xian on 2005-07-28
You just need to edit your /boot/grub/menu.lst file
Find the section that looks similar to this
```
title		Ubuntu, kernel 2.6.10-5-k7 
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda8 ro quiet 
initrd		/boot/initrd.img-2.6.10-5-k7
```
Now, just add the desired entry.
The kernel line should now appear as below.

Do not match the example precisely!
Only add in the nolapic entry to your setup.
```
kernel		/boot/vmlinuz-2.6.10-5-k7 root=/dev/hda8 ro quiet nolapic 
```
You can also add it temporarily at the grub menu by using the 'e' key.
Then just select the kernel line and add the nolapci parameter.
This will only affect that particular boot session.

---

### Post by leslie on 2005-07-29
Thanks a bundle not solved my problem it is nice to know!

---

