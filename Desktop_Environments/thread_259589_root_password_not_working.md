---
title: "root password not working"
date: 2006-09-17
forum: Desktop Environments
---

### Post by alexbOrsova on 2006-09-17
[LEFT]Hello everyone, I'm back. After lots and lots of meticulous work, I've managed to install Ubuntu LTS on my computer. However, I now have another problem. I wanted to update my applications using the Update Manager but the prompt window  (that asks for your root passwd) doesn't accept my password. I created it with
```

sudo passwd root

```
a few days ago. What do I do?

P.S. Yes, I did run a search first. ;)
[/LEFT]

---

### Post by Crayoneater on 2006-09-17
the prompt window is asking for your user account password i believe, not the root account password...ubuntu doesn't have a root account by default anyway....

---

### Post by ciscosurfer on 2006-09-17
The password you set during your install is what you should've used as your password when prompted (for any administrative task)...this password is placed into your sudoers file.  Try using the password you set during install -- you don't need to enable your root account or set a password in this situation.  There are other (very specific times) when it might be advantageous to enable root, but in your case and in most cases, it does not need to be enabled.

---

### Post by ciscosurfer on 2006-09-17
> **Crayoneater said:**
> the prompt window is asking for your user account password i believe, not the root account password...ubuntu doesn't have a root account by default anyway....

Ubuntu does have a root account, it's just not enabled by default.

---

