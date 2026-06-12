---
title: "upgrade to 19.10 kde or XFCE will not boot?"
date: 2019-11-03
forum: Desktop Environments
---

### Post by LMH1 on 2019-11-03
How to fix KDE\XFCE because when i use startX Gnome start.

But did i use [B]startkde its did not works i get no screen found but if it startx and then startkde i get it to boot.

But its look like its some issue with grapics.[/B]

How to fix?

---

### Post by #&amp;thj^% on 2019-11-03
> **LMH1 said:**
> 
But its look like its some issue with grapics.[/B]

How to fix?
Nope it's a user issue ;)
To determine the client to run, startx first looks for a file called ".xinitrc" in the user's home directory. If that is not found, it uses the file "xinitrc" in the "xinit" library directory.
On the other hand, if you want to choose a GUI (LXDE, XFCE4, KDE, etc), then xdm and look-alikes such as kdm, gdm or LightDM are used for selecting different desktop types.
If you want to try out other environments as a one-off, you can specify a different program to run on the command line of startx itself. The startx program has a quirk: you need to use the full path to the program.
```

startx /usr/bin/startkde
```

---

### Post by LMH1 on 2019-11-03
I also get issue with ubuntu, with linux 5.3.0-19 generic kernel its just give black screen with _ so its did not works.

I need to boot linux 5.1.0-05100 generic to get ubuntu to works?

Thanx for help.

---

### Post by #&amp;thj^% on 2019-11-03
> **LMH1 said:**
>  _ so its did not works.

Thanx for help.
EDIT: This is said with a Kind Tone.
Every time I see just "**so its did not works**" or "**it did not work**" I have now decided to end my efforts  to help.
I'm not here to pull teeth, I'm here to help users that will supply useful information to help them with. :)
I'm old, grumpy, and persnickety about having my operating system just so.

---

### Post by LMH1 on 2019-11-09
Ubuntu, with Linux 5.1.0-050100-generic

> 
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  ce175d2d-f51e-41b2-a88f-0adb7680b419
    else
      search --no-floppy --fs-uuid --set=root ce175d2d-f51e-41b2-a88f-0adb7680b419
    fi
    echo    'Loading Linux 5.1.0-050100-generic ...'
    linux    /boot/vmlinuz-5.1.0-050100-generic root=UUID=ce175d2d-f51e-41b2-a88f-0adb7680b419 ro  quiet splash $vt_handoff
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-5.1.0-050100-generic



can you find a issue here why kernel 5.1 did not boot but 5.0 boot:
Ubuntu, with Linux 5.0.0-32-generic
> 
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  ce175d2d-f51e-41b2-a88f-0adb7680b419
    else
      search --no-floppy --fs-uuid --set=root ce175d2d-f51e-41b2-a88f-0adb7680b419
    fi
    echo    'Loading Linux 5.0.0-32-generic ...'
    linux    /boot/vmlinuz-5.0.0-32-generic root=UUID=ce175d2d-f51e-41b2-a88f-0adb7680b419 ro  quiet splash $vt_handoff
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-5.0.0-32-generic



---

### Post by ubume2 on 2019-11-13
Regarding Ubuntu 19.10 Kernel 5.3.0.-19 does not work. My system updated with a 5.3.0-22 kernel and it also does not work.  Kernel 5.0.0-32 does work.

---

### Post by LMH1 on 2019-11-16
> Processing triggers for man-db (2.8.7-3) ...
Processing triggers for gnome-icon-theme (3.12.0-3) ...
Processing triggers for shared-mime-info (1.10-1) ...
Processing triggers for menu (2.1.47ubuntu3) ...
Processing triggers for fontconfig (2.13.1-2ubuntu2) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for doc-base (0.10.9) ...
Processing 1 changed doc-base file...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.62.1-1) ...
Processing triggers for libglib2.0-0:amd64 (2.62.1-1) ...
Processing triggers for libc-bin (2.30-0ubuntu2) ...
Setter opp nautilus-extension-gnome-terminal (3.34.2-1ubuntu1) ...
Processing triggers for initramfs-tools (0.133ubuntu10) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-19-generic
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...



can someone tell why ubuntu have so poor pack manager?
should it works after a updated (disto-updates) to get new packmanager set up without do anything after?

---

