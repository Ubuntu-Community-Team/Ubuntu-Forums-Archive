---
title: "rsync woes"
date: 2009-03-16
forum: General Help
---

### Post by nunki on 2009-03-16
I am trying to do a simple backup of my home directory into my backup directory on my desktop. Im on my laptop running xubuntu intrepid. Rsync will not exclude hidden files no matter what I type. The command I am using is:
```


rsync -av --progress --exclude=¨.*/¨ --exclude=¨.*¨ <my source dir> user@mydesktop::backup/dest

```

No hidden files or directories are excluded. I have tried multiple different combinations of the exclude directive to no avail. Any suggestions?

---

### Post by jonobr on 2009-03-16
If I recall rightly, the exact syntax should be 

```
--exclude="- *."
```

and you should be able to remove

```
--exclude=¨.*/¨ --exclude=¨.*¨
```

hope that works, and remember to test before deploying!

---

### Post by nunki on 2009-03-16
> **jonobr said:**
> If I recall rightly, the exact syntax should be 

```
--exclude="- *."
```

and you should be able to remove

```
--exclude=¨.*/¨ --exclude=¨.*¨
```

hope that works, and remember to test before deploying!

Thanks, that seems to have done the trick. Syntax is a bit non-intuitive, but it works.

---

### Post by jonobr on 2009-03-16
agreed, 

good to hear its running!

---

### Post by philinux on 2009-03-16
You might want to give gadmin-rsync a go. It's in the repos.

---

### Post by jonobr on 2009-03-16
philinux

if that name is a play on the name of the lead singer of thin lizzy and you are a fan , that's hilarious,
If not , then its still amusing to me............


I need to lie down now...........


;)

---

