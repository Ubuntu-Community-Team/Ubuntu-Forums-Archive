---
title: "Unidentified kernel messeges"
date: 2009-05-20
forum: Desktop Environments
---

### Post by shayfisher on 2009-05-20
Hello all,

I'm getting these unidentified message in the my logs.
This computer is getting its home dirs from a NFS server on another machine.
Logons and mount permissions are available through NIS authentication.
As I can read from the messages there is a segmentation fault occurring over and over again.


This computer gets stuck from time to time, especially after manipulating large amounts of data over network.

Other data - The computer is running debian lenny.

Here are some of the messages:


[ 9064.022431] extract-cons-va[6437]: segfault at b7c4bc10 ip 08048a87 sp bfa68200 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[12063.971287] extract-cons-va[7119]: segfault at b7d36f18 ip 08048a87 sp bffc3da0 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[12361.581408] extract-cons-va[7172]: segfault at b7ccdf18 ip 08048a87 sp bfc5aa40 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[12554.377098] extract-cons-va[7223]: segfault at b79f8da8 ip 08048a87 sp bfb9f1c0 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[12710.969613] extract-cons-va[7254]: segfault at b7c447b8 ip 08048a87 sp bfa6d090 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[12968.721606] extract-cons-va[7315]: segfault at b7958550 ip 08048a87 sp bfd162f0 error 6 in extract-cons-vals-from-prec-file[8048000+2000]
[13236.277144] extract-cons-va[7378]: segfault at b7c03e28 ip 08048a87 sp bf91eec0 error 6 in extract-cons-vals-from-prec-file[8048000+2000]

I would appreciate it if someone could help.
Best regards,
shay.

---

