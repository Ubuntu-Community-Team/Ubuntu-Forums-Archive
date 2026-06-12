---
title: "Naitulus default file creation mask"
date: 2009-03-14
forum: General Help
---

### Post by buldozerceto on 2009-03-14
Hello everyone,

How I can change nautilis file creation mask. Tried with umask in terminal but that only applies when I create files on the terminal.

---

### Post by ad_267 on 2009-03-14
You can edit /etc/profile and change the umask line to whatever you want. I think the default is 022, I have mine set to 002.

---

### Post by buldozerceto on 2009-03-14
That is for all users or only for me?

---

### Post by ad_267 on 2009-03-15
That would be for all users. If you want it just for you then you can add it to ~/.profile, unless you have a ~/.bash_profile or ~/.bash_login, in which case it would need to go in there.

You might have to log out and back in for this to take effect.

---

