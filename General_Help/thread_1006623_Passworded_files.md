---
title: "Passworded files"
date: 2008-12-09
forum: General Help
---

### Post by Peter_G on 2008-12-09
Is there a was to have password protected files without compressing them into an archive thing?

---

### Post by p_quarles on 2008-12-09
> **Peter_G said:**
> Is there a was to have password protected files without compressing them into an archive thing?

Yes, this can be done pretty easily with GnuPG.

---

### Post by Peter_G on 2008-12-09
Could you elaberate? :D

---

### Post by p_quarles on 2008-12-09
Start by running: 
```
gpg --gen-key
```
and follow the directions on the screen. This will generate your unique GPG "key" with which you can encrypt files. Beyond that, it depends on the method you want to use. There are GUI utilities like Seahorse (which I believe ships standard with Ubuntu at this point), as well as the gpg command line utility, which has an elaborate and generally helpful man page. 

If you're just encrypting files for yourself, the two main commands you would use are as follows. To encrypt a file:
```
gpg --encrypt filename
```
To decrypt:
```
gpg --output target_filename --decrypt encrypted_filename.gpg
```
Those are just the very basics, though.

---

### Post by lukjad on 2008-12-09
I think there is a program called Truecrypt that might be a place to start looking. Just something to look into.

---

### Post by Peter_G on 2008-12-09
Well I meant like you click on a folder then access the files, but I was wondering if there was something where you click on the folder, a promt comes up for a password, you type it in, then you have access/can edit the files in that folder.

---

### Post by KeyserSoze93 on 2008-12-10
Try encfs:
[http://www.linux.com/feature/52820](http://www.linux.com/feature/52820)

---

### Post by snova on 2008-12-10
There is no support builtin to the filesystem, nor in any generic fs that I know of, though there are several encrypted filesystems.

And even for encrypted FS's, the closest thing you'd come to a password prompt would be when you mount it.

---

### Post by oldos2er on 2008-12-10
ccrypt is easy to use.

---

