---
title: "Sharing Files (local network)"
date: 2009-02-28
forum: General Help
---

### Post by majikhotline on 2009-02-28
i can shared a file with 2 linux machines but i cant share a file wit ubuntu and a windoze machine.  i have the a ubuntu machine configured with a windoze group name, i can see the ubuntu machine in the windoze network and when i click on the icon it says i do not have permisson.  where did i go wrong?

---

### Post by insineratehymn on 2009-02-28
Right click on the folder and be sure that "other persons can change my files" or whatever it says is clicked.

---

### Post by Iowan on 2009-02-28
Have you set up [Samba]("https://help.ubuntu.com/community/SettingUpSamba")? Does the Windows user have both an Ubuntu account and a Samba account (or do you have security=share in */etc/samba/smb.conf*)?  If you didn't specifically set up */etc/samba/smb.conf*, the info may be in */var/lib/samba/usershares *.

---

### Post by majikhotline on 2009-02-28
i set up samba, i must have it misconfigured cause it's telling me that is have a parameter is incorrect, which parameter do i configure

---

### Post by Iowan on 2009-02-28
Does **testparm** shed any light - or is that what reported incorrect parameter?

---

### Post by majikhotline on 2009-02-28
testparm results

```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[your share name]"
Loaded services file OK.

```

---

