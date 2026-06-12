---
title: "Problems Installing NIC"
date: 2006-06-23
forum: Desktop Environments
---

### Post by rnsimmons on 2006-06-23
I've just installed Ubuntu 5.10, but am having problems getting it on my network.  I initially had an Intel Pro 10/100 card in the box.  Ubuntu didn't recognize it.  I then changed to a 3c905B-TX card and tried to install the Linux drivers from 3com's support website.  I followed the directions for installing, but get the message "-bash: ./install3c90x: /bin/csh: bad interpreter: No such file or directory".

Help!!!!!  ](*,)

---

### Post by rnsimmons on 2006-06-24
[QUOTE=rnsimmons]I've just installed Ubuntu 5.10, but am having problems getting it on my network.  I initially had an Intel Pro 10/100 card in the box.  Ubuntu didn't recognize it.  I then changed to a 3c905B-TX card and tried to install the Linux drivers from 3com's support website.  I followed the directions for installing, but get the message "-bash: ./install3c90x: /bin/csh: bad interpreter: No such file or directory".

Help!!!!!  ](*,)[/QUOTE]
I figured it out.  I didn't have the csh package installed.  However, now the install3c90x is telling me that the install is for kernel 2.4 and I'mm running 2.6.  Can anyone help me figure out how to get the 3c90x installed on Ubuntu 5.10?

---

