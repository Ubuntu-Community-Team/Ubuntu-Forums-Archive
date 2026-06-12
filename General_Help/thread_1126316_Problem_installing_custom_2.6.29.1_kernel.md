---
title: "Problem installing custom 2.6.29.1 kernel"
date: 2009-04-15
forum: General Help
---

### Post by luquino on 2009-04-15
Hi to all.
I'm trying to compile 2.6.29.1 kernel on Jaunty, I downloaded the sources from Ubuntu repos, made some few changes to .config and compiled it like this
```
sudo time make-kpkg --rootcmd fakeroot --initrd kernel_image kernel_headers modules_image
```

I attach the full result of the compilation for more info. (sorry for spanish)

headers package installs ok.
```
luca@luca-desktop:/usr/src$ sudo dpkg -i linux-headers-2.6.29.1_2.6.29.1-10.00.Custom_amd64.deb 
[sudo] password for luca: 
Seleccionando el paquete linux-headers-2.6.29.1 previamente no seleccionado.
(Leyendo la base de datos ...  
175507 ficheros y directorios instalados actualmente.)
Desempaquetando linux-headers-2.6.29.1 (de linux-headers-2.6.29.1_2.6.29.1-10.00.Custom_amd64.deb) ...
Configurando linux-headers-2.6.29.1 (2.6.29.1-10.00.Custom) ...
```

but I got this error installing the kernel package
```
luca@luca-desktop:/usr/src$ sudo dpkg -i linux-image-2.6.29.1_2.6.29.1-10.00.Custom_amd64.deb 
Seleccionando el paquete linux-image-2.6.29.1 previamente no seleccionado.
(Leyendo la base de datos ...  
182945 ficheros y directorios instalados actualmente.)
Desempaquetando linux-image-2.6.29.1 (de linux-image-2.6.29.1_2.6.29.1-10.00.Custom_amd64.deb) ...
Done.
Configurando linux-image-2.6.29.1 (2.6.29.1-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.29.1
Found kernel: /vmlinuz-2.6.29-02062901-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.29.1.postinst line 1186.
dpkg: error al procesar linux-image-2.6.29.1 (--install):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.29.1
luca@luca-desktop:/usr/src$ 

```

On my pc I have two installation of Ubuntu:
- on sda2 Intrepid with 2.6.27
- on sda3 Jaunty with 2.6.28
  in jaunty I installed as well the 2.6.29.1 kernel from Ubuntu ppa kernel.

Both versions of ubuntu share the /boot on sda1.

Can somebody help me installing my custom kernel?

---

### Post by khelben1979 on 2009-04-15
I think [this thread]("http://forums.opensuse.org/install-boot-login/401200-good-documentation-compiling-kernel.html#post1904742") can be of interest for you. It contains a lot of good links also.

It's not easy compiling a custom kernel. Spending one day of reading some documentation on the subject is definitely a good thing, I think, "if" one has the patience for it.

---

### Post by luquino on 2009-04-15
thanks for your link khelben, but it does not resolve my problem.
I assure to you that I red a lot of guides, and I spent much more than 1 day studing the kernel compilation.
The link you posted refers to a general discussion on how to create a valid .config file.
If you should have read my post you' d find out that my problem is not to create .config file, my problem is that the command ```
sudo dpkg -i linux-image-xxx
``` report a error code 2, but I don' t have any chance to understand what kind of error is this.
I suspect that is something related with the kernel compilation "ubuntu-way" (not "open-suse way"), but I don' t know what it is.

---

### Post by khelben1979 on 2009-04-15
If you post the line with the error code 2 including the previous 20 lines in the compilation process, it should be easier to understand what might be wrong (although I must confess that I myself may not understand it, but someone else may).

---

### Post by luquino on 2009-04-15
ok, I posted too many lines? it was just to give more info, I edited the post to make it more readable.
Anyway, I give even more info:
- my custom kernel can boot and works fine, I'm trying to test everything I can test.
- booting I can see only 2 errors: APPARMOR fails and VirtualBox drivers fails loading.

In /boot I don' t have any ABI file related with my kernel.

---

### Post by luquino on 2009-04-17
Bump.... anybody can help me?

---

### Post by danwood76 on 2009-04-17
It looks like the nvidia drivers dont build a dynamic kernel module. (using dkms)
Nothing critical unless you want the nvidia drivers loaded?

---

### Post by luquino on 2009-04-18
> **danwood76 said:**
> It looks like the nvidia drivers dont build a dynamic kernel module. (using dkms)
Nothing critical unless you want the nvidia drivers loaded?

Well I need the nvidia driver to use compiz, but actually the nvidia driver is loaded and functional on the custom kernel.
the problem is that every other software I try to install from repos give the same error, even if it looks like to work well after the installation and I just have some problem using VirtualBox.
I tried to compile a kernel on my eeepc without any restricted drivers and DKMS, using exactly the same commands and there I don' t have a single problem.
So I guess that on the desktop pc the problem is DKMS or may be some of the restricted drivers.
The first thing I' m  trying to understand is if are required some more steps in kernel building when dkms or restricted drivers are present.

---

### Post by danwood76 on 2009-04-18
The nvidia driver is causing the issue and is the weak link.
Remove it through synaptic and remove dkms.

Then install the nvidia driver manually and it should fix it.

---

### Post by luquino on 2009-04-18
yes danwood, you are definitely right.
There is a bug opened on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/345079]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/345079")
Thanks a lot for your help

---

