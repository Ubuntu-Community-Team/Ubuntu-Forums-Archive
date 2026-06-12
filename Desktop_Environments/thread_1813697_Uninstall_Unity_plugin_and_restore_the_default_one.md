---
title: "Uninstall Unity plugin and restore the default one"
date: 2011-07-28
forum: Desktop Environments
---

### Post by kannanjagadeesan on 2011-07-28
Hi Experts,

I installed Ubuntu Unity Plugin in my Computer(Ubuntu 10.10). Now I do not like the feel of it and I want to remove it and restore the old default one.

Can you provide me the steps to perform it?

Waiting for your advice,
With Kind Regards,
Kannan

---

### Post by Russ.pinkslippa on 2011-07-28
Hi,

I'm not an expert but if you installed it using apt-get you can remove the package a similar way 

```
apt-get --purge remove <package>
```

Don't know about restoring the old one though, it might not automatically go back to the old one once you remove unity..

You could, on the login screen, switch to gnome then do the above, but i haven't tried it myself. 

Someone else might have a better idea though.

Regards,

Russ :)

---

