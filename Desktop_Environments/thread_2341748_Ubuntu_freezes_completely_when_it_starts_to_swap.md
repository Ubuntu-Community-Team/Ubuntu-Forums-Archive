---
title: "Ubuntu freezes completely when it starts to swap"
date: 2016-10-31
forum: Desktop Environments
---

### Post by ascripting on 2016-10-31
Hi.

I have a problem: My ubuntu freezes when it starts to use swap. System monitor shows that I have swap available. And when it starts to use swap then it even runs fine when it has just started to use swap. I managed to use 179.6 MiB  out of 7.9GiB before my system crashed. Expected behavior with using swap should be that system starts to run slower but in my case it just freezes completely.  Even if I waif five minutes, muse doesnt move, graphs on system monitor doesnt move, ctrl + alt + f6 doesnt work anymore. Does anyone know what's happening?

---

### Post by oldrocker99 on 2016-10-31
Welcome to the forums!

You can, of course, decrease swappiness:[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness). A swappiness of 0 means that the swap file will never be used. That doesn't exactly solve your problem of a lockup, but it will avoid it happening.

---

### Post by buzzingrobot on 2016-10-31
Is this only happening with one particular application?

---

### Post by ascripting on 2016-10-31
No, doesnt matter what application it is. Just when it starts using swap it freezes. What is strange is that usually it even writes a little bit in swap and then it freezes.

---

### Post by ascripting on 2016-11-01
I have also noticed that harddrive indicator doe not blink anymore, so I assume that it does not even try to swap anymore. However  gnome-system-monitor shows that it managed to consume around 100-200 mb of swap.

---

### Post by &amp;KyT$0P# on 2016-11-01
What are you using for swap space?  Swap file, swap partition, or...?

---

### Post by Bashing-om on 2016-11-01
ascripting; Hello;


In addition to:
> **halogen2 said:**
> What are you using for swap space?  Swap file, swap partition, or...?

It would be instructive to know more about this /swap .

What have we ?

check to see if swap is encrypted:
```

sudo blkid | grep swap
sudo dmsetup status

```

A report on the swap partition :
```

swapon -s

```

verify the UUID of the swap partition :
```

ls -l /dev/disk/by-uuid/
cat /etc/fstab

```

With these, we should have a 
[INDENT][INDENT][INDENT]point of direction
[/INDENT][/INDENT][/INDENT]

---

