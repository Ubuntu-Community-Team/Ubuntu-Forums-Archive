---
title: "How to move files between drives as guest?"
date: 2009-05-27
forum: General Help
---

### Post by Nixie Pixel on 2009-05-27
Hi, I have set up several samba shares on my Ubuntu Server installation, with security set to share and guests allowed. I have Windows machines that will be accessing these shares without linux usernames set up, so guests need to be allowed access to read/write/execute the files.  

If I move files between the shared drives via a guest connecting to the machine, there is no issue, the files are owned by "nobody," and guests have access. If I move files from the server console, the owner is set to "root" and guests can no longer move or manipulate the files.

The problem is that if I move files from another machine, it actually copies them from the server to the client and then back, which for over 500GB of data will take an extremely long time.  

There must be a simple way for me to move files while at the server console but make them all available to guests, yes?

Thanks!

---

### Post by Nixie Pixel on 2009-05-27
Is there a way to change to "guest" on the console so that "guest" permissions are kept intact?

Or perhaps a way to chmod and/or chown recursively (to modify the permissions/ownership of all files in a directory structure)?

---

### Post by neosurge on 2009-05-28
chown -R username.username directory
chmod -R 777 directory


Changes the ownership/permissions recursively.

---

### Post by veruus on 2009-05-28
> **Nixie Pixel said:**
> Is there a way to change to "guest" on the console so that "guest" permissions are kept intact?

Or perhaps a way to chmod and/or chown recursively (to modify the permissions/ownership of all files in a directory structure)?

This should work:

sudo -u guest mv /var/lib/samba/usershares/shareblarg/* /var/lib/samba/usershares/sharefoo/.

---

### Post by Nixie Pixel on 2009-05-28
Wow, thanks for the help, I'll give it a shot right away.

---

