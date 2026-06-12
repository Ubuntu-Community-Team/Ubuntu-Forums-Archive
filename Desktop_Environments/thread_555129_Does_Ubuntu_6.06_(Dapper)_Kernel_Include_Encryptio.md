---
title: "Does Ubuntu 6.06 (Dapper) Kernel Include Encryption Support?"
date: 2007-09-19
forum: Desktop Environments
---

### Post by xp_newbie on 2007-09-19
I came across the article "[Implementing Encrypted Home Directories]("http://www.linuxjournal.com/article/6481")" in the 2003-08-01 issue of the Linux Journal and before attempting to try the loopback encrypted filesystem technique:
> 
[LIST=1]
[*]dd if=/dev/urandom of=ciphertext.img bs=1M count=20
[*]losetup -e aes /dev/loop0 ciphertext.img
[*]mkfs -t ext2 /dev/loop0
[*]mount -o loop,encryption=aes ciphertext.img mount point
[/LIST]

I was wondering if the requirements for the kernel configuration:

> [LIST]
[*]cryptographic API support (CONFIG_CRYPTO)
[*]generic loop cryptographic filter (CONFIG_CRYPTOLOOP)
[*]cryptographic ciphers (CONFIG_CIPHERS)
[/LIST]

are already included in the Ubuntu 6.06 LTS (Dapper) kernel, or do I have to reconfigure and recompile the kernel myself in order to be able to encrypt a filesystem per the article?

Thanks,
Alex

---

