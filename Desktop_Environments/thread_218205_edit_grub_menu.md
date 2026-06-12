---
title: "edit grub menu"
date: 2006-07-18
forum: Desktop Environments
---

### Post by zigoto on 2006-07-18
Hi, with the updates of dapper, my grub menu a now 3 diferents kernels, i only use the last one, can some one tell me how to put only one option.

Regards!

---

### Post by Malac on 2006-07-18
You can either uninstall the other images in synaptic.
look for linux-image-2.16.25-[SIZE=1][I]something-or-other.

[/I][SIZE=2]Or just run 
```
sudo gedit /boot/grub/menu.lst
```
and comment out the entries you don't want.
They will look something like this.

[/SIZE][/SIZE]```

title        Ubuntu, kernel 2.6.15-26-686
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-686
boot

```
comment them out like this.

```

#title        Ubuntu, kernel 2.6.15-26-686
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
#initrd        /boot/initrd.img-2.6.15-26-686
#boot

```
 Hope this helps.

---

### Post by zigoto on 2006-07-18
Hi. It works...
thanks!

---

### Post by wangbin on 2006-07-18
I am curious if you don't uninstall the old kernel, when next time you upgrade to a newer kernel, will the auto generated menu show the older ones again?

---

### Post by aysiu on 2006-07-18
> **wangbin said:**
> I am curious if you don't uninstall the old kernel, when next time you upgrade to a newer kernel, will the auto generated menu show the older ones again?
Yes, but it will default to booting the newest kernel.

---

### Post by VirtuAlex on 2006-07-18
> **wangbin said:**
> I am curious if you don't uninstall the old kernel, when next time you upgrade to a newer kernel, will the auto generated menu show the older ones again?
It should.

---

### Post by Malac on 2006-07-19
If you uninstall the old kernels it will not show them the next time you upgrade to a newer kernel just your last one will show until you uninstall that one.

If you comment out the entries instead of uninstalling them then, when it next rescans after a new kernel install, GRUB will leave these commented ones commented thus not showing them at boot time.
That is why it is better to comment them out than just delete the entries as GRUB will put them back after a new kernel install.

However unless you have a particular need to keep an old kernel(i.e. a particular device only works with that kernel, or as a backup kernel in case anything goes wrong with the current one) I would always (IMHO :)) uninstall old kernels as they are just wasted space.

Hope this helps.

---

### Post by ellion on 2006-07-19
I always uninstall old kernels, they're just wasted space, nevertheless I keep 2 kernels. Even if it's unlikely to happen, I then have one older kernel if the new one's corrupted.

---

### Post by greeneemer on 2006-07-22
This thread answers your question. It just solved the same problem for me:
[http://www.ubuntuforums.org/showthread.php?t=220160](http://www.ubuntuforums.org/showthread.php?t=220160)

---

