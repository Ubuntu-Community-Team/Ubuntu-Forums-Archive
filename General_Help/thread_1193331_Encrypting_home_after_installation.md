---
title: "Encrypting /home after installation"
date: 2009-06-21
forum: General Help
---

### Post by malfist on 2009-06-21
Hello, I just installed 9.04 but forgot to use the alt CD to encrypt everything, and I was wondering if I could encrypt my /home partition after installation. Does anyone know how to do it?

---

### Post by linuxloon on 2009-06-21
Did you install with LVM ? Did you install with /home a separate file system ?

Not sure on the procedure. It should be possible but it my be a little trick to do after the install.

you could you also use encfs to create an encrypted dir in your home dir. just could'nt use it to encrypt the whole home dir.

---

### Post by starcraft.man on 2009-06-21
Not an expert on this, but I think 2 ways. One is go one folder up and right click on your username (or the home folder itself) and select encrypt. I think that will prompt you through a series of windows, fairly straightforward, you'll need a key to encrypt with, and a password to get into it. The other alternative is truecrypt, that's a professional encryption program though, military grade. Truecrypt isn't availabe in repos to my knowledge, google their site and you can get a deb.

Either way, make sure you know what your doing and remember the password or else your data is lost. Just fair warning.

Edit:On a side note, why encrypt all of Home instead of just creating a small folder somewhere and filling it with your important docs to encrypt?

---

### Post by Soul-Sing on 2009-06-21
1) dm-crypt with LUKS.
2) truecrypt

---

### Post by linuxloon on 2009-06-21
Two How-To's from the net that should work.

[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

---

### Post by cmost on 2009-06-21
May I caution you to be careful encrypting your /home directory.  Many people look at encryption as something they should do simply because they can.  Ask yourself: "do I really need this?"  "Who has access to my system, realistically, other than me?"  If you believe you have sufficient reasons to encrypt your files then proceed at your own risk.  Some people have encrypted their home directories only to lose access after upgrading from one version of Ubuntu to the next.  Others have reported problems accessing encrypted partitions after reinstalling their systems from scratch.  I would caution against encrypting your files for obvious reasons, unless you really need it.  If something goes wrong, you won't have access to your files unless you have an unencrypted backup somewhere.  Good luck!

---

### Post by blueridgedog on 2009-06-21
> **malfist said:**
> Hello, I just installed 9.04 but forgot to use the alt CD to encrypt everything, and I was wondering if I could encrypt my /home partition after installation. Does anyone know how to do it?

Given that you just did it, the easiest way would be to reinstall.

---

### Post by malfist on 2009-06-21
it would be easier to reinstall again, but the installer, as far as my knowledge goes does not permit separating / and /home when encrypting. I've used full drive encryption for quite some time, but I think for a speed increase I'd rather have / unencrypted (or put it on an SSD). Truecrypt isn't in the repo's, but I can compile it, it's what I use for my other harddrives. I don't think it's setup with LUKS.

---

