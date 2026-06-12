---
title: "find: WARNING: Hard link count is wrong for /proc..."
date: 2005-12-11
forum: General Help
---

### Post by Kronocide on 2005-12-11
I'm trying to teach standard Apache for Linux, and the school as standardized on Ubuntu for some reason. (Not the likeliest choice for a Linux server in my mind.) I had noticed that several of my students got this error:

*find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver. [...]*

Now I have it as well. Does this ring a bell for anyone? Corrupted filesystems are in my experience very rare in Linux. I'm also aware that /proc is not on the disk, but all the same, still curious.

As a sidenote, I tried to switch off gdm in the "services" app, and that crashed my 'puter. Couldn't even switch to another tty or kill the X server. Deleting the rc link manually worked fine though.

---

### Post by ctos on 2006-04-08
I just now noticed this error as well.

find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

---

### Post by jchau on 2006-04-09
Yup. I get that too.
> find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.

when I type something like:
```
find / -name "test"
```

---

