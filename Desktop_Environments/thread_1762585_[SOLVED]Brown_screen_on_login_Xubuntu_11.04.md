---
title: "[SOLVED]Brown screen on login Xubuntu 11.04"
date: 2011-05-19
forum: Desktop Environments
---

### Post by Mortesins93 on 2011-05-19
Hello,
I just installed Xubuntu 11.04 and all of a sudden I got a brown screen when I logged in that made my desktop unvisible (everything else worked fine). After a while I understood it was a problem with nautilus which I installed because I thought I needed to for Dropbox. So this is what I did and it worked:
```
 sudo apt-get purge nautilus
```
And everything turned back to normal.

---

### Post by Kraft4406 on 2011-05-24
You, sir, are a genious! This was the exact issue I was having :) Thanks for the help :)

---

### Post by Mortesins93 on 2011-05-25
Well, I am really glad to help, in fact if it wasn't for that I wouldn't have done this thread.

---

