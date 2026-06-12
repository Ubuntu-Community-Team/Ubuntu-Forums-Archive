---
title: "nautilus crash; : please help me!"
date: 2010-03-01
forum: Desktop Environments
---

### Post by vale_ron on 2010-03-01
Hi guys,

today I experienced this problem: suddenly nautilus crashed and after that it became unusable. This means that if I try to open a directory, sfter a few instants it crashes.

I tried to use it through another user as root or another one and in these cases nautilus works. So that I'm thinking to a user-specific issue. 

In addition to all of that, if I use it with root and I move to the default user's home folder, it crashes.

This is the output of ```
sudo nautilus
```:

```

valeron@valeron-laptop:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7364): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:7364): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:7364): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension
valeron@valeron-laptop:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7377): WARNING **: Unable to add monitor: Operation not supported
nautilus: /build/buildd/glib2.0-2.18.2/gio/xdgmime/xdgmimecache.c:461: cache_glob_node_lookup_suffix: Assertion `character != 0' failed.
Aborted
valeron@valeron-laptop:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:7397): WARNING **: Unable to add monitor: Operation not supported

```

Thanks in advance for your support!

---

