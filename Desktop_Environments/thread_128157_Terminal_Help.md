---
title: "Terminal Help"
date: 2006-02-10
forum: Desktop Environments
---

### Post by BillyCreek on 2006-02-10
After a command I get a question mark. Then nothing else happens and I can't get back to the orginal prompt.
It doesn't matter what command or anything.

---

### Post by dcstar on 2006-02-10
[QUOTE=BillyCreek]After a command I get a question mark. Then nothing else happens and I can't get back to the orginal prompt.
It doesn't matter what command or anything.[/QUOTE]
Tell us exactly what you are doing, and exactly what is displayed.

---

### Post by BillyCreek on 2006-02-10
I am trying to edit /etc/hosts using the ed command

---

### Post by jrib on 2006-02-11
why!?

use nano if you don't know how to use ed and need something in the terminal

---

### Post by kabus on 2006-02-11
> After a command I get a question mark. Then nothing else happens and I can't get back to the orginal prompt.

That's just how ed works. :) 
Hit Control-D to get out of it.
If you absolutely have to use ed take a look at the man page, but you'd make your life a lot easier by using a less archaic editor like nano or vim.

---

### Post by alfonz on 2006-02-11
your better off using nano as jason stated or gedit.

```
sudo nano(or gedit) /etc/host
```

---

### Post by BillyCreek on 2006-02-11
Thanks

---

