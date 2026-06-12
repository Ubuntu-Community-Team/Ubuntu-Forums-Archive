---
title: "Entering LUKS passphrase for cryptdisk"
date: 2006-09-20
forum: Desktop Environments
---

### Post by charlesbrooking on 2006-09-20
Hi all,

I recently used dm-crypt with LUKS to encrypt my /home partition, and so it asks for the passphrase when booting.

To be more detailed: it displays the usual Ubuntu splash screen with scrolling messages beneath it for a while, then reverts to the raw text display, where it prompts for the LUKS passphrase, usually with other messages printed over the top, etc. You can see the prompt a few lines up, but it's quite untidy.

Is there a way to prompt for the passphrase after booting has happened, at the session login screen, for example? I realise this might be a silly question, given that access to /home might be needed to get that far, but I thought I'd ask anyway.

Thanks!

---

### Post by charlesbrooking on 2006-09-24
> **charlesbrooking said:**
> Is there a way to prompt for the passphrase after booting has happened, at the session login screen, for example?

This can be can done! See [http://deb.riseup.net/storage/encryption/dmcrypt/]("http://deb.riseup.net/storage/encryption/dmcrypt/") for notes on using pam_mount to mount encrypted partitions when starting a session. :)

Note: I also removed the lines I'd previously added to /etc/fstab and /etc/crypttab.

---

