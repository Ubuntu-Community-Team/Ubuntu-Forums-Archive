---
title: "Encrypting"
date: 2009-04-07
forum: General Help
---

### Post by majikhotline on 2009-04-07
Hello Ubuntu County,

I had an earlier ver of ubuntu server on my computer, but now I have unbuntu 8.10 desktop.  My question is how do I encrypt the Hard Drive, for the server ver I had, I put a password on it so i could boot up

thx

---

### Post by FiberOptix on 2009-04-07
> **majikhotline said:**
> Hello Ubuntu County,

I had an earlier ver of ubuntu server on my computer, but now I have unbuntu 8.10 desktop.  My question is how do I encrypt the Hard Drive, for the server ver I had, I put a password on it so i could boot up

thx

If you want full disk encryption you have look into reinstalling via the alternate cd and then restoring any files you backed up.

These threads should help:

[http://ubuntuforums.org/showthread.php?t=1012103](http://ubuntuforums.org/showthread.php?t=1012103)
[http://ubuntuforums.org/showthread.php?t=81311&highlight=backing+system](http://ubuntuforums.org/showthread.php?t=81311&highlight=backing+system)

---

### Post by bostonaholic on 2009-04-07
I've heard really good things about [True Crypt]("http://www.truecrypt.org/").  I've never used it but I know multiple people at work use it.

EDIT:  I just re-read your OP, nm.

---

### Post by FiberOptix on 2009-04-07
> **bostonaholic said:**
> I've heard really good things about [True Crypt]("http://www.truecrypt.org/").  I've never used it but I know multiple people at work use it.

Truecrypt is nice but unfortunately doesn't provide full disk encryption support for linux.

---

### Post by bostonaholic on 2009-04-07
> **FiberOptix said:**
> Truecrypt is nice but unfortunately doesn't provide full disk encryption support for linux.

What's the last one on the list?  [http://www.truecrypt.org/downloads]("http://www.truecrypt.org/downloads")

---

### Post by FiberOptix on 2009-04-07
> **bostonaholic said:**
> What's the last one on the list?  [http://www.truecrypt.org/downloads]("http://www.truecrypt.org/downloads")

You're clearly not understanding, which is why I'm surprised you're forcing this issue. 

You've shown that Truecrypt is available for Linux, which is true. While it can do lots of cool things under Linux, it does not support full disk encryption. The way most people implement FDE on Linux, and the way I recommend doing it, is to use a dmcrypt/luks setup which is provided by the alternate installer.

I use Truecrypt FDE on my windows machine and dmcrypt/luks FDE on my Ubuntu machine.

---

### Post by bostonaholic on 2009-04-07
> **FiberOptix said:**
> You're clearly not understanding, which is why I'm surprised you're forcing this issue. 

You've shown that Truecrypt is available for Linux, which is true. While it can do lots of cool things under Linux, it does not support full disk encryption. The way most people implement FDE on Linux, and the way I recommend doing it, is to use a dmcrypt/luks setup which is provided by the alternate installer.

I use Truecrypt FDE on my windows machine and dmcrypt/luks FDE on my Ubuntu machine.

It was nothing but a simple question, but thanks for the answer anyway.

---

