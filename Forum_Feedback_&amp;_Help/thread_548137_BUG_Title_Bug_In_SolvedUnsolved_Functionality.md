---
title: "BUG: Title Bug In Solved/Unsolved Functionality"
date: 2007-09-10
forum: Forum Feedback &amp; Help
---

### Post by Jamie Jackson on 2007-09-10
There is a bug in the forums software: HTML entities in thread titles are unnecessarily escaped in marking a thread "solved" or "unsolved"

Steps to reproduce:
Create a thread with double-quotes in the title, such as
```
Mount Windows "Drive Letter" "Shares" via Samba
```

Mark the thread "Solved," and the quotes in the thread title are *visibly* escaped.

For fun, you can toggle the thread from solved to unsolved, and vice-versa a few times to completely annihilate the title (both functions affect the title).

Here's what I end up with when I mark that thread Solved & Unsolved:
```
Mount Windows &amp;amp;quot;Drive Letter&amp;amp;quot; &amp;amp;quot;Sha
```

Moderator: When (or possibly before) this is fixed, could you please repair my illegible [thread]("http://ubuntuforums.org/showthread.php?t=547784") title?

---

### Post by bapoumba on 2007-09-11
Hello!
I fixed the title. An admin is required to fix the rest ;)

---

### Post by Jamie Jackson on 2007-09-11
Thanks!

Also, I just noticed that I didn't paste in the screwy title in the second code block. I've done so now.

---

### Post by matthew on 2007-09-11
> **Jamie Jackson said:**
> Thanks!

Also, I just noticed that I didn't paste in the screwy title in the second code block. I've done so now.Thanks! I read it the first time and thought, "What?!"

We will look into it.

---

