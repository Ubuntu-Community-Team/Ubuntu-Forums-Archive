---
title: "how to uninstall a startup script that I installed?"
date: 2008-12-18
forum: General Help
---

### Post by yinglcs2 on 2008-12-18
Hi,

I follow this step to install script in my ubuntu:
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

But my question is: how to uninstall a startup script that I installed?

Thank you.

---

### Post by iponeverything on 2008-12-19
Where "script" is your script.

```
sudo update-rc.d -f script remove
```

---

