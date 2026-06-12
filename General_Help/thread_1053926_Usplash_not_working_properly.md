---
title: "Usplash not working properly"
date: 2009-01-29
forum: General Help
---

### Post by 09buntu on 2009-01-29
Hi

About 4 times out of 5 when I boot my Ubuntu there is no boot splash (usplash) just scrolling text.

There's also no errors just OK messages.

If I do a presentation of something where booting into my Ubuntu laptop and it starts to spit out text all over the place people are not going to be impressed by Ubuntu.

Thanks

---

### Post by caljohnsmith on 2009-01-29
How about posting the output of:
```

free
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
apt-cache policy usplash
```
That might give some clues what is causing your startup splash screen problem.

---

### Post by 09buntu on 2009-01-29
> **caljohnsmith said:**
> How about posting the output of:
Sure no problem, here's the outputs...
> **caljohnsmith said:**
> ```
free
```
```
oops...
```
> **caljohnsmith said:**
> ```
sudo fdisk -lu
```
```

oops...
```
> **caljohnsmith said:**
> ```
sudo blkid -c /dev/null
```
```

oops...
```
> **caljohnsmith said:**
> ```
cat /etc/fstab
```
```

oops...
```
> **caljohnsmith said:**
> ```
cat /etc/initramfs-tools/conf.d/resume
```
```
oops...
```
> **caljohnsmith said:**
> ```
apt-cache policy usplash
```
```
oops...
```
> **caljohnsmith said:**
> That might give some clues what is causing your startup splash screen problem.
Thanks I hope so, haven't had any other problems with this setup =)

---

### Post by caljohnsmith on 2009-01-29
Interesting, so you have an encrypted swap partition? I think that might be part of the issue, because I'm guessing there is a timing issue with when the encrypted swap partition becomes available to mount. In other words, 4 out of 5 times (as you say) maybe the LVM software you are using hasn't fully loaded when fstab gets executed and tries to mount the swap partition. How about trying this experiment:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end of the kernel line for whichever Ubuntu entry you normally use to boot, add a "rootdelay" like:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root            (hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Blue"]rootdelay=120[/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```
Then reboot, and let me know if that changes anything or not.

---

### Post by dcstar on 2009-01-29
> **09buntu said:**
> Hi

About 4 times out of 5 when I boot my Ubuntu there is no boot splash (usplash) just scrolling text.
........
Try:

```
sudo update-initramfs -k all -u
```

---

### Post by 09buntu on 2009-01-30
> **caljohnsmith said:**
> Interesting, so you have an encrypted swap partition? I think that might be part of the issue, because I'm guessing there is a timing issue with when the encrypted swap partition becomes available to mount. In other words, 4 out of 5 times (as you say) maybe the LVM software you are using hasn't fully loaded when fstab gets executed and tries to mount the swap partition. How about trying this experiment:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end of the kernel line for whichever Ubuntu entry you normally use to boot, add a "rootdelay" like:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
root            (hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Blue"]rootdelay=120[/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```
Then reboot, and let me know if that changes anything or not.

Thanks for your help. I think you may be right. That didn't change anything though. Disabling swap in fstab didn't change anything either.

---

### Post by 09buntu on 2009-01-30
> **dcstar said:**
> Try:

```
sudo update-initramfs -k all -u
```

Thanks for your help. It didn't change anything though. Here's the output.
```
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
cryptsetup: WARNING: target lvm-swap_crypt has a random key, skipped
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
cryptsetup: WARNING: target lvm-swap_crypt has a random key, skipped
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
cryptsetup: WARNING: target lvm-swap_crypt has a random key, skipped

```

---

### Post by srpayo on 2009-06-11
Hi,

I'm not sure if this will help you but if you still have the problem or if someone else comes across this post you could try the following in the terminal:

First make sure you have StartUp-Manager installed:

sudo apt-get install startupmanager

Then type:

sudo apt-get install usplash*

This should install usplash and many usplash themes, I had lots of problems with my fingerprint-usplash and this solved the issue once and for all.

If you still do not have luck make sure that in StartUp Manager your settings are 1024x768 and 16bit color.

Also check that the screen resolution settings are the same on:

/etc/usplash.conf

To check you need to become root and then type: less /etc/usplash.conf
To edit the file type: gedit /etc/usplash.conf

Hope this helps.

---

### Post by cobb_cruiser on 2010-03-23
I had the same problem when on Jaunty (9.04).  I upgraded to Karmic (9.10) yesterday and now I get what reminds me of a TV channel that is not in service although a bit different (several colors on four corners with various numbers in the middle).  

It looks strange.  Hopefully someone can help.

---

