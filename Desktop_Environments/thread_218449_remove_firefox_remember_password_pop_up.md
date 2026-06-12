---
title: "remove firefox remember password pop up"
date: 2006-07-18
forum: Desktop Environments
---

### Post by thekiller on 2006-07-18
I was wondering if anyone knows how to remove Mozilla firefox's remember password pop up. I want to set it up in such a way that it remembers typed passwords by default instead of having it ask me whether to remember one or not.

Thanks in advance.

---

### Post by aysiu on 2006-07-18
I don't think this can be done. I looked in about:config and also browsed some extensions relating to passwords...

---

### Post by thekiller on 2006-07-18
There is an option "security:ask_for_password" when you go into about:config and I have a feeling if one knows a specific value for enabling/disabling the pop up, it can be done.

Thanks for a prompt response anyway.

---

### Post by aysiu on 2006-07-18
I thought that was more for the master password and not for individual ones...

---

### Post by thekiller on 2006-07-18
I am not sure about that, you might be right !:-k

---

### Post by aysiu on 2006-07-18
What I would do, to be safe, is...

1. Close Firefox
2. ```
cp -R ~/.mozilla ~/.mozilla.backup
```
3. Re-launch Firefox. Then play around with the *about:config* settings to your heart's content. 
4. Once you find the exact setting you want, close Firefox again.
5. ```
mv ~/.mozilla ~/.mozilla.old
mv ~/.mozilla.backup ~/.mozilla
```
6. Restart Firefox and do your tweaking on the "real thing."

---

