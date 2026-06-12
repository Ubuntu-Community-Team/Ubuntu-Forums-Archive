---
title: "Change display manager?"
date: 2014-05-25
forum: Desktop Environments
---

### Post by JamesMiller93 on 2014-05-25
Hello, 

I recently installed Ubuntu 14.04 and got the latest version of gnome. However, I must have selected my computer to boot using the gnome display manager as the default display manager. How would I set LightDM back as the default display manager?

Thanks.

---

### Post by JamesMiller93 on 2014-05-25
Nevermind, figured it out.

---

### Post by deadflowr on 2014-05-27
> **JamesMiller93 said:**
> Nevermind, figured it out.

Could you give us a hint as to how you figured it out?

---

### Post by JamesMiller93 on 2014-06-01
Sorry for the late reply but I just had to open the terminal and type:

sudo dpkg-reconfigure lightdm

And then you follow the prompt. Nice and easy!

---

