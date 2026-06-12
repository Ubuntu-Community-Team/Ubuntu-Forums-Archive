---
title: "trouble locking screen with gnome-screensaver"
date: 2007-05-29
forum: Desktop Environments
---

### Post by alwakjubar on 2007-05-29
very wierd thing: gnome-screensaver randomly won't start when i want to lock the screen.  

sometimes it works.  sometimes it doesn't.  at first, i noticed it when i would come back from suspend mode.  but then, it started happening when i would use the ctrl-alt-l shortcut, and the screen wouldn't lock.

i couldn't find any error or log messages for why it wasn't working.  i tried starting gnome-screensaver from the command line but it was already running, it just didn't seem to be responding properly.  

i'm running ubuntu 6.06.1 LTS.  it's gnome-screensaver 2.14.3.

i google'd and came up with the info to use gnome-screensaver-command --lock.

that seemed to get gnome-screensaver working alright, and the screen locked just fine.  from then on, the screen would lock whenever i used the ctrl-alt-L command.

however, randomly when i come back from suspend, the problem starts, and it won't lock again.

when i came back from suspend, the screen saver wasn't running in the process list, so i ran gnome-screensaver from the command line and here's the output i got:

(gnome-screensaver:1865): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(gnome-screensaver:1865): libgnomevfs-WARNING **: Internal error: the configuration system was not initialized. Did you call _gnome_vfs_configuration_init?

any help?

this is a major security problem for me, obviously, if the lock screen doesn't work properly.  especially if it seems to happen when it's resume from suspend, because then it leaves the computer open, obviously.

---

### Post by Pragmatist on 2007-05-29
Have you tried just using xscreensaver instead of gnome-screensaver?

There are also some other interesting packages in the repositories.  Such as lockvc and pessulus among others.  I just used the search feature in synaptic with the key words "lock screen".

---

