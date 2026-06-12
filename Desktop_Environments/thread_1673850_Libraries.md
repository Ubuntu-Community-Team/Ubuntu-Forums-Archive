---
title: "Libraries"
date: 2011-01-23
forum: Desktop Environments
---

### Post by kainalu on 2011-01-23
Is there a way to combine multiple folders into one "folder" similar to the way that Windows7 does Libraries? That way movies, for instance, would be able to be distributed on multiple drives, but appear in one place, when wanted. sort of like mounting multiple folders on on one mount point.

---

### Post by 3Miro on 2011-01-23
Check symlink, "ln -s"

```
man ln
```

---

### Post by kainalu on 2011-01-23
EDIT: 

3Miro, I tried what you said, using asterisks to indicate contents instead of linking the whole folder, works great. Thanks for the help.

---

### Post by Krytarik on 2011-01-24
> **kainalu said:**
> EDIT: 

3Miro, I tried what you said, using asterisks to indicate contents instead of linking the whole folder, works great. Thanks for the help.
That way you have to create further symlinks if you add files to those directories, considered that?

---

### Post by kainalu on 2011-01-24
Well I did, but really don't know how to get around that easily. I just made a script that will update my merge folders, then set it as a daily cronjob, with a link to it in bashrc so I can run it any time like any other command (or even make a button on my panel)

Do you have a suggestion that is more elegant? Also, as a minor side note, how can I prevent that folder from showing link badges on the files?

Thanks for the help!

---

### Post by Krytarik on 2011-01-24
It's elegant enough imo, if you like it that way. I would have made it with just symlinks to the different locations, would be sufficient for me, and is more transparent.

As for the symlink arrow, try this solution, the last post, should work, but unfortunately you will have to rename them all down the "inherits" path, open the file "index.theme" in the themes' dir with the text editor to look them up, you have to open it from within the text editor, like the .desktop-files:
[http://ubuntuforums.org/archive/index.php/t-236013.html](http://ubuntuforums.org/archive/index.php/t-236013.html)

---

### Post by kainalu on 2011-01-24
OK cool, thank you very much. Marking thread solved!

---

