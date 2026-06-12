---
title: "easy-way to delete old kernel images?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by abiezerm on 2008-06-04
hi every one.

there r a easy-way to delete old kernel images?
graphical at least?

greetings

---

### Post by overdrank on 2008-06-04
> **abiezerm said:**
> hi every one.

there r a easy-way to delete old kernel images?
graphical at least?

greetings

Hi and you can comment them out  of the list with #
```
gksu gedit /boot/grub/menu.lst
```
Example: highlighted in red
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3d5a2444-f3f4-4b04-a683-d56e170d8792 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

[COLOR="Red"]#[/COLOR]title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
```

---

### Post by VMC on 2008-06-04
You can remove the old ones from Synaptic. Look up '386'.

This question keeps coming up for some reason. They don't hurt and maybe come up useful if you ever get an error. I would wait a while before removing all your old kernels

---

### Post by kaboodle_fish on 2008-06-04
If you do choose to remove via Synaptic make sure you check and double check to be 100% positive about what you are removing and do a complete uninstall

---

### Post by overdrank on 2008-06-04
Also I would suggest leaving the recovery mode in case the new kernel has some errors and does not boot in the future.

---

### Post by abiezerm on 2008-06-04
ya, i would like leave the actual kernel one old version..

but 10 old kernels is to much.. and much space too im laptop user..


thanks a lot guys

---

### Post by abiezerm on 2008-06-04
via synaptic package manager works just fine :)

---

### Post by warp99 on 2008-06-04
The easiest way for me is using the command line with apt-get like so:

```
sudo apt-get remove linux-image-<insert_kernel_version>
```

This will delete the image, restricted drivers, and Ubuntu modules for that kernel version. Then running a 'sudo apt-get autoremove' afterwards will remove any header files that you my have installed for that kernel version. If you want to make a test run before your actually delete the older images use the '-s' parameter:

```
sudo apt-get -s remove linux-image-<insert_kernel_version>
```

That way you know exactly what is going to get deleted before you commit.

---

### Post by gaffurabi on 2008-06-04
> **warp99 said:**
> The easiest way for me is using the command line with apt-get like so:

```
sudo apt-get remove linux-image-<insert_kernel_version>
```

This will delete the image, restricted drivers, and Ubuntu modules for that kernel version. Then running a 'sudo apt-get autoremove' afterwards will remove any header files that you my have installed for that kernel version. If you want to make a test run before your actually delete the older images use the '-s' parameter:

```
sudo apt-get -s remove linux-image-<insert_kernel_version>
```

That way you know exactly what is going to get deleted before you commit.

how long does it take to remove an older kernel version?
i entered *sudo apt-get remove linux-image-2.6.24-16* and it has been over 5 minutes

---

### Post by snl2587 on 2008-06-06
It shouldn't take long at all...less than 1 minute to remove 3 kernels on my computer as well as the headers and dependancies.

---

### Post by warp99 on 2008-06-30
> **gaffurabi said:**
> how long does it take to remove an older kernel version?
i entered *sudo apt-get remove linux-image-2.6.24-16* and it has been over 5 minutes

You forgot to add the generic on the end so the command string should look like this:

```
sudo apt-get remove linux-image-2.16.24-16-generic
```

Sorry for the late reply. I've been rather busy with a home improvement project. ](*,)

---

### Post by Saorex on 2010-08-05
> **warp99 said:**
> 
```
sudo apt-get remove linux-image-2.16.24-16-generic
```

I wasn't aware of this command and it proves to be very useful. I also like to keep only two kernel versions at the same time.

---

### Post by Ginsu543 on 2010-08-06
Yeah, I usually use Synaptic to do this. To remove a particular kernel, you have to remove three (3) associated files:

1) linux-headers-2.6.XX-XX
2) linux-headers-2.6.XX-XX-generic
3) linux-image-2.6.XX-XX-generic

You can find them in Synaptic if you type "kernel" in the Quick search prompt.

---

