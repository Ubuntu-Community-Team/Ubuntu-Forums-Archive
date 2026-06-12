---
title: "Single Folder Permissions"
date: 2007-03-27
forum: Desktop Environments
---

### Post by lsutiger on 2007-03-27
I browsed the forum, as I get more good info here than doing a google, and didn't find an answer to this question. Is it possible to have security raised on a single folder to where it would ask you for your password each time you open it, even if you are the owner?
The reason for this is I am on a laptop, which in general, get stolen more. I have some pretty important personal info on here and i this computer were to get stolen, I wouldn't want to become a victim of identity theft also...
Thanx for any input!

---

### Post by z0d on 2007-03-29
Generally speaking, no, not as far as I know. The closest I can suggest would be logging in, then mounting an [encrypted virtual filesystem via the "loop" device]("http://www.google.co.uk/search?q=mount+encrypted+loop+linux") if you're reasonably confident with such things.

This tutorial should help, provided you change the CD ISO for your encrypted filesystem: [Encrypting filesystems via the loop device]("http://linuxmonitor.net/blog/2007/03/howto-encrypt-cddvds-in-ubuntu.html").

If you're not sure about what all this means, I'd suggest the answer is to not do it. The idea of encrypting a specific folder with a passphrase isn't a long-term fix anyway, as you're likely to have the same information elsewhere (e.g. caches, shell logs, swap partition etc.).

However, it's hard to keep info really secure if an attacker has local access; the only way I can think of to definitively achieve what you're asking is mounting your root (or home) and swap filesystems at boot as encrypted devices, but this requires typing a passphrase every time you boot the machine.

If you want to do this, [FUSE]("http://www.linux.com/article.pl?sid=06/03/13/1656228") should help you out.
[This forum post]("http://ubuntuforums.org/showthread.php?page=3&t=199824") should also be helpful. [LUKS]("http://johnleach.co.uk/words/archives/2006/12/06/245/") may also be useful.

Hope this helps - z0d.

---

### Post by lsutiger on 2007-03-30
Appreciate the help! I will look into those posts.
chown -R us ./base
:D

---

### Post by lsutiger on 2007-05-07
Found the answer!
[http://users.piuha.net/martti/comp/ubuntu/encfs.html](http://users.piuha.net/martti/comp/ubuntu/encfs.html)

---

### Post by z0d on 2007-08-30
Thanks for posting the URL; hopefully this will help future searchers!
:D

---

### Post by oomingmak on 2007-08-30
> **lsutiger said:**
> Found the answer!
[http://users.piuha.net/martti/comp/ubuntu/encfs.html](http://users.piuha.net/martti/comp/ubuntu/encfs.html)
The link is dead 

:(

---

