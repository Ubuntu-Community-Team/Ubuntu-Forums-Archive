---
title: "Cant be root!"
date: 2005-02-24
forum: Desktop Environments
---

### Post by cdhotfire on 2005-02-24
When i try to do sudo, in terminal it says:
```

Sorry, sudo must be setuid root.

```
can anyone help, i cant do much of anything now. Also this happened after i set up the auto login.

---

### Post by bored2k on 2005-02-24
[QUOTE=cdhotfire]When i try to do sudo, in terminal it says:
```

Sorry, sudo must be setuid root.

```
can anyone help, i cant do much of anything now. Also this happened after i set up the auto login.[/QUOTE]


Ubuntu doesnt uses root by default

in terminal type 
> $sudo su 
and input ur user password

this gives u root access in Ubuntu.

If u want root , then do
> #passwd  as root .

---

### Post by jmings on 2005-02-25
What I would do is:
1) boot with the live disk.
2) mount the partition your root is located (probably hda1)
3) bring up the root terminal from the menu 
     [Applications -> System Tools -> root terminal ]
4) edit using a command-line editor /mnt/hda1/etc/passwd
     change the line
root:x:0:0:root:/root:/bin/bash
      to
root::0:0:root:/root:/bin/bash
     save and exit
5) boot from disk
6) in a terminal enter the command
passwd root
[enter new root password twice] 

YMMD

Of course you could directly edit the /mnt/hda1/etc/sudoers and add the automatic logon you are using.

---

