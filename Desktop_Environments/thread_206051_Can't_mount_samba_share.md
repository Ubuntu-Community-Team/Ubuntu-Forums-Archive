---
title: "Can't mount samba share"
date: 2006-06-29
forum: Desktop Environments
---

### Post by DiGiTY on 2006-06-29
Currently I can only get my samba share to mount/map if it's NOT password protected. I've fiddled with samba's .conf file and Ubuntu's Shared Folders panel to make it prompt me for my Ubuntu username & password when trying to map/mount it, but it always re-prompts me which I'm assuming means incorrect username/password, eventhough I know for sure they are entered correctly.

How do I get it to successfully mount/map my samba share using my Ubuntu username & password???

TIA

i'm running Ubuntu 6.06

---

### Post by manicka on 2006-06-29
You probably need to create a SMB user, make sure this account exists on your Ubuntu Linux.

```
sudo smbpasswd -a `*acountname*`
```

and set your password.

---

### Post by DiGiTY on 2006-06-29
whoa! it worked like a charm. thanks a mil!

quik question... how do i set permission masks per share? if not possible what's the best i could do??? (i wanna add a samba share for my www root, but with a 644 mask for files and 755 for folders, yet still have my dropbox share have the default 744 file/755 folder masks)

---

