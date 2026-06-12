---
title: "I've lost desktop's control"
date: 2008-09-06
forum: Desktop Environments
---

### Post by Darkfirephoinix on 2008-09-06
**Hello everyone**, I am here looking for help with my Ubuntu(hardy) desktop;

A few days ago I tried to delete (send to trash or delete) some files in my desktop but it seems that my account doesn't have the permission to do that,i cant even create a folder in desktop (or download anything to that folder) I've tried to run Nautilus as root to delete the files, but the desktop appears empty, also i have tried to create a folder in nautilus as root but i cant do that.( it seems that even the root account has lost control over the desktop) I can send to trash files from other folders, the problem is only on desktop.
[I]
Edit;I forgot to mention a folder with an arrow pointing to northwest (virtual north west) is in my desktop, I don't know if this can be causing the problem[/I]

Any suggestion?_(thanks in advance)_

If my English is bad sorry, not native speaker

** c ya**

---

### Post by fornix on 2008-09-06
Please paste the output of this command
```
$ ls -l ~ | grep Desktop
```

---

### Post by Darkfirephoinix on 2008-09-06
Here is it;
> drwxr-xr-x 11 root   root   4096 2007-11-15 10:21 Desktop


---

### Post by puppywhacker on 2008-09-06
Your ~/Desktop is owned by root, so anybody else is only allowed to read, but not write. You can change back the ownership with chown

sudo chown `whoami` ~/Desktop

---

### Post by Darkfirephoinix on 2008-09-06
Thank you very much both, it worked!!
:)

---

