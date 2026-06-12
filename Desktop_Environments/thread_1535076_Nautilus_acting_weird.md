---
title: "Nautilus acting weird"
date: 2010-07-20
forum: Desktop Environments
---

### Post by nirvana21 on 2010-07-20
Greetings,

Nautilus acts very weird for me. If I try to open up the trash or open up Network via Places, nautilus dies. For example if I open Network, all my icons vanish as well as currently open directories such as home, but does not end Firefox, etc. If I open Home and browse, nothing bad ever happens. So its like half broken.

Here is the result of starting nautilus from the command line and attempting to go to smb:/// for example.

```
nautilus

** (nautilus:24529): WARNING **: Unable to add monitor: Not supported

(nautilus:24529): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:24529): WARNING **: Got GFileInfo with NULL name in smb:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:24529): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

It has been like this since I changed motherboards. Nautilus is version 2.26.2. I am running 9.04 if that matters as well.

What can I do? Should I try to remove nautilus and reinstall it, or is that a bad idea? 

Thanks!!

---

### Post by jardin_max on 2010-07-20
Not sure if this is what is causing your problems, but something to look into nonetheless.
 
[http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html](http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html)
 
Cheers

---

### Post by nirvana21 on 2010-07-20
> **jardin_max said:**
> Not sure if this is what is causing your problems, but something to look into nonetheless.
 
[http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html](http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html)
 
Cheers

Thanks, but I don't think it is related to a memory leak. It seems to be triggered by specific actions noted in the first post. Also, I should have mentioned I am running 9.04.

---

### Post by nirvana21 on 2010-07-20
Is uninstalling nautilus a bad idea? Will it mess up other things? I can do it from another tty if needed.

```
sudo aptitude remove nautilus;sudo aptitude install nautilus
```

---

### Post by JustinR on 2010-07-20
Uninstalling nautilus will break your system.

Edit: You could reinstall it though.

---

### Post by nirvana21 on 2010-07-20
> **JustinR said:**
> Uninstalling nautilus will break your system.

Thanks for warning me.

---

### Post by nirvana21 on 2010-07-21
> **JustinR said:**
> Edit: You could reinstall it though.

As in...
```
sudo aptitude reinstall nautilus
```
?

What is the difference between this and what I posted above? I honestly didn't know there was a reinstall option.

---

### Post by JustinR on 2010-07-21
```

sudo aptitude reinstall nautilus

```

Its different because when you say remove Aptitude doesn't know your going to reinstall it later, and Ubuntu has hard dependencies on Nautilus. But when it does as in passing the reinstall action command then it won't break your system - it's most likely corrupting a broken installation.

---

