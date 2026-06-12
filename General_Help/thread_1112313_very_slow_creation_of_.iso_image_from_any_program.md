---
title: "very slow creation of .iso image from any program"
date: 2009-03-31
forum: General Help
---

### Post by andrea_p on 2009-03-31
Hi,
I had a 'slow burning speed' issue, so after checking everything I have the following situation:

Hard disk speed: OK

andrea@andrea-desktop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   6330 MB in  2.00 seconds = 3166.82 MB/sec
 Timing buffered disk reads:  270 MB in  3.04 seconds =  88.73 MB/sec

Creation of .iso images (4,3 gb) from brasero / k3b takes 20 - 30 minutes.

if I burn the .iso i got 15x speed, else 0,5x ... not funny at all.

how can I solve this problem?

my system:
jaunty x64 on core2quad


Thanks!!! Andrea

---

### Post by andrea_p on 2009-03-31
Solved,
was transmission fault, downloaded files are too fragmented..

Bye!

---

