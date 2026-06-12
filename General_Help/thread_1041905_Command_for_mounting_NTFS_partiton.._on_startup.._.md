---
title: "Command for mounting NTFS partiton.. on startup.. automatically"
date: 2009-01-17
forum: General Help
---

### Post by jskandhari on 2009-01-17
My Ubuntu 8.10 is on eXternal Hdd so as by default Ubuntu doesn't mount other Hdd. Automatically and my NTFS partition is the one in which all the data folders an stuff is stored..

i tried the NTFS mount commands using the help in the terminal but of no help.

---

### Post by jerome1232 on 2009-01-17
Alot of people like to use ntfs-config, it's a gui to add ntfs drives to your fstab.

To install it just open synaptic package manager and search for it, then mark it for installation.

For info about the manual way to make them mount on boot up take a look here [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by jskandhari on 2009-01-17
All i need is the command that i can include in the startup list.... so that it automatically mounts my on board hdd partition..

but it will do only the mounting the same which i do now also manually ..

---

### Post by dcstar on 2009-01-17
> **jskandhari said:**
> All i need is the command that i can include in the startup list.... so that it automatically mounts my on board hdd partition..

but it will do only the mounting the same which i do now also manually ..

As the other post said - put it in the fstab file and it will mount automatically.

You do not add manual mount commands to any startup list, that is utterly pointless when the proper (fstab) method exists for this specific purpose.

---

