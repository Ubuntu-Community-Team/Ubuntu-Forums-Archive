---
title: "Migrating from ext3"
date: 2009-02-13
forum: General Help
---

### Post by swordfishRU on 2009-02-13
Hi, folks!

It's possible to migrate from ext3 file system to some encrypted file system in an already installed system?

Thnx!

---

### Post by kidders on 2009-02-14
Yes ...

You basically have two choices. If you're happy to encrypt only the parts of your filesystem that *need* it (eg /var or /home), you can make the move live ... if you know what you're doing. Alternatively, to encrypt your entire filesystem, you'll need to boot into another Linux OS, and do it from there.

I would probably opt for partial encryption, personally. Arguably, it's safer, performs better, and can be added to a pre-existing install without having to reboot. Encrypting an entire filesystem is far easier if you're not confident tinkering with Linux systems though.

I hope that helps.

---

### Post by swordfishRU on 2009-02-16
Thanks you, kidders!

If I choose a partial encryption, how I can make this one?

---

### Post by kidders on 2009-02-18
You should be able to follow (more or less) any howto that discusses moving bits of your system to another filesystem. For example, to encrypt /home, you'd need to ...[LIST]
[*]Terminate any major services, like X, that might try to access the directory you want to encrypt.
[*]Double-check that there are no open file handles (eg **lsof | grep /home**).
[*]Rename the directory & create a replacement.
[*]Create your encrypted filesystem & mount it.
[*]Copy your files into the new filesystem (eg **sudo cp -dpR /home.old/* /home**).
[*]Alter your /etc/fstab to have the new /home mounted at boot.
[/LIST]

After a day or two, once you're sure the changes are stable, you could remove the unencrypted copies of your data. You may want to **shred** them (rather than just running **rm**), to make them harder to recover.

---

