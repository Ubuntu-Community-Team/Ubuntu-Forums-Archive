---
title: "Ubuntu file sharing"
date: 2006-06-12
forum: Desktop Environments
---

### Post by wpshooter on 2006-06-12
Am I correct in that if I have a home computer network consisting of a mixture of Ubuntu/Linux machines and Microsoft Windows machines that I would want to install SAMBA to do the sharing ?  And if the home computer network consisted of ONLY Unbuntu/Linux machines I would install NFS ?

P.S. - Is it possible to have both of these installed at the same time ?

Thanks.

---

### Post by mjm115 on 2006-06-12
This is correct, but by default, Samba comes installed in Dapper.  You just have to specify your workgroup name and PC name for the network

---

### Post by PriceChild on 2006-06-12
Samba doesn't come installed by default on dapper..... does it?
 
Pricey

---

### Post by wpshooter on 2006-06-12
[QUOTE=mjm115]This is correct, but by default, Samba comes installed in Dapper.  You just have to specify your workgroup name and PC name for the network[/QUOTE]

Thanks for your reply, but are you sure about that, because when I initially click on file sharing under administration, it pops and and says that in order to share files I must install either SAMBA or NFS, it has a check box beside each one ?

Thanks.

---

### Post by ayoli on 2006-06-12
[QUOTE=PriceChild]Samba doesn't come installed by default on dapper..... does it?
 
Pricey[/QUOTE]
right i had to apt-get install samba after a default innall of dapper.

[QUOTE=wpshooter]

P.S. - Is it possible to have both of these installed at the same time ?

Thanks.[/QUOTE]
yes, i think.

---

### Post by wpshooter on 2006-06-12
O' Man, this works GREAT !!!!

THANK YOU.

---

