---
title: "Winmail.dat attachment on Evolution"
date: 2010-10-21
forum: Desktop Environments
---

### Post by cirobr on 2010-10-21
Hello,

I have a clean Lucid install on a notebook, running with two different users. There are certain e-mails sent from MS-Outlook that are received by one user with a "TNEF winmail.dat" attachment. The very same e-mail is received by the other user correctly, i.e., with the proper attachment (PDF, XLS, etc), or even with no attachment. Both users get emails from same IMAP provider/server.

This leads me to believe that the way Evolution is configured by the two users is different from each other - unfortunately I couldn't find that.

Any help is greatly appreciated.

Thanks.

---

### Post by oregonbob on 2010-10-21
One user has html mail configured, the other has text. Some systems attach a text version when html is sent.

---

### Post by cirobr on 2010-10-21
> **oregonbob said:**
> One user has html mail configured, the other has text. Some systems attach a text version when html is sent.

If you mean menu Edit > Preferences > HTML Messages tab, the entire configuration for both is exactly the same. Specifically, "show HTML if present" as well.

---

### Post by cirobr on 2010-10-25
Hello,

Issue seems to be even worse. I've completely removed the user that shows this bad behavior on Evolution (confirmed that folder /home/user was completely eliminated) and created it again. Evolution account was created from scratch (i.e. not from a backup file). Problem persists.

The other user account at the same machine performs properly.

Thanks for posting hints.

---

