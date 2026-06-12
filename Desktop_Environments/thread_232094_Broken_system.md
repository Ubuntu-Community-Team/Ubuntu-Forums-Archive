---
title: "Broken system"
date: 2006-08-08
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-08-08
Whenever I try to update the system, i get errors...

sudo apt-get upgrade gives me: E: 
```
Sub-process /usr/bin/dpkg returned an error code (1)
```

the update-manager returns error code:
```
Error: BrokenCount > 0'
```
It also says:
> It is impossible to install or remove any software. Please use the package manager or run "sudo ap-get install -f" in a terminal to fix this issue at first.
Running sudo apt-get install -f gives me(like i said):
```
Sub-process /usr/bin/dpkg returned an error code (1)
```

anyone have any ideas?

---

### Post by Ziox on 2006-08-08
> **stiankarlsen said:**
> Whenever I try to update the system, i get errors...

sudo apt-get upgrade gives me: E: 
```
Sub-process /usr/bin/dpkg returned an error code (1)
```

the update-manager returns error code:
```
Error: BrokenCount > 0'
```
It also says:

Running sudo apt-get install -f gives me(like i said):
```
Sub-process /usr/bin/dpkg returned an error code (1)
```

anyone have any ideas?

just a suggestion, try using aptitude instead of apt-get...

sudo aptitude update

sudo aptitude dist-upgrade

---

### Post by stiankarlsen on 2006-08-08
sudo aptitude dist-upgrade gives me this at the end: 
```
Generation complete.
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Errors were encountered while processing:
 linux-image-386
 firefox-gnome-support
 linux-restricted-modules-386
 linux-386
 ubuntu-desktop
server@server-laptop:~$        

```

and when i then run sudo apt-get install -f, i get:
```
Updating /boot/grub/menu.lst ... done

Cannot delete /boot/initrd.img-2.6.15-26-386, doesn't exist.
Unpacking linux-restricted-modules-2.6.15-26-386 (from .../linux-restricted-modules-2.6.15-26-386_2.6.15.11-3_i386.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.15-26-386_2.6.15.11-3_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.15-26-386/fcdsl/fcdsl-lib.o')
Errors were encountered while processing:
 /var/cache/apt/archives/libnss3_2%3a1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb
 /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb
 /var/cache/apt/archives/linux-restricted-modules-2.6.15-26-386_2.6.15.11-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo aptitude install -f gives me: 
```
Package linux-restricted-modules-2.6.15-26-386 is not installed.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-image-386; however:
  Package linux-image-386 is not configured yet.
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on firefox-gnome-support; however:
  Package firefox-gnome-support is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-386
 firefox-gnome-support
 linux-restricted-modules-386
 linux-386
 ubuntu-desktop

```

seems totally messed up

---

