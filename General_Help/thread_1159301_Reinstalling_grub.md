---
title: "Reinstalling grub"
date: 2009-05-14
forum: General Help
---

### Post by WSCCGreg on 2009-05-14
I dual boot my laptop with windows and Ubuntu. The list of old versions of grub was getting lengthy so I decided to delete some older ones (which I've done before) but ended up deleting them all. Any suggestions for putting reinstalling without do a fresh install of Ubuntu?

Greg

---

### Post by Locutus_of_Borg on 2009-05-14
what is the output of the following commands
become root first:
```
sudo -i
```
then
```
mount
```
```
fdisk -l
```
```
ls -R /boot
```

---

### Post by WSCCGreg on 2009-05-14
When starting the computer I get the message:
[INDENT]Grub loading stage 1.5[/INDENT]

Then I get the following options:
[INDENT]Ubunto 8.10 memtest86+[/INDENT]
[INDENT]Windows[/INDENT]

I am unable to load Ubuntu

---

### Post by whoop on 2009-05-14
> **WSCCGreg said:**
> When starting the computer I get the message:
[INDENT]Grub loading stage 1.5[/INDENT]

Then I get the following options:
[INDENT]Ubunto 8.10 memtest86+[/INDENT]
[INDENT]Windows[/INDENT]

I am unable to load Ubuntu
Oh, wait, you removed all your kernels (is that even possible, can't imagine)? Or did you just remove them from menu.lst? In that case update-grub should work. Or you could manually add a kernel entry in menu.lst, boot from that kernel and run update-grub from there.
In any case, you'll need a live-cd...

this is the basic setup
```

title           Ubuntu 9.04, kernel 2.6.28-11-generic
root            (hdx,x)
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=xxxxx ro
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

```
You can get your UUID by typing
```

sudo blkid

```

---

### Post by WSCCGreg on 2009-05-14
It's sounding like I need to reinstall.

I did a search of grub files comparing it to the list on another computer. I am missing these files:

/usr/sbin
     grub-mkdevicemap
     grub-probe

/usr/share/doc/grub-common
     AUTHORS
     changelog.Debian.gz
     copyright
     NEWS.gz
     README
     THANKS
     TODO

/usr/share/recovery-mode/options
     grub
     netroot

/var/cache/apt/archives
     grub_0.97-29ubuntu53_i386.deb

/var/lib/dpkg/info
     grub-common.list
     grub-common.md5sums

I haven't been able to copy them onto my computer. Perhaps it wouldn't even help.

---

### Post by whoop on 2009-05-14
> **WSCCGreg said:**
> It's sounding like I need to reinstall.

I did a search of grub files comparing it to the list on another computer. I am missing these files:

/usr/sbin
     grub-mkdevicemap
     grub-probe

/usr/share/doc/grub-common
     AUTHORS
     changelog.Debian.gz
     copyright
     NEWS.gz
     README
     THANKS
     TODO

/usr/share/recovery-mode/options
     grub
     netroot

/var/cache/apt/archives
     grub_0.97-29ubuntu53_i386.deb

/var/lib/dpkg/info
     grub-common.list
     grub-common.md5sums

I haven't been able to copy them onto my computer. Perhaps it wouldn't even help.

Nah, never do a reinstall :p. Especially if you don't have to.
Allthough I am not entirely sure what you have done, there should be a way out of this.
Let's say, worst case scenario, your grub is completely borked. Then try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

