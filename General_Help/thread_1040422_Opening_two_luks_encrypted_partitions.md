---
title: "Opening two luks encrypted partitions"
date: 2009-01-15
forum: General Help
---

### Post by Kissell on 2009-01-15
When I boot up Ubuntu I've got two partitions that I have encrypted...  so I have to type in two commands like "cryptsetup luksOpen /dev/sda98 VD" and enter two passphrases to unlock the two encrypted partitions before I can mount them.  

Is there a way I can pass one passphrase to unlock both partitions simultaneously?  If I script it, i still have to enter the passphrase twice even if I make it the same on both partitions, because cryptsetup sees it as unlocking two distinctly different devices.

---

### Post by Kissell on 2009-01-15
oh, and I do want to use a passphrase and not a keyfile or anything else, because i trust my head more than the physical or digital world.  I know I won't forget and I know nobody can get in there except me.

---

### Post by Nostalos on 2009-01-15
So use your passphrase to unlock the first volume which contains the keyfile for the 2nd volume.

I realize that you said you did not want to use a keyfile, but if a password is good enough to protect your first volume, would it not be sufficient to protect the key for the 2nd as well?

---

### Post by hangfire on 2009-01-15
> **Kissell said:**
> Is there a way I can pass one passphrase to unlock both partitions simultaneously?  If I script it, i still have to enter the passphrase twice even if I make it the same on both partitions, because cryptsetup sees it as unlocking two distinctly different devices.

Yes. I have been using this method for several months. It uses my login password to decrypt the home partition. It generates a new swap password each time, since swap data is disposable between boots.

[http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

-HF

---

