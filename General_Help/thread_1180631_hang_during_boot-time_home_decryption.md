---
title: "hang during boot-time /home decryption"
date: 2009-06-07
forum: General Help
---

### Post by chequers on 2009-06-07
Hi all,
I created an LVM-encrypted EXT4 /home partition for my Ubuntu laptop:
```
ajlaptop.internal:~> df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1             19228276   2778032  15473496  16% /
/dev/mapper/sda2_crypt
                     211471568  70830848 129898508  36% /home

```
When Ubuntu is booting, I am prompted to type the passphrase for this partition. However, more than 50% of the time the keyboard doesn't respond to key presses!

I've noticed that during the boot sequence, just before it asks for my passphrase, the hard drive in my laptop goes "click". Booting into recovery mode also seems to work all the time.

I'm really stumped as to a possible cause or further troubleshooting ideas. Any tips?

---

