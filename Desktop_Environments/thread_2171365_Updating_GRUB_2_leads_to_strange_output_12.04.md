---
title: "Updating GRUB 2 leads to strange output 12.04"
date: 2013-08-30
forum: Desktop Environments
---

### Post by elpiel93 on 2013-08-30
```
sudo update-grub2

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.9.11-030911-generic
Found initrd image: /boot/initrd.img-3.9.11-030911-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found Windows 8 (loader) on /dev/sdb4
Found linux image: /boot/vmlinuz-3.9.11-030911-generic
Found initrd image: /boot/initrd.img-3.9.11-030911-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-37-generic
Found initrd image: /boot/initrd.img-3.5.0-37-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sdb4
done
```

I've only moved Windows 8 right after Ubuntu 12.04 - 3.9 and that's the output of the update, but on boot every thing's OK?!

---

### Post by VMC on 2013-08-30
There's nothing strange about the output. Its just identifying your images, both Linux and Windows.
The topic says updating grub2. Did you just update grub or update in general.

edit: usually anything touching grub and/or kernels, the grub will be updated. *grub.cfg* may have been re-created, but the user scripts will be unchanged, so you wouldn't notice anything different on re-boot.

---

### Post by elpiel93 on 2013-08-30
I sudo update-grub2, but why does it prints 2 times the images? This is my question?

---

### Post by oldfred on 2013-08-30
You may have double scripts? If you manually edited or renamed a script in /etc/grub.d and grub did a major update where it rewrote new scripts you may have duplicate script?

post this:
ls -l /etc/grub.d

Do you have multiple installs of Ubuntu? There was a bug in some versions where it would pick up all the installs in the other install which go very confusing.

You also may want to houseclean some of the old kernels. I like to keep at least two - current & one older just in case.
       
Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by elpiel93 on 2013-08-30
ls -l /etc/grub.d:

```
-rwxr-xr-x 1 root root 6743 Jan 22  2013 00_header
-rwxr-xr-x 1 root root 5522 Jan 22  2013 05_debian_theme
-rwxr-xr-x 1 root root 1010 Aug 28 11:13 10_linux_proxy
-rwxr-xr-x 1 root root  188 Aug 28 11:13 11_os-prober_proxy
-rwxr-xr-x 1 root root 1010 Aug 28 11:13 13_linux_proxy
-rwxr-xr-x 1 root root 6335 Jan 22  2013 14_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 15_memtest86+
-rwxr-xr-x 1 root root  188 Aug 28 11:13 16_os-prober_proxy
-rwxr-xr-x 1 root root 1388 Jan 22  2013 17_uefi-firmware
-rwxr-xr-x 1 root root  214 Jan 22  2013 18_custom
-rwxr-xr-x 1 root root   95 Jan 22  2013 19_custom
drwxr-xr-x 2 root root 4096 Aug 28 11:12 bin
drwxr-xr-x 2 root root 4096 Aug 28 11:13 proxifiedScripts
-rw-r--r-- 1 root root  483 Jan 22  2013 README
```

uname -a
Linux elpiel-magnum-ubuntu 3.9.11-030911-generic #201307202035 SMP Sun Jul 21 00:35:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I've deleted the old ones exept 1, but it still repeats it self:

```
Generating grub.cfg ...
[COLOR=#ff0000]Found linux image: /boot/vmlinuz-3.9.11-030911-generic
Found initrd image: /boot/initrd.img-3.9.11-030911-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found Windows 8 (loader) on /dev/sdb4[/COLOR]
[COLOR=#008000]Found linux image: /boot/vmlinuz-3.9.11-030911-generic
Found initrd image: /boot/initrd.img-3.9.11-030911-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sdb4[/COLOR]
done
```

The update-grub2 Repeats his output and That's what I want to fix, but after these changes still appears!

---

### Post by oldfred on 2013-08-30
It looks like you used Grub Customizer. But I do not know exact what it does in creating its versions to customize your grub.

But I see two os-prober proxy file with executeable bit on.
And both 18 & 19 custom.

---

### Post by grahammechanical on 2013-08-31
I have found that when I use gksudo gedit to edit system configuration files that Gedit will make a backup copy of the script. The backup will have the same name but a tilde ( ~ ) character will have been added. This tilde character will make the backup a hidden file but the file will still be read by the system. So that, in effect, there are two versions of the system file and both are active and are being read.

Regards.

---

