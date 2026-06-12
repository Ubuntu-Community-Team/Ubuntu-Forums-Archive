---
title: "deleting files in the filesystem"
date: 2009-02-03
forum: General Help
---

### Post by Jameshardy88 on 2009-02-03
Hi i know this is quite a basic question but i was wondering how do i go about deleting files in the file system (that i know i can delete) as i have lots of old themes/backgrounds etc stored in their that i want to get rid of. I don't mind using some basic terminal commands if necessary. 

Thanks for your help,

James

---

### Post by jespdj on 2009-02-03
The 'rm' command (for remove) deletes files (and directories). Type:
```
man rm
```
for a complete list of options.

---

### Post by Jameshardy88 on 2009-02-03
so for example would i type...

sudo man rm /usr/share/themes/(theme)

?

---

### Post by oldos2er on 2009-02-03
> **Jameshardy88 said:**
> so for example would i type...

sudo man rm /usr/share/themes/(theme)

?

 No. "man rm" gives you info on the "rm" command. To delete a theme, you would run ```
sudo rm -rf /usr/share/themes/whatever
```

 If you're extra cautious and want to be prompted to delete each file, run ```
sudo rm -ri /usr/share/themes/whatever
```

---

### Post by jimv on 2009-02-03
Or you can press Alt+F2 and type 'gksudo nautilus /', which should give you a Nautilus window with root access.  That way you can use the GUI to delete the files and not worry about the command line stuff.

---

### Post by Jameshardy88 on 2009-02-03
thankyou all =)

---

### Post by jerome1232 on 2009-02-03
> **jimv said:**
> Or you can press Alt+F2 and type 'gksudo nautilus /', which should give you a Nautilus window with root access.  That way you can use the GUI to delete the files and not worry about the command line stuff.

And then wonder why no disk space free's up because you are actually just moving files to your root user's trash ;).

To bypass trash hold shift while pressing delete.

---

