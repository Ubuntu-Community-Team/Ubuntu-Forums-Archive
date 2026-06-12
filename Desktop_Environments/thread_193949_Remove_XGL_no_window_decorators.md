---
title: "Remove XGL no window decorators"
date: 2006-06-10
forum: Desktop Environments
---

### Post by mthaddon on 2006-06-10
Hi Folks,

I've tried out XGL and have found just a few things I'm not quite happy with yet (but very hopefully for a few months down the line). I'm trying to revert back to non-XGL by removing /etc/gdm/gdm.conf-custom, and commenting out all the lines in my xgl.sh script.

Problem is I now have no XGL (good) and no window decorators (bad). How do I restore those?

Thanks, Tom

---

### Post by userundefine on 2006-06-10
What do you mean by "no window decorators"?  Toolbars on top of windows and such?  If so, do
```
$ metacity --replace
```

---

### Post by mthaddon on 2006-06-11
Thanks. Just after posting this I ran "metacity" and that seemed to work.

Cheers, Tom

---

