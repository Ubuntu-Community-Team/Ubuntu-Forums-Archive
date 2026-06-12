---
title: "chmod help"
date: 2009-02-02
forum: General Help
---

### Post by ForMar on 2009-02-02
I am trying to use the chmod command on a mounted partition in the /mnt dir. For some reason it will not let me change the owner saying that the "operation is not permitted". I'm sure that there is log somewhere that can give more info that I would be happy to post. BTW the command I am giving is:

```
sudo chmod -L username dir 
```
I also tried it without the -L option but both dont work


Well after asking around a bunch I got the answer

fat32 does not have user permissions 
there are ways around it though:
[http://www.linuxforums.org/forum/installation/38815-chown-problem-chnging-dir-ownership.html](http://www.linuxforums.org/forum/installation/38815-chown-problem-chnging-dir-ownership.html)

---

### Post by adamlau on 2009-02-02
That is the syntax for chown. The -L option is implicit (default) and does not typically need to be optioned in the argument. Try: 

```
sudo chown username /mnt/dir
```

Followed by the following for typical single user/owner permissions: 

```
chmod 700 username /mnt/dir
```

---

### Post by Yellow Pasque on 2009-02-02
Persmissions for a mounted partition will also depend on how you mount it. What command are you using to mount (or what does the /etc/fstab line look like)?

---

### Post by ForMar on 2009-02-02
> **Temüjin said:**
> Persmissions for a mounted partition will also depend on how you mount it. What command are you using to mount (or what does the /etc/fstab line look like)?

I mounted it by editing the fstab
```
/dev/sda3       /mnt/sharedir   vfat    defaults       0       0
```

adamlau I tried what you suggested but got the same error

Thanks to everyone for your time and help

---

### Post by ForMar on 2009-02-03
anyone?

---

### Post by ForMar on 2009-02-03
come on I know someone knows the answer to this!

---

