---
title: "RAM vs SWAP"
date: 2006-06-26
forum: Desktop Environments
---

### Post by quedigg on 2006-06-26
Hello Fellows, 
is there any relation between RAM size and the swap's partition ?
i have 512 Mb RAM ,how should my SWAP be ?

Many thanks in advance ...

---

### Post by kinalus on 2006-06-26
[QUOTE=quedigg]Hello Fellows, 
is there any relation between RAM size and the swap's partition ?
i have 512 Mb RAM ,how should my SWAP be ?

Many thanks in advance ...[/QUOTE]

Hi, 
I usually create a swap partition twice as big as the RAM size.
Linux can work even without a swap partition but I think it is recommended
to use at least a swap partition as large as the the RAM size, which is also the 
minimum requirement for hibernation to work properly. For memory intensive
applications 2*(RAM size) worked fine for me so far. 

Best regards

---

### Post by matthew on 2006-06-26
I would agree with the other poster's formula of 2*(RAM) until the swap partition reached 1 Gib.Iit really shouldn't be necessary to have one larger.

So for you specifically, I would recommend a 1 Gib swap.

---

