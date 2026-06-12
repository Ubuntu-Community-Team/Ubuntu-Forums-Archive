---
title: "Where can I find Jammy mini.ISO?"
date: 2022-04-25
forum: Desktop Environments
---

### Post by greg2lapa on 2022-04-25
In the past, have always been able to find the mini.iso at URL like follows but none exists for Jammy:
[http://archive.ubuntu.com/ubuntu/dists/jammy/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jammy/main/installer-amd64/current/images/netboot/mini.iso)

Where can I find Jammy's mini.iso?

---

### Post by deadflowr on 2022-04-25
Does not exist anymore.

Edit: Unless they've buried it even deeper this time.
Which I doubt.

---

### Post by grahammechanical on 2022-04-25
The Ubuntu 22.04 installer has a minimal install option.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

Regards

---

### Post by him610 on 2022-04-25
You might want to consider the LTS 22.04 server download. It is a lot smaller than the desktop version; although, not as small as the mini.iso of the past. Download 22.04 server here, [https://releases.ubuntu.com/22.04/]("https://releases.ubuntu.com/22.04/")

The LTS 22.04 server has all of the same basic software as the desktop version without all of the GUI applications. You can tailor the server version to your actual specifications. If there is a package you don't want then there is no need to install it. 

A link to the 22.04 file listings - [https://releases.ubuntu.com/22.04/ubuntu-22.04-live-server-amd64.list]("https://releases.ubuntu.com/22.04/ubuntu-22.04-live-server-amd64.list")

---

### Post by greg2lapa on 2022-04-26
> **him610 said:**
> You might want to consider the LTS 22.04 server download. It is a lot smaller than the desktop version; although, not as small as the mini.iso of the past. Download 22.04 server here, [https://releases.ubuntu.com/22.04/](https://releases.ubuntu.com/22.04/)

The LTS 22.04 server has all of the same basic software as the desktop version without all of the GUI applications. You can tailor the server version to your actual specifications. If there is a package you don't want then there is no need to install it. 

A link to the 22.04 file listings - [https://releases.ubuntu.com/22.04/ubuntu-22.04-live-server-amd64.list](https://releases.ubuntu.com/22.04/ubuntu-22.04-live-server-amd64.list)

When labeled "server" it is the same as the desktop version, just a more minimal footprint? In other words, after installing the "Server" version, one could manually install all the same things as the Desktop version and they would be the same? 

I assumed the "server" version had different kernel modules present and other changes that made it less ideal for desktop use.

---

### Post by oldfred on 2022-04-26
It has to be about 10 years since Kernel in server & desktop were different.

The old minimal was BIOS only and since most systems are now UEFI, I presume that is why they did away with it.

Part of server install is this app which you can run separately which lets you choose what additional software you want. If you choose one of the standard desktops you get all the standard software that desktop includes.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by ActionParsnip on 2022-04-26
The desktop and server kernels are identical. The desktop comes with a graphical UI and the server is CLI only (But can have desktop things installed)

---

