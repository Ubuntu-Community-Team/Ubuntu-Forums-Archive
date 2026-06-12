---
title: "Setting up a file server"
date: 2004-10-18
forum: General Help
---

### Post by nyqo on 2004-10-18
I am new to Ubuntu, Samba, and Gnome, so I appologize for lack of understanding.  I have read the Samba help and the previous questions here, but most of these seem to be trying to set-up samba's access to windows. I have this working i.e. I can access my windows machines. 

However, I am trying to set-up Ubuntu to be a file server/backup storage. I have been able to get samba to share a directory from my /home/user-name area, but I would like to share my hda3 (fat32) partition as a common area for my windows machines to access. 

It seems that I need to have root do this because it will not allow me to share the /mnt/Shared directory (where I have mounted hda3) as my user.  However when I try to "sudo chown user-name /mnt/Shared", I am told that I cannot do this, any thoughts?

Thanks in advance, Ubuntu seems to be a great distro.

---

