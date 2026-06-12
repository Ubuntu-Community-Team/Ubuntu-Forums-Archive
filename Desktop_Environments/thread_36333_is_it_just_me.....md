---
title: "is it just me....?"
date: 2005-05-22
forum: Desktop Environments
---

### Post by vegetto on 2005-05-22
find files/folder in kde(kfind) seems to never work. i want search with index files which gnome search takes only a few seconds but it takes ages in kfind. how do i enable index files in kfind. i ticked the checkbox but still it takes ages and i get angry and close it , this i when it totaly crashes.

---

### Post by bored2k on 2005-05-22
[QUOTE=vegetto]find files/folder in kde(kfind) seems to never work. i want search with index files which gnome search takes only a few seconds but it takes ages in kfind. how do i enable index files in kfind. i ticked the checkbox but still it takes ages and i get angry and close it , this i when it totaly crashes.[/QUOTE]
 I never liked find tools. I suggest kiolocate:
[http://www.kde-look.org/content/show.php?content=17201](http://www.kde-look.org/content/show.php?content=17201)

If you like locate.. youll like kiolocate.

---

### Post by sancho on 2005-05-24
I don't remember it ever working right in any distro.  

I usually do this from terminal 


```

find / ".*hi.*"

```

the /  means the root file system; search the whold drive.   The .* are regular expressions.  Meaning match any character before or after.    So the script above would find  files name "hi" and "chipset" .  It can get alot more complex and fun but thats my simple alternative to KDEs brok find feature.

---

