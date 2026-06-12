---
title: "Is there a way to UNhide directories?"
date: 2009-01-19
forum: General Help
---

### Post by xeddog on 2009-01-19
Personally, I really don't like the way Linux handles hidden directories.  In most cases I don't really see any need for them to be hidden in the first place.  I am constantly having to turn on/off the "View hidden files" option in the file managers.  You can't simply change their status from hidden to unhidden without (most likely) screwing up your application.  I have one or two directories that I would like UN-hidden, but simply renaming them without the leading "." certainly isn't the answer.  One application just wouldn't run without the original with the leading ".", and the other one simply created a new one.

Any ideas???

xeddog

P.S.  I am running Ubuntu Intrepid, but have tried Kubuntu Intrepid and had the same issues.  Didn't use Kubuntu very long though.

---

### Post by dagnabit dang doohickey on 2009-01-19
Create a symlink for the hidden files/directories.

```
ln -s *hidden_file filename_without_leading_dot*
```

---

### Post by xeddog on 2009-01-19
Thanks for the reply.  I will probably have to use links, but the issue I have with links is that if the target is deleted the link is not.  You then have to manually go and delete the links.  Granted this isn't a major problem but it is a pita.  Especially for someone like me who just might be borderline OCD and wants to keep a clean system.  :-)  I was hoping for something a little "cleaner" that would not take extra manual steps.

xeddog

---

### Post by Lars Stokholm on 2009-01-19
Linux doesn't handle hidden directories - Nautilus (File Browser) does. If you don't need it, disable it: Edit > Preferences > Views > Show hidden and backup files.

---

### Post by James_mtl on 2009-01-19
A simple CTRL-H would do the trick to in Nautilus :-)

---

### Post by xeddog on 2009-01-19
Lars Stokholm and James_mtl - the obvious problem with that option is that now you have a jillion or two files/directories that you don't want/need to see.  I currently have 30 or 40 (or more?) hidden directories and I just want 2 or 3 or 4 of them "un" hidden.  I guess I can just add that to the list of things that I would like to see changed or improved in the Ubuntu file manager. 

xeddog

---

### Post by adamlau on 2009-01-19
Ctrl+h works to do the same in Thunar as well :) .

---

### Post by dagnabit dang doohickey on 2009-01-19
If dangling symlinks are of concern, I suppose you could create a cron job to remove the danglers. The [readlink]("http://linux.die.net/man/1/readlink") command will come in handy for this task.

---

