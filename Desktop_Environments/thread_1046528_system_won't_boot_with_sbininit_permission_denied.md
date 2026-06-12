---
title: "system won't boot with /sbin/init: permission denied"
date: 2009-01-21
forum: Desktop Environments
---

### Post by ranskalex on 2009-01-21
Hi all,

I am getting a run-init: /sbin/init: permission denied then a Kernel panic - not syncing: Attempt to kill init!

Some days ago I tried to start my pc but it got stuck right before the kernel boot (at least that's what I understood with my very limited knowledge). The previous shut down appeared clean to me but maybe it wasn't. I have not been able to boot my instal since then. I have tried all the options from the Grub list, including previous kernels but it just keeps on doing the same thing.

I executed an e2fsk from the live cd and it did not return any error.
I have managed to mount my ext3 partition and access it with no problem. From there, I have enabled the boot logs but when checking after the next boot failure, the /var/log/boot file was still empty.

I am using Ubuntu Intrepid.

I took a pic of the screen as I didn't know where to find the log.
[http://share.ovi.com/media/ranskalex.public/ranskalex.10285]("http://share.ovi.com/media/ranskalex.public/ranskalex.10285")

I would like to avoid re-installing my system. That's the reason for that post.

Any help would be really appreciated.

---

### Post by snova on 2009-01-21
Well, since you've got a Live CD around, boot it up, mount the partition, and find out what permissions are on /sbin/init.

Maybe the permissions got messed up somehow... is it executable?

---

### Post by ranskalex on 2009-01-22
I have checked the permission and it's executable
-rwxr-xr-x 1 root root   104364 2008-09-29 23:52 init

If the init doesn't execute, what could be the reason for that ?

Thanks.

---

### Post by mgol on 2009-01-22
Post Your /boot/grub/menu.lst file, this can be an error with boot parameters. Here is my corresponding section:
```

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
uuid		50e22019-8cc3-4a8e-9be0-b141c55d1d73
kernel		/vmlinuz-2.6.24-23-generic root=UUID=4261b8a7-0da1-415e-8657-ff09d053c398 ro vga=798
initrd		/initrd.img-2.6.24-23-generic
quiet

```

---

### Post by ranskalex on 2009-01-25
ok so in my grub list I have:

```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro quiet splash
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro  single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet
```

And the hd0,5 is the correct partition the UUID points to it.

Thanks.

---

### Post by mgol on 2009-01-25
Have You tried to choose one of older kernels in GRUB menu?

You can also try adding "enforcing=0" *OR* "selinux=0" (without quotation marks) and boot with that option.

It's not necessary to manually edit menu.lst file each time (there's a lot of work to change it via LiveCD). Just wait for the GRUB menu and then press 'e' - after that, You'll be able to edit all those menu.lst lines. It will work *JUST FOR ONE BOOT* - if it fixes the problem, You can change it permanently in running system, in menu.lst.

---

### Post by ranskalex on 2009-01-26
Thanks. (I am at work right now so I'll check that tonight at home).

I have tried to boot from the older Kernels and the result was the same.

---

### Post by ranskalex on 2009-01-26
So I tried:

```
title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=6aac8dfb-e6fe-4a7e-96fc-99a30dfaa992 ro  single selinux=0
initrd        /boot/initrd.img-2.6.27-9-generic
```

but it didn't work. I also tried with enforcing=0

After editing the line I pressed b to boot and it went on until I got stuch the same way as described in my first post.

---

### Post by mgol on 2009-01-26
I'm sorry, I run out of ideas... Maybe others can help.

---

### Post by ranskalex on 2009-01-27
Thanks anyway. I'll try to search some more on my side as well.

I was wondering if there could be some dependencies that would prevent the /init to be ran. Does anyone knows how to check that ?

Is there any possibility to boot bypassing the /init ?

---

### Post by mgol on 2009-01-27
> **ranskalex said:**
> Is there any possibility to boot bypassing the /init ?

No, init is the parent of all processes that don't have another parent, it generates all the processes...

---

### Post by blasko on 2009-01-28
Hi there guys,

I have a 100% similar problem. The case is worse somehow since it's a server machine with heavy e-mail traffic. And now it's stuck.

One day the services stopped workin and I started to receive permission denied messages on anything. I started fsck and then I lost control (i was in via PuTTy), next day I've checked personally and here we go I can't boot the system.

My first theory is that this an HDD hardware error. And thats all my theories.

Although I found a tip to boot with enforcing=0 and selinux=0 (you can edit a line in the grub menu by pressing 'e' and then you can boot that by pressing 'b', it works for one boot only. if you managed to boot in you should edit the grub line manually and permanently) which solved the case for a guy who used SuSe10. He got stuck immedeately in the install process. I hope it will help. I'm gonna try it and keep you posted if you are still interested. If you have already found a solution than please post it. Thanks in advance.

---

### Post by mgol on 2009-01-28
> **blasko said:**
> 
I found a tip to boot with enforcing=0 and selinux=0

He has already tried that...

---

