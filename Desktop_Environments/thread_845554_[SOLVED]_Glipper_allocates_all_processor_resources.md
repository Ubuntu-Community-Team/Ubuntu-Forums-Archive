---
title: "[SOLVED] Glipper allocates all processor resources"
date: 2008-06-30
forum: Desktop Environments
---

### Post by vlc on 2008-06-30
Hi *,

I have the problem with glipper that it uses the complete processor time when being started (via Add to Panel -> Clipboard Manager). I can see in the system monitor that it consumes ~ 99% of the processor time and furthermore it freezes the panel, so that I have to kill the task.

The problem occurred after enabling compiz. It did not work out for me so I disabled it again. But then, the trouble with glipper started. I already removed glipper (completely with configuration files) and reinstalled it again, but the problem remains.

Does anyone have an idea what could cause this problem?

Thanks a lot in advance!

---

### Post by vlc on 2008-06-30
Got it. I removed glipper again (_with_ configuration files), but what the heck is this? *~/.glipper* is still there. I run the configuration editor and ... */apps/glipper* and */schemas/apps/glipper* are still there. Well, I removed this stuff manually, reinstalled glipper and it works.

But why does removing an application with configuration files does not remove everything? I am quite new to gnome, but this leaves the bad taste of Windows, where removing a program does not mean that it's really removed (program folder, registry, ...). Is this now intended behavior or a kind of bug?

---

### Post by sdennie on 2008-06-30
That's normal behavior.  The configuration files that a program creates in a users home directory are not part of the package and so not removed when the package is removed.  However, if you've uninstalled the package, the worst that these leftover configuration files in your home directory are likely to do is take up a small amount of disk space.

---

### Post by vlc on 2008-07-01
The point is that the problem was probably in these configuration files. After deleting the files, the problem disappeared.

Another point is that the configuration files are apparently not deleted if I make a complete uninstall, even if the description tells me

> To remove all files related to the package			choose Mark for	Complete Removal instead of Mark for Removal.

So my expectation was that all files related to the package would be removed. But that was not the case.

---

### Post by sdennie on 2008-07-01
Well, along with what I said above, you have to realize that Unix/Linux machines are made to be multi-user.  It's not polite for a package manager to go into each users home directory and start erasing files that might be vaguely related to an application when you uninstall it.  If for instance, there are 3 users on a machine, and only 1 has a problem with an application and so that user purges the app to re-install it, the other two users are not going to be pleased that it's caused their configuration files to be deleted.

---

### Post by vlc on 2008-07-01
Good point.

Just for my personal interest: Which configuration files are deleted when I do a complete remove?

---

### Post by sdennie on 2008-07-01
You should be able to see exactly what files will be removed with a --purge before doing it by doing:

```

dpkg -L name_of_package

```

Normally things that are in /etc won't be removed if you don't --purge (possibly other things as well but, --purge is commonly used to insure /etc is cleaned up after the application is removed).

---

### Post by vlc on 2008-07-02
Thanks a lot!

---

### Post by Stefanie on 2008-07-30
> **vlc said:**
> Got it. I removed glipper again (_with_ configuration files), but what the heck is this? *~/.glipper* is still there. I run the configuration editor and ... */apps/glipper* and */schemas/apps/glipper* are still there. Well, I removed this stuff manually, reinstalled glipper and it works.

But why does removing an application with configuration files does not remove everything? I am quite new to gnome, but this leaves the bad taste of Windows, where removing a program does not mean that it's really removed (program folder, registry, ...). Is this now intended behavior or a kind of bug?


thanks, i had the same problem and i didn't figure deleting .glipper might help.

---

