---
title: "Can't Get Plank To Run At Startup"
date: 2021-01-07
forum: Desktop Environments
---

### Post by O)9(yo&amp;# on 2021-01-07
I'm running 16.04 with default Unity desktop. I recently installed Plank. I like it, but I have to run it every time I start up. I tried adding it to Startup Applications, using the following:

Name:        Plank
Command: /user/bin/plank
Comment:  Dock

That did not work. Do I need to use the terminal? I have seen tutorials for doing so, but thought I'd ask here first, as I may just need to change some of the above info.

Thanks,  Mike

---

### Post by Frogs Hair on 2021-01-07
Try changing the command to ```
plank
```

---

### Post by deadflowr on 2021-01-07
Change user to usr
Unless you created a /user directory, it does not exist.
But /usr does.

Frog's Hair's suggestion should also work.

---

### Post by O)9(yo&amp;# on 2021-01-07
Thanks guys, changing /user/ to /usr/ did it. Good eye, deadflowr!

---

### Post by SantaFe on 2021-01-10
> **michael_diemer said:**
> Thanks guys, changing /user/ to /usr/ did it. Good eye, deadflowr!

I guess that makes deadflowr a Power USR then! :D

---

