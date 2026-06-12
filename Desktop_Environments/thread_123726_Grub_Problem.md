---
title: "Grub Problem"
date: 2006-01-30
forum: Desktop Environments
---

### Post by shade11 on 2006-01-30
I successfully formatted my Windows partition and copied all my Linux files into it on Gparted via Live disk. So far so good. My friends are all ticked off at me becuase they dis-like Linux (But they never tired it out yet.) Well so far so good I successfully converted into a full Linux user in about 3 Months. One problem is with GRUB. After copying all my kernaels are not shown instead there are the old ones and I still have the old partition which is weird. My friend Ben Plaut tried to fix it but we couldn't do anything.

---

### Post by duff on 2006-01-30
Did you update your /boot/grub/menu.lst with your new kernels?

---

### Post by Tichondrius on 2006-01-30
```
sudo grub-update
```

---

### Post by shade11 on 2006-02-01
Nothing works!!! Please help.

---

### Post by Tichondrius on 2006-02-01
sorry it should be

```
sudo update-grub
```

---

### Post by shade11 on 2006-02-13
Ah, forget it . I got it to work perfectly after re-installing Ubuntu. Even with a shiny new jfs partition format.

---

