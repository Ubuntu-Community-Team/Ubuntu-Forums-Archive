---
title: "Darwinia demo"
date: 2010-05-25
forum: Gaming &amp; Leisure
---

### Post by Rustybolts on 2010-05-25
Trying to get the demo working before I decide to purchase full game. Windows demo runs in wine. Have followed sticky for full version in 64bit gaming guides.

Terminal error when running installer
> /home/rustybolts/.setup5392: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2010-05-25
[http://cz.archive.ubuntu.com/ubuntu/pool/universe/g/glib1.2/libglib1.2ldbl_1.2.10-19build1_i386.deb](http://cz.archive.ubuntu.com/ubuntu/pool/universe/g/glib1.2/libglib1.2ldbl_1.2.10-19build1_i386.deb)

Try this one;

getlibs -i libglib1.2ldbl_1.2.10-19build1_i386.deb

---

### Post by Rustybolts on 2010-05-25
Install now works but when i run Darwinia binary in terminal i receive:
> /home/rustybolts/darwinia-demo2/lib/darwinia.bin.x86: /home/rustybolts/darwinia-demo2/lib/../lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

---

### Post by Perfect Storm on 2010-05-25
```
sudo cp -r /usr/lib32/libgcc_s.so.1 /usr/local/games/darwinia/lib

```
note this /usr/local/games/ is where the games is installed by default. If you installed it anywhere else you need to change the line.

---

### Post by Rustybolts on 2010-05-25
Many thanks! That did it as a matter of interest did the last command copy the file  from my 32bit library file to the darwinia lib folder? (sudo cp -r)

---

### Post by Perfect Storm on 2010-05-25
> **Rustybolts said:**
> Many thanks! That did it as a matter of interest did the last command copy the file from my 32bit library file to the darwinia lib folder? (sudo cp -r)

Aye.

---

### Post by danielsouzat on 2011-06-18
I know it's already solved but maybe it help someone that come here with other difficulties that aren't solved.
I wrote a complete how-to upon installing it onto Ubuntu 11.04. 


[**[http://cp.daniel.souza.nom.br/?p=17](http://cp.daniel.souza.nom.br/?p=17)**]("http://cp.daniel.souza.nom.br/wp-admin/post.php?post=17&action=edit")

---

