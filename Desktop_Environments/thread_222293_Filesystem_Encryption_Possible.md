---
title: "Filesystem Encryption Possible?"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-07-24
File permissions are great but the recovery mode is always sitting around waiting to allow any thief local root access. I'm wondering if there's an encrypted file system support available in Ubuntu? Perhaps something like scramdisk/safecrypt where you can define an entire encrypted volume which is inaccessible to every user (including root) without the key-pair passphrase...

---

### Post by wieman01 on 2006-07-24
I reckon you are looking for a Linux/Ubuntu standard solution and not for a 3rd party software, right? I am using Truecrypt which is a pretty convenient tool for such requirements. 

It is free and fairly reliable. Perhaps not the most convenient tool, but check it out if that's what you are looking for.

[http://www.truecrypt.org/]("http://www.truecrypt.org/")

I don't know any other tool apart from this one.

---

### Post by JoWilly on 2006-07-24
Look here : [http://ubuntuforums.org/showthread.php?t=216356]("http://ubuntuforums.org/showthread.php?t=216356")

If you like encrypted containers/volumes, jetico.com 's bestcrypt has worked for many years and has the advantage to use your volumes in windows and linux.

If you are looking for full hd partition and root partition encryption, there are also several ways. Search these forums, this has been talked about many times.

---

### Post by mlind on 2006-07-24
I reckon [LUKS]("http://luks.endorphin.org/") would be right choice. There's also very stable kernel module for this purpose called cryptoloop, see *aptitude show cryptsetup*

---

### Post by Thund3rstruck on 2006-07-25
Great.. truecrypt looks like exactly what I need.

---

### Post by wieman01 on 2006-07-25
> **Thund3rstruck said:**
> Great.. truecrypt looks like exactly what I need.

Glad to hear it. Encrypted folders/files can be open from both Windows & Linux. May turn out to be an advantage one day, who knows.

---

