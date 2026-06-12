---
title: "Users and Groups"
date: 2009-04-02
forum: General Help
---

### Post by Sjeti on 2009-04-02
So I recently setup a linux machine at work, and I have a few users one the account.  I want them to be able to use sudo, etc, and I've set that up.

However, I don't want them to be able to change the root password and my password (the first two accounts set up on the computer)

But when I log in as one of them and go to users and groups, it allows them all to change the root and admin passwords.  What am I doing wrong and what do I need to change?

---

### Post by Sjeti on 2009-04-02
It turns out the root issue was because I was ssh'd onto the system as root at that time, but they are still able to access my account, the one I made at install.

---

### Post by _Purple_ on 2009-04-02
Did you manage to solve your problem? If you are still having issues, can you please clarify?

---

### Post by Sjeti on 2009-04-02
If I log on as another user, I can go to Administration > Users and Groups and change my password.  Considering that I'm supposed to be the admin of this, that isn't supposed to happen.

I'm thinking this might have something to do with the fact this was the first account made on the computer?  Maybe I forgot to reset a permission somewhere?

---

### Post by _Purple_ on 2009-04-02
Check this [link](http://ubuntuforums.org/showpost.php?p=2837552&postcount=5).

---

