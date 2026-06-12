---
title: "noob alert! fdisk and virtualbox"
date: 2009-04-26
forum: General Help
---

### Post by bob bobbish on 2009-04-26
Is it possible to use fdisk to find drives outside of virtualbox?  I would like to mount my music and movie directories. fdsik-l only shows the patitions in my vb. I have installed the ntfs driver and done a lot of reading but no luck so far

---

### Post by amingv on 2009-04-26
> **bob bobbish said:**
> Is it possible to use fdisk to find drives outside of virtualbox?  I would like to mount my music and movie directories. fdsik-l only shows the patitions in my vb. I have installed the ntfs driver and done a lot of reading but no luck so far

No. The virtual machine only has access to the virtual hard disks you created and nothing outside that.

If you want to have access to those folders from the virtual machine you can share them. Just select the VM you're using, click "settings" and go to "shared folders", add all the folders you need and you can mount them inside your VM (mounting process depends on what your guest OS is).

EDIT
Doh' if you're using fdisk from within the VM, Ubuntu must be your guest OS, sorry for not noticing that.

Follow the instructions here to mount it:
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

---

