---
title: "More apt problems"
date: 2006-02-27
forum: Desktop Environments
---

### Post by chubsmalone on 2006-02-27
I run breezy on my Dell Inspiron 1200 laptop.  I'm having a problem with apt.  I recently tried to apt-get the laptop-tools package and it hung for a very long time on the setup.  I did a ctrl + c to stop it and now I have a new problem.  

Now, when I do apt-get upgrade, I get this message.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

I did that and it still hangs.  Is there a way to remove the packages from the dpkg queue so I can move on with other installs and upgrades?  

My internet connection is good.  
\\:D/

---

### Post by zxee on 2006-02-27
Have you tried 'dpkg --purge laptop-tools' ?
Or maybe 'apt-get --fix-missing'

---

