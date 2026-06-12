---
title: "Root password"
date: 2005-11-06
forum: Desktop Environments
---

### Post by bptba93 on 2005-11-06
Is there any way to reset the root password if you can't remember it? Or is there a default password?

---

### Post by endersshadow on 2005-11-06
[QUOTE=bptba93]Is there any way to reset the root password if you can't remember it? Or is there a default password?[/QUOTE]

```
sudo passwd root
```

It will prompt you for your password (your normal user one), then ask you to put in a new UNIX password (aka your root password).  Verify it once, and you're done!

---

### Post by bptba93 on 2005-11-06
Thanks alot!

---

### Post by endersshadow on 2005-11-06
Quite welcome!

---

