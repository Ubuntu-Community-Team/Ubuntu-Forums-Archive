---
title: "Discussion - Full_Disk_Encryption_Howto_2019"
date: 2021-03-02
forum: Documentation and Community Wiki Discussions
---

### Post by gyari on 2021-03-02
Hello!

First of all, thanks for [tj]("https://launchpad.net/~tj") for the awesome [tutorial]("https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019")!

And i have a question about the tutorial, maybe someone can help me.

1. After rebooting it always ends in grub failer:
[I]"Booting from Hard Disk...
Attempting to decrypt master key...
Enter passphrases for hd0,gpt1 (numbers):
error: access denied.
error: no such cryptodisk found.
error: disk 'cryptouuid/numbers' not found.
Entering rescue mode...
grub rescue> _"[/I]
My installation always end like this. I followed every step, except i   didn't make efi partition, because i'm using BIOS, and didn't make swap   partition either. Otherwise i followed every step, mainly copy and  paste  from the article.

Is there someone who could help me out?

Thanks any help you can provide!

---

### Post by CelticWarrior on 2021-03-02
Welcome.

A swap partition isn't required, Ubuntu uses a swapfile now.
If installing in BIOS mode in a GPT drive a small unformatted 'bios_grub' partition is required.

---

### Post by gyari on 2021-03-02
Thanks for your reply and the heads up on swap in Ubuntu!
As written in the tutorial i made a 2MB size & ef02 type partition. It was not formatted at all.

---

### Post by gyari on 2021-03-03
So now i tried that i just followed every step in the tutorial. Copy paste everything, needed or not. Still after reboot it ends with grub fail detailed in the first comment. Maybe the tutorial won't work with 20.04?

---

### Post by gyari on 2021-03-03
I just installed Ubuntu 18.04.5 with this method. It just worked. So it  seems the tutorial somehow not compatible with 20.04. Is there anybody  who could tell me why is it not compatible with 20.04?

---

