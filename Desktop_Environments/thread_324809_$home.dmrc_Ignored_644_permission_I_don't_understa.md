---
title: "$home/.dmrc Ignored? 644 permission? I don't understand. XFCE"
date: 2006-12-24
forum: Desktop Environments
---

### Post by Drezliok on 2006-12-24
Ok, I messed something up, which isn't bad if I can learn from it.

While messing with Samba and a howto I did something that made sense to me at the time.
I used this command on my home directory

sudo chmod 0777 home/drezliok

I now know that it was not a good idea

Now when I log in it throws an error that tells me that my .dmrc file is being ignored.

On top of that I can no longer access much of the system menu items.

Please help me fix my stupidity and tell me why it's this way, so I can learn from this mistake.

Thankyou
Drezliok

---

### Post by taurus on 2006-12-24
/home/drezliok/.dmrc should have a permission of -rw------...

```
chmod 600 ~/.dmrc
```

---

### Post by Drezliok on 2006-12-24
I tried that command, the error persists.

I really screwed this up, I'd hate to have to reinstall. I just started using my current as my main Operating System.

---

### Post by taurus on 2006-12-24
That's why you need to be real careful with the **sudo** command!

---

