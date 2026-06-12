---
title: "~/ In Conky"
date: 2010-09-28
forum: Desktop Environments
---

### Post by Mr_VeRiTy on 2010-09-28
Hi, I'm trying to edit my conky theme, so that if I share it with people, it will correctly show how much free space is in their home partition, So I tried ```
${fs_free ~/}
``` But It doesn't work, Is there another way to do this? 'Cos I can't just leave it as ```
${fs_free /home/luke}
``` 'Cos unless their name is Luke it wont work.

I could just use ```
${fs_free /home/}
``` But I also have a bar showing how much space is used in the home partition, and if I just use ```
${fs_used /home/}
``` Then it wont be accurate if there is more than one user on the computer.

---

### Post by Tibuda on 2010-09-28
Can you post the contents of /etc/fstab?

---

### Post by Mr_VeRiTy on 2010-09-28
> **Tibuda said:**
> Can you post the contents of /etc/fstab?
I couldn't find a folder named fstab in etc.
EDIT: OH its a file, embarrassing, the contents of is 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c0b0bc91-0ada-4651-a71d-96ef363d7da0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ee78cc1c-1995-4075-8f15-b4f74a09a124 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=54d0c7a2-50f6-4862-9173-4041ed5197bc none            swap    sw              0       0
```

---

### Post by MooseDog on 2010-09-29
i use this to display /home stats:

    ```
     Available${alignr}${fs_size /home}
     Free${alignr}${fs_free /home}
     Percent Free${alignr}${fs_free_perc /home}%
```

---

### Post by Tibuda on 2010-09-29
That's it. Only /home is on a separate partition, /home/$USER is not.

You can use **${exec du -s ~}** to display the total size of any folder.

---

### Post by Mr_VeRiTy on 2010-09-29
> **Tibuda said:**
> That's it. Only /home is on a separate partition, /home/$USER is not.

You can use **${exec du -s ~}** to display the total size of any folder.
So would ```
]${exec du -s ~}
``` show the used space of /home/$user regardless of what the username is?

---

### Post by Tibuda on 2010-09-29
> **Mr_VeRiTy said:**
> So would ```
]${exec du -s ~}
``` show the used space of /home/$user regardless of what the username is?

yes. try running **du -s ~** in a terminal. see also **man du** for more info on du.

---

### Post by Mr_VeRiTy on 2010-09-29
> **Tibuda said:**
> yes. try running **du -s ~** in a terminal. see also **man du** for more info on du.

It works, but is there any way I can get it to output in Gigabytes instead of megabytes?

---

### Post by Tibuda on 2010-09-29
> **Mr_VeRiTy said:**
> It works, but is there any way I can get it to output in Gigabytes instead of megabytes?

Yes! Use the -B argument.
```
du -s -B G ~
```

---

### Post by Mr_VeRiTy on 2010-09-29
> **Tibuda said:**
> Yes! Use the -B argument.
```
du -s -B G ~
```

Thanks :)

---

### Post by Tibuda on 2010-09-29
You are welcome! :)

---

