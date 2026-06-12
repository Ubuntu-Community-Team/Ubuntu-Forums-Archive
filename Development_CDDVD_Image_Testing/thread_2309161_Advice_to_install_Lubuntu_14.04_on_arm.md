---
title: "Advice to install Lubuntu 14.04 on arm"
date: 2016-01-08
forum: Development CD/DVD Image Testing
---

### Post by sarah25 on 2016-01-08
Hello

I have recently bought a development board from Orbbec which uses Lubuntu 14.04.

I have wrongly modified the /etc/sudoers file. Now the file is corrupted. I can't use sudo anymore. I cannot use su or pkexec because it requires a root password which I don't know.

I would like to reinstall the operating system.
I have created a bootable USB, but the device does not have a grub, so I cannot boot on the USB key. I cannot mount the iso in command line since I cannot use sudo.

Please someone, any idea what else I could try?

Thank you very much for your help.

---

### Post by matt_symes on 2016-01-08
Hi

> **sarah25 said:**
> Hello

I have recently bought a development board from Orbbec which uses Lubuntu 14.04.

I have wrongly modified the /etc/sudoers file. Now the file is corrupted. I can't use sudo anymore. I cannot use su or pkexec because it requires a root password which I don't know.

I would like to reinstall the operating system.
I have created a bootable USB, but the device does not have a grub, so I cannot boot on the USB key. I cannot mount the iso in command line since I cannot use sudo.

Please someone, any idea what else I could try?

Thank you very much for your help.

Firstly welcome to the forums :)

To start with, when you want to edit the sudoers file use

```
sudo visudo
```

It's the safest way to edit the sudoers file as it will not allow you to save the sudoers file if there is an error. i.e it will perform basic syntax checking on the file before you can save it.

> I have created a bootable USB, but the device does not have a grub, so I cannot boot on the USB key.

I think you may be confusing GRUB for a BIOS with the above statement.

I know nothing about the Orbbec board so this may be off base but, as a first suggestion, can you boot into recovery mode (a root shell) for the kernel ? 

If you can then you can fix your sudoers file from there by reverting the changes you made to it.

Kind regards

---

