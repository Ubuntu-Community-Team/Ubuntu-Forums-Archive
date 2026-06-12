---
title: "ubuntu Partitions"
date: 2006-04-23
forum: Desktop Environments
---

### Post by morequarky on 2006-04-23
](*,) 
i know ubuntu needs one '/' partition and '/home' partition would be nice for personal files.](*,) 

why are their other partition options like '/var' and '/tmp'? ](*,)  How big should the partitions for each be?  Are the other options only for servers?  ](*,) Do you use any of the other partition options?

I noticed that ubuntu won't let me install one of each.  there is a limit to the number of types of partitions i can have.

Is there a howto on those different partitioning options?](*,) 
](*,) 
Thanks,  quarky

---

### Post by Qrk on 2006-04-24
You don't need or want a separate partition for /var, /tmp /etc or any of those folders. These folders are just top level directories on the / partition, not separate partitions. 

Although some people like having /usr or /boot on a separtate partition, you shouldn't wory about it. Just make three partitions, one for / and one for /home, with a swap partiton.

Each of these directories should be on the / partition. Ubuntu won't let you make more than that because you can only have four primary partitions at a time. 

Here is a good rule of thumb:
/                10 GB
swap          1.5x RAM
/home         rest of space


Think of /usr as "Program files" on widows. /home as "my documents" (although it is soo much more) 
 / is the  C: equivalent

---

