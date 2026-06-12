---
title: "Default file permissions for everything create in a shared folder"
date: 2009-06-04
forum: General Help
---

### Post by jonboy99 on 2009-06-04
Hi folks.

I have created a shared folder in ubuntu. I wish anything **subsequently** created in that folder to have the file permissions 777.
I have run the command ```
chmod ~/sharedfolder
``` on that folder, so it is now read and writeable by everyone. However if I now create a subfolder in that directory, either from the terminal using

```
mkdir ~/sharedfolder/subfolder
```

or using the nautilus file manager then subfolder has the permission 744.

I imagine I need to edit a config file somewhere to change default permissions for anything created in that particular parent folder - is this possible?

What i DON'T want to have to do is run the chmod command on every file or subfolder I create there.

Thanks.

---

