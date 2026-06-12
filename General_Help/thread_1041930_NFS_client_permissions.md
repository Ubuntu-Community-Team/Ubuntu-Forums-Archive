---
title: "NFS client permissions"
date: 2009-01-17
forum: General Help
---

### Post by Tex-Twil on 2009-01-17
Hello,
I have a nfs server which exports a folder via NFS. The owener of this folder is root:root.

When a client mounts this directory, can I set the the mount appears to be owned by somen else  (e.g. root:users ) ? I want a non root user to be able to write in this mounted directory. Or do I have to do this on the server side ?

Thanks,
Tex

---

### Post by Jose Catre-Vandis on 2009-01-17
On the server, you need to give permissions for that user to write to that directory (the user should be set up on the server!) then when you access the share from a remote machine as that user you will be able to write. So you need to have the same user on both the server and client machines. Well, that's how I do it :)

---

### Post by Tex-Twil on 2009-01-17
> **Jose Catre-Vandis said:**
> On the server, you need to give permissions for that user to write to that directory (the user should be set up on the server!) then when you access the share from a remote machine as that user you will be able to write. So you need to have the same user on both the server and client machines. Well, that's how I do it :)
ok thanks :)

Tex

---

