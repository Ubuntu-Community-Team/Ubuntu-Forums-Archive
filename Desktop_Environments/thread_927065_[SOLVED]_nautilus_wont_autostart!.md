---
title: "[SOLVED] nautilus wont autostart!"
date: 2008-09-22
forum: Desktop Environments
---

### Post by Darkened35 on 2008-09-22
Hi, i have this HUGE problem, I was following How to Geeks guide to show trash on the desktop, i tried to change the trash name and nautilus wont autostart now, I cant browse my files, but i can open apps fine, when i type gksudo nautilus it boots it in roots, but i like my desktop, I have no icons since i tweak Ubuntu. thanks for your help, 
Saryth:KS

---

### Post by anotherdisciple on 2008-09-22
hmm... try this...

Hit Alt+F2 and type:

```
gconf-editor
```

Then, navigate to:

apps-> nautilus-> desktop

...and try to change the name of the trash back to "Trash"

Let me know if it worked.

PS- You may need to log out and log back in again.

---

### Post by Darkened35 on 2008-09-23
the thing is, that the trash_icon_name setting is a integer value, But thing is nautilus is there, just wont load my stuff and if i do sudo nautilus it loads roots desktop...
 Saryth
EDIT: IT WORKED!! Thanks anotherdisciple, when i went to the key, show trash icon  was ticked so i set trash name to 0 and unticked show trash and it worked!

---

### Post by anotherdisciple on 2008-09-23
> **Darkened35 said:**
> the thing is, that the trash_icon_name setting is a integer value, But thing is nautilus is there, just wont load my stuff and if i do sudo nautilus it loads roots desktop...
 Saryth
EDIT: IT WORKED!! Thanks anotherdisciple, when i went to the key, show trash icon  was ticked so i set trash name to 0 and unticked show trash and it worked!

Good! I forgot about it being an integer... that's confusing isn't it?

By the way...Can you mark this thread as solved please?

---

