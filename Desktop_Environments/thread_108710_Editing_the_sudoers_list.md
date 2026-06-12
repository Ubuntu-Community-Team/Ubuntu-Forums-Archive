---
title: "Editing the sudoers list?"
date: 2005-12-26
forum: Desktop Environments
---

### Post by rekabbelac on 2005-12-26
I just installed Kubuntu 5.10 using the expert setup mode, and now I am not able to use sudo within KDE, just in the Terminal. This problem appears here:
[http://ubuntuforums.org/showthread.php?t=91295]("http://ubuntuforums.org/showthread.php?t=91295")
as well, but I'm not sure how to edit the list in question.

---

### Post by 11hjpphty76lkjj on 2005-12-26
I'm assuming you already tried this, but can you just type su and then the root password?

---

### Post by rekabbelac on 2005-12-26
I can do that at the command line, but I'd like to do it from within KDE, like Kubuntu was designed to do.

---

### Post by 11hjpphty76lkjj on 2005-12-26
If you can use su, then you should be able to use su and edit the sudoers files, and then you should be able to sudo.

Aye?

---

### Post by rekabbelac on 2005-12-26
That is correct. I'm just notsure where the sudoers file is stored.

---

### Post by enlightened on 2005-12-26
sudoers file is here --> /etc/sudoers

---

### Post by Xian on 2005-12-26
[QUOTE=rekabbelac]That is correct. I'm just notsure where the sudoers file is stored.[/QUOTE]

You should never edit the sudoers file with a common text editor by opening it's location path. There are many inherit problems with this method. If you use the proper method you have no need to even find the location of the actual file.

Open a terminal and use the visudo command:

```
$ su
# visudo
```

---

