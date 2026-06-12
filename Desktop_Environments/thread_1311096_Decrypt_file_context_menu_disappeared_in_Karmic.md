---
title: "Decrypt file context menu disappeared in Karmic"
date: 2009-11-02
forum: Desktop Environments
---

### Post by don_eros on 2009-11-02
Hi there,

I just installed a fresh karmic (x86_64) and I can't figure out how to decrypt gpg encrypted files using nautilus. In 9.04 you just had to right click on a file to encrypt/decrypt it (and I'm pretty sure this was available by default), now the option has disappeared and I haven't been able to get it back.

Seahorse and gnome-gpg are installed.

I know I can use the command line tool, but the right click thingy in nautilus was really handy.

Does anyone know how to re-enable the option?

Cheers,
E

---

### Post by Polygon on 2009-11-07
Yeah, I noticed that this was gone too. I shall try to investigate on how to get it back.

~Mark

---

### Post by lyncis on 2009-11-14
Any ideas? I've searched the web but found nothing on decrypt context menu (

---

### Post by sybille on 2009-11-15
I think you need to install seahorse-plugins.

[Click here to install from your respositories]("apt:seahorse-plugins")

Then restart nautilus, for example by logging out and in again.

---

### Post by epictete on 2010-01-24
> **sybille said:**
> I think you need to install seahorse-plugins.

Yes, it works and you don't have to even relaunch Nautilus.

Thank's **Sybille**!

---

