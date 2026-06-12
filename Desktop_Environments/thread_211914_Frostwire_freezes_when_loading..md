---
title: "Frostwire freezes when loading."
date: 2006-07-09
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-09
Hello!

I'm having trouble starting Frostwire.  I have used it once with no problems since installing it, but now my system freezes when it starts to load.

I have not installed anything else since frostwire.

Any Ideas?

Thanks!

---

### Post by empthollow on 2006-07-13
i've just run into this problem, i don't know why it does that but in my case , it was the kernel "linux-image-2.6.15-26-386".  when i booted with "linux-image-2.6.15-25-386". i was able to run frostwire again no problem.  hope this helps.

---

### Post by randell6564 on 2006-07-13
> **empthollow said:**
> i've just run into this problem, i don't know why it does that but in my case , it was the kernel "linux-image-2.6.15-26-386".  when i booted with "linux-image-2.6.15-25-386". i was able to run frostwire again no problem.  hope this helps.


Thanks!  But I've since installed the limewire rpm and no problems!

I actually paid for limewire pro a long time ago but up until recently could not install it cuz i could not find any help page regarding limewire pro, only limewire free.

I finally figured out how to install the rpm so now i gots my pro!

Lets see... is kernel image 2.6.15-26-386 the most current update?  If it is then I just updated today so that would be the kernel that i now have.

---

### Post by amunimanghi on 2006-07-15
How do you boot into 2.6.15-25-386? I have 2.6.15-26-386 and its causing some of my programs to crash the entire computer.

---

### Post by randell6564 on 2006-07-15
> **amunimanghi said:**
> How do you boot into 2.6.15-25-386? I have 2.6.15-26-386 and its causing some of my programs to crash the entire computer.

I show kernel 25 for recovery mode at my boot menu.  The rest are all kernel 26.

Not sure how you roll back your kernel.

---

### Post by amunimanghi on 2006-07-15
What do you mean when you say boot menu? When I start my computer, it just goes straight to the login menu. I've never really seen a boot menu. =-=

---

### Post by Perfect Storm on 2006-07-15
The countdown after bios load. Hit <esc>

---

### Post by randell6564 on 2006-07-15
> **amunimanghi said:**
> What do you mean when you say boot menu?

restart your system, its the screen that you see that gives you boot options.

In my case, I dual boot Windoze XP with Ubuntu, so I have the option to boot to xp or ubuntu.

---

### Post by amunimanghi on 2006-07-15
> In my case, I dual boot Windoze XP with Ubuntu, so I have the option to boot to xp or ubuntu. Oh, I'm not dual booting. 
@ Artificial Intelegance: Do I press "Esc" where it shows primary and secondary, and checks for that. It looks like text. I don't what thats called.

---

### Post by Perfect Storm on 2006-07-15
There should be a count down 3-2-1. Just hit <esc> while it's counting down.

---

### Post by amunimanghi on 2006-07-15
Ok, I'll reboot and try it out.

---

### Post by amunimanghi on 2006-07-15
Ok, I booted into 2.6.15-25-386 successfully. Is it possible to make this the default until 2.6.15-26-386 gets stable?

---

### Post by empthollow on 2006-07-15
do this

```
sudo gedit /boot/grub/menu.lst
```

look for a line that says 
```
default=0
```
and change the "0"  to whatever number that kernel is (just count the number of entries starting with 0)

example 
```
default=3
```

then reboot and see what happens

---

### Post by amunimanghi on 2006-07-15
```


title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

``` 

So in this case, would it be 3?

---

### Post by empthollow on 2006-07-15
it looks like the number would actually be 2, but the kernel you want to use has a "savedefault" option. that means if you default line is
```
default=saved
```
then you shouldn't have to do anything.  if the entry contains "savedefault" grub will remember which kerenl you last used and make it the default automatically. :D

---

### Post by amunimanghi on 2006-07-15
Wow thats easy. If I wanted the one that was released the other day, do I just set it back to 0?

---

### Post by empthollow on 2006-07-16
yep, that's it.

---

