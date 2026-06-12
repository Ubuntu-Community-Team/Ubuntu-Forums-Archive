---
title: "Mounting Win2k8 File Share"
date: 2009-06-10
forum: General Help
---

### Post by GaryS128 on 2009-06-10
I'm having a problem mounting a Windows 2008 file share. At first try to mount the share, I will get "error 112 = Host is Down", any attempt after that will result in "error 2 = No such file or directory". Using smbclient and the same arguments, I am able to connect and browse the share. Anyone have any idea what I am doing wrong or an incompatibility? I can mount Windows 2003 file shares just fine. below is the command I am using

```

mount -t cifs //shareserver/share/ /mnt/location/ -o user=Username,pass=Password

```

---

### Post by GaryS128 on 2009-06-10
Sorry, I forgot to mention I am using Ubuntu 9.04 and samba 3.0.28a

---

### Post by GaryS128 on 2009-06-11
Bump? :(

---

