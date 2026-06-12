---
title: "Whole disk encryption Questions"
date: 2009-02-02
forum: Desktop Environments
---

### Post by stormzen on 2009-02-02
I have a number of questions regarding disk encryption.  What I need to set up is an encrypted dual-boot environment, preferably with PGP WDE/Windows XP (because this is the supported standard here where i work) and whatever Linux will use.  I have one hard drive with which to do this, a 500 GB drive.  ( Which is a limitation of the laptop. )

I'm considering options such as TrueCrypt, LUKS, and loop-AES.  I'm not sure how I would do full disk encryption (root, swap, etc) with TrueCrypt.  LUKS looks like it is supported, even by GUI with Intrepid, however, I found a reference not to use it here: [http://ubuntuforums.org/archive/index.php/t-401222.html](http://ubuntuforums.org/archive/index.php/t-401222.html), which says:

---

It's recommended NOT to use cryptoloop, LUKS, dm-crypt in kernels prior to 2.6.10, bestcrypt, truecrypt versions prior to 4.1, or loop-AES in single-key mode.

The recommended full disk encryption solution is loop-AES ([http://loop-aes.sourceforge.net/](http://loop-aes.sourceforge.net/)) in multi-key mode with encrypted swap! This achieves maximum available security for your data. Available ciphers are AES, Blowfish, Serpent, and Twofish.

---

Implied in the description of what I need to have working is that Windows / PGP WDE would need to be set up first, consuming one primary partition on the drive.  This may warrant consideration, it may not, if LUKS is now a more viable alternative and/or the process can work with extended partitions...  I'm not sure how to even set up a dual boot with PGP WDE/Windows...

Thanks!

---

