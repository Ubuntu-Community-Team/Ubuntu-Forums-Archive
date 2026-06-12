---
title: "Ubuntu Live cd gives weird error on booting"
date: 2008-05-12
forum: Desktop Environments
---

### Post by jeroenprogdevexp on 2008-05-12
Hello when I want to boot from the ubuntu live cd I receive a weird eroor.
The error is as follown:

inflate_dynamic+0x442/0x720
unpack_to_rootfs+0x7af/0x960
vprintk+0x340/0x370
early_populate_rootfs+0x4b/0x60
start_kernel+0x31a/0x3b0
unknown_bootoption+0x0/0x260

code 00 05 84 ...
....
EIP [<c03e77f9>]huft_build+0x69/0x600 SS:ESP 0068:c03dfe78
Kernel panic - not syncing: Attempted to kill the idle task!

Has anybody an idea what is wrong, and how i can solve this issue?

Thanks in advance,
Kind regards,
Jeroen

---

### Post by overdrank on 2008-05-12
> **jeroenprogdevexp said:**
> Hello when I want to boot from the ubuntu live cd I receive a weird eroor.
The error is as follown:

inflate_dynamic+0x442/0x720
unpack_to_rootfs+0x7af/0x960
vprintk+0x340/0x370
early_populate_rootfs+0x4b/0x60
start_kernel+0x31a/0x3b0
unknown_bootoption+0x0/0x260

code 00 05 84 ...
....
EIP [<c03e77f9>]huft_build+0x69/0x600 SS:ESP 0068:c03dfe78
Kernel panic - not syncing: Attempted to kill the idle task!

Has anybody an idea what is wrong, and how i can solve this issue?

Thanks in advance,
Kind regards,
Jeroen
Hi and welcome, You may want to look at this link  
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jeroenprogdevexp on 2008-05-13
Hello,

Thanks for your reply.

The checksum is OK. 
I burned the ISO correctly, because I was able to install ubuntu on another PC with the same CD. My conclusion is that there must be something wrong with that certain PC's hardware or bios settings ... any suggestions?

Kind regards and thanks for the help.
Jeroen

---

### Post by overdrank on 2008-05-13
> **jeroenprogdevexp said:**
> Hello,

Thanks for your reply.

The checksum is OK. 
I burned the ISO correctly, because I was able to install ubuntu on another PC with the same CD. My conclusion is that there must be something wrong with that certain PC's hardware or bios settings ... any suggestions?

Kind regards and thanks for the help.
Jeroen

Hi and I have not seen those errors myself but what are the system specs and maybe something will stand out and others may help. A little bump to the top :)

---

