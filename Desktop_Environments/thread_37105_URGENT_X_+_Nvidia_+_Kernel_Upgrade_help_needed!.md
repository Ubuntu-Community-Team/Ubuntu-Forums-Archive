---
title: "URGENT X + Nvidia + Kernel Upgrade help needed!"
date: 2005-05-25
forum: Desktop Environments
---

### Post by tommy04 on 2005-05-25
I need some help.

I upgraded the kernel and now the nvidia graphics module does not load. xorg.conf is fine, I checked it, but the module "Nvidia" cannot be found. I tryed to remove and reinstall the nvidia drivers, but it gave me an error.

Sorry for the sloppy grammer, but I'm in a bit of a hurry. Any help would be REALLY appreciated!!!!!

---

### Post by Xian on 2005-05-25
[QUOTE=tommy04]I upgraded the kernel and now the nvidia graphics module does not load. xorg.conf is fine, I checked it, but the module "Nvidia" cannot be found.[/QUOTE]
You didn't mention which kernel you upgraded to, but absent that information I would just remind you to be certain the linux-restricted-modules package matches your kernel type.

---

### Post by tommy04 on 2005-05-25
Sorry for being such a noob but... can you tell me how to do that? I usually use Synaptic...

---

### Post by Xian on 2005-05-25
[QUOTE=tommy04]Sorry for being such a noob but... can you tell me how to do that? I usually use Synaptic...[/QUOTE]
That would be difficult to do precisely since I don't know what kernel you are using. So I can only tell you again to match the restricted-modules to your kernel type. For example, if you are using the k7 kernel, then this is the package you would need to install:

```
$ sudo apt-get install linux-restricted-modules-k7
```

Search for 'restricted-modules' in Synaptic if you want to go that route.

---

### Post by tommy04 on 2005-05-25
Eeek. I forgot to mention X doesn't load.

I'm using kernels 2.6.10.x-i386 and 2.6.11.x-i386, which was upgraded from synaptic, causing all this mess.

---

### Post by Xian on 2005-05-25
Assuming your /boot/grub/menu.lst file still contains the previous kernel to boot from, you might just want to remove the newer kernel giving you these problems, and then ensure that you have the linux-restricted-modules-386 package installed to match the booted kernel.

```
$ sudo apt-get remove linux-image-2.6.11-1-386
$ sudo apt-get install linux-restricted-modules-386
```
If you still can't get X to load then issue the command below from a prompt after boot, and then change your video driver to something generic that X can use, like 'vesa' (see below). Then just save the file [ctrl + x] and enter to confirm.


```
$ sudo nano -w /etc/X11/xorg.conf
```

```
Section "Device"
	Identifier	"NVIDIA Corporation"
	Driver		"vesa"
	BusID		"PCI:2:0:0"
```

---

### Post by tommy04 on 2005-05-26
Well, I tried booting into the kernel that was working before (I'm in it right now, actually), but it won't work either. I set the driver to vesa, but I need my OpenGL and large resolutions...

---

### Post by tommy04 on 2005-05-26
Reinstalling didn't work ;_;

---

### Post by tommy04 on 2005-05-26
EDIT: Wrong thread! I forgot which page I was on '^_^

---

