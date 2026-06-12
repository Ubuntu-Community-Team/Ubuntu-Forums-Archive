---
title: "how to add a bootscript ??"
date: 2009-01-29
forum: Desktop Environments
---

### Post by santhoshsd on 2009-01-29
Hi,

i added a bootscript to my system by doing the following things

added the file myscript in /etc/init.d
chmod 770 /etc/init.d/myscript
update-rc.d myscript defaults 


now when I reboot my system ... the bootscript is getting executed twice ?

The content of myscript is 
```
#!/bin/sh
echo "hello" >>hello.txt
```

in hello.txt .. hello was written twice ?

how do I make sure the script gets executed only once ?

---

### Post by Yashiro on 2009-02-07
Rename all instances of the script in the rc?.d folders to begin with K apart from the in one in rcS. That's not the 'proper' way but should work.
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

