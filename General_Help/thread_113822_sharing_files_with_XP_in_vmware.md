---
title: "sharing files with XP in vmware"
date: 2006-01-07
forum: General Help
---

### Post by nandasunu on 2006-01-07
I have installed winXP pro wih vmware and would like to access the files on my normal harddrive within it, how can I do this?

---

### Post by AdaHacker on 2006-01-07
There are a couple of ways.  If the VM can access your Linux box through a network connection, you can set up some Samba shares on your Linux box and access them normally from the VM.  Second, you can use VMware's shared directory feature.  Of course, that will require installing vmware-tools on the VM and it's not available if you're using the freeware VMware Player.

---

### Post by garren on 2008-01-13
Is there a way to share a directory (without samba) using VMWare Server?  I'm using VMWare server, and would prefer to use a built-in solution prior to going through the effort to setting up a Samba share.

---

### Post by fjgaude on 2008-01-13
I use the free VMware Server and I've found no way to share files other than through NAT and Samba.

It's easy to setup shared files in Ubuntu through the System/Administration dropdown menus. Then all that's left is to enter your smbpasswd in the terminal. Then use Network in Windows to get to the shares.

It's not very difficult. If you don't know how I'll write it out here.

---

