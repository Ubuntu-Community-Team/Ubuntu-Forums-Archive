---
title: "Update Manager Hangs"
date: 2008-06-11
forum: Desktop Environments
---

### Post by Tevya on 2008-06-11
I just upgraded to 8.04 from 7.10 and I have not been able to get the firefox (or any) upgrades to install. :(  The update manager just hangs and hangs.  I let it go for some hours without any progress.  Eventually I had to kill it by logging off, even rebooting.

Any ideas how I can get more information on what's happening here?

Has anyone else seen these problems?  BTW, I am operating with minimal memory (376Mb).

Thanks for the help.

---

### Post by ibutho on 2008-06-11
Hi.

Its the second time in a day that I have seen such a post. Try Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by Tevya on 2008-06-12
That did the trick. I am now all up-to-date.  Thank you! :)

---

### Post by paechan on 2008-06-12
That helped me out aswell, but it doesn't really remove the problem. I basically can't start any administrator application outside the terminal. At least I can now update, and hopefully a fix for this problem will be in one such update.

---

