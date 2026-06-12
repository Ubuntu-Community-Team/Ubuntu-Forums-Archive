---
title: "Its a Newbie:&gt;&gt; Firefox crash..&lt;&lt;"
date: 2005-12-14
forum: General Help
---

### Post by Cromie on 2005-12-14
Just playing around installing some apps with automatrix, and now firefox wont load at all. How can i fix this browser ? Opera still works as always. But  always having issue's with the Firefox browser.. its version 1.07...](*,)

---

### Post by aysiu on 2005-12-14
Have you tried this? ```
mv ~/.mozilla ~/.mozilla_backup_copy
firefox
```

---

### Post by Cromie on 2005-12-14
that works but when i hit the button i get this:

"/usr/share/ubuntu-artwork/home/index.html cannot be found. Please check location and try again.."

---

### Post by aysiu on 2005-12-14
[QUOTE=Cromie]that works but when i hit the button i get this:

"/usr/share/ubuntu-artwork/home/index.html cannot be found. Please check location and try again.."[/QUOTE] That's fine. It just means it's looking for the homepage there. If you change the homepage to something else, it should be good (and not give you that warning).

If Firefox works fine, then you can just import your bookmarks from the backup folder and you're set.

The bookmarks in your backup folder are probably in ~/.mozilla_backup_copy/firefox/*gobbledygook*.default/bookmarks.html

My "gobbledygook," for example, is *7jfpfska*.

---

### Post by Cromie on 2005-12-14
that worked , Thanks

But another Q,    what made this happen ?

---

### Post by aysiu on 2005-12-14
[QUOTE=Cromie]
But another Q,    what made this happen ?[/QUOTE] No idea. Firefox is buggy that way. I've seen Firefox profiles get corrupted on Windows, Mac, and Linux. Sometimes it has to do with installing and uninstalling too many extensions and themes. Sometimes, it's just random.

---

### Post by Cromie on 2005-12-14
True there about Windows, At least there i can get around that one fine. Still learning the Terminal thing with all the commands is something i have not used in a few years.. But thats why i like the Ubuntu Forum, people are willing to help without taking your head off.. 

Thanks again Aysiu..

---

### Post by aysiu on 2005-12-14
[QUOTE=Cromie]True there about Windows, At least there i can get around that one fine. Still learning the Terminal thing with all the commands is something i have not used in a few years.. [/quote] Actually, everything I told you to do you could have done graphically if you navigated to your /home folder and pressed control-H. It's just easier for me to give you terminal commands.

> 
But thats why i like the Ubuntu Forum, people are willing to help without taking your head off.. Go, and do likewise.

---

