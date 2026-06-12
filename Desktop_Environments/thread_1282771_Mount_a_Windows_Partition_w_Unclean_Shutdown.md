---
title: "Mount a Windows Partition w/ Unclean Shutdown?"
date: 2009-10-04
forum: Desktop Environments
---

### Post by justinram22 on 2009-10-04
Hello, here is what im trying to do.

My Uncle has a nice desktop that he put all his music and pictures onto...  Now it will not start up due to virii.  He wanted me to clean it up for him but wanted to save his music and pictures.  I thought "oh, no problem, I'll just boot off a live CD and copy all his files to my external hdd and then kill-disk his drive" But i totally forgot about the unclean shutdown aspect of it... Is there a way to mount his drive?

---

### Post by renkinjutsu on 2009-10-04
what happens when you try to boot it up?

I don't know if this is safe or not.. but try booting the computer and turn it off when windows starts "loading" .. when you see some sort of splash screen or something

---

### Post by justinram22 on 2009-10-04
It goes to the "start windows safely" option.  But as soon as you hit enter (on any of the options [ex safe mode, safe mode w/ command prompt]) it just restarts.  Personally to me, the computer was getting slow and needed a fresh install anyway?  Thanks for the reply!

---

### Post by renkinjutsu on 2009-10-04
i remember being able to mount windows partitions after unclean shutdowns after having have windows START to load/resume and then turning the machine off.. But you can't even seem to get windows to start loading here

sorry my reply didn't help.. keep trying!

---

### Post by drs305 on 2009-10-04
Of course the preferred method is to put it back in a Windows environment and cleanly unmount it.

If that is not an option, another is to use "ntfsfix". I've used it without any problems but others are still a bit leery. "ntfsfix" is part of the "ntfsprogs" package. To me it is much preferable to trying to force mount the partition.

Install it with:
```

sudo apt-get install ntfsprogs

```

Then run it on the unmounted partition:
```

sudo ntfsfix /dev/sd**XX**

```

I would read the man page for ntfsfix before running the command, and you might want to see what others have said about it via a Google search.

---

### Post by justinram22 on 2009-10-04
Found This command in the error tab thing (idk what to call it)

sudo mount -t ntfs-3g /dev/sda1 /mnt/ -o force

And it worked! lol i guess that makes this thread useless... I Don't really know how to delete a thread, but i'm all hears!

EDIT:  Well then i guess I'm lucky it worked?

---

### Post by drs305 on 2009-10-04
> **justinram22 said:**
> Found This command in the error tab thing (idk what to call it)

sudo mount -t ntfs-3g /dev/sda1 /mnt/ -o force

And it worked! lol i guess that makes this thread useless... I Don't really know how to delete a thread, but i'm all hears!

Glad you got it working.

*You mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance. You can also retract a 'Solved' status there if needed.*

---

