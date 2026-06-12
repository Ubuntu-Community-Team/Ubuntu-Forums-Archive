---
title: "edititing /boot/grub/menu.Ist"
date: 2009-01-11
forum: General Help
---

### Post by MarkenK on 2009-01-11
Hello, sorry for bothering.

i'm trying to fix a fan bug on my laptop. a guide is telling me: "Then, edit /boot/grub/menu.lst file and add acpi_no_auto_ssdt to the kernel boot lines. Add it to the #defoptions line to make all the new kernel additions enabled with that too. This tells the kernel to not make a new dsdt file at boot and reads the dsdt file you copied."

i don't really know where to exactly add it, and i'm afraid i'll put it on a wrong line.

Would anyone be so kind to point out exactly where to type it.
/boot/grub/menu.Ist is attatched

---

### Post by avtolle on 2009-01-11
I'd add it to your kernel line for now (as is suggested) to see whether it works as you wish. I'll leave it to others as to whether to add a #defoptions line to your /boot/grub/menu.list file, as I'm not knowledgeable in this area.

---

### Post by spiderbatdad on 2009-01-11
Observe the rules here:
```
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

```

Edit this section:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f3a41c9d-0501-4c5c-85f0-3453ba3a271a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=XXXX ro ROOTFLAGS=syncio** acpi_no_auto_ssdt**
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```

And this section:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=**acpi_no_auto_ssdt**

```

---

### Post by MarkenK on 2009-01-11
hmm... still a problem with the fan not working

the guide is at: [https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G)

so far i have copied the file to /etc/initramfs-tools

i have no idea what means leaving the uppercase up. Is that important?

i have updated initframs in the terminal

and i have added the acpi... to /boot/grub/menu.Ist

And when i reboot and a lot of text is running through the screen i can see 5 or 6 acpi: error installing bay notify handler

can anyone help me?

---

