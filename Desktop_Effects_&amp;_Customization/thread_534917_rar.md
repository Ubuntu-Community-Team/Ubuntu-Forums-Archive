---
title: "rar"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by turtle02 on 2007-08-25
i cannot open .rar files 

i have already tried sudo apt-get install rar and it give me this

Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

any help?

---

### Post by hyperair on 2007-08-25
Go to System->Administration->Software Sources. In the first tab, check all the checkboxes. Then click close. When it asks you to reload, allow it to reload. Then you can install rar through "sudo apt-get install rar"

---

### Post by turtle02 on 2007-08-26
I did as you said but it gave me the same message as before.

---

### Post by hyperair on 2007-08-26
Ok how about this, attach a screenshot of your Software Sources window to your next post so I can take a look at it.

---

### Post by kellemes on 2007-08-26
You need unrar

---

### Post by Dark Star on 2007-08-26
```
sudo apt-get install unrar
``` Have you tried this ? :? This add  .rar privilidge to default archiver ;)

---

### Post by turtle02 on 2007-08-26
I got it working in software properties i had to click add and check the other two boxes, let it update, and then go back in and checkmore boxes.

thanks for pointing me in the right directions.

i have anew problem now i need to be able to view .chm files

---

### Post by kellemes on 2007-08-26
> **turtle02 said:**
> I got it working in software properties i had to click add and check the other two boxes, let it update, and then go back in and checkmore boxes.

thanks for pointing me in the right directions.

i have anew problem now i need to be able to view .chm files

Mark this post as SOLVED please..
And start a new thread with your new question.

---

### Post by turtle02 on 2007-08-26
how to i change status to solved.

---

### Post by kellemes on 2007-08-26
> **turtle02 said:**
> how to i change status to solved.

Just edit the title..
Change it to something like "rar (SOLVED)"
Thanks.

---

### Post by Rupertronco on 2007-08-26
Click the edit button on your first post, and viola.

---

