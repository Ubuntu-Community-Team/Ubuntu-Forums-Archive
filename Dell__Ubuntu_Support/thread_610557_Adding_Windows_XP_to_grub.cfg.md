---
title: "Adding Windows XP to grub.cfg"
date: 2007-11-12
forum: Dell  Ubuntu Support
---

### Post by Stryker250 on 2007-11-12
I have searched the forums and none of what I have found helped.
All the posts refer to editing the menu.lst file. Yet the grub installation I am using uses the grub.cfg file. 

I am not sure how to add a Windows installation in that file. But it exists in the menu.lst file.

Is there some way I can get grub to use the menu.lst file or can someone help me with adding the Windows installation to the grub.cfg file.

Partitions are as follows.

sda1 -> Windows
sda2 -> /boot
sda3 -> swap
sda4 -> /

Thanks in advance.

---

### Post by Stryker250 on 2007-11-12
I was able to solve the problem.

It was as easy as adding the following to the grub.cfg file

```


menuentry "Windows XP Pro" {
      set root=(hd0,1)
      chainloader +1
}

```

And that did the job.

---

