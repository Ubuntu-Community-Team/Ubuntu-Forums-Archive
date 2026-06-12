---
title: "~/Desktop folder deleted"
date: 2012-06-21
forum: Desktop Environments
---

### Post by Scoubidou on 2012-06-21
Hi,

Somehow my ~/Desktop folder was deleted (with all file/folder in it)
There was some pretty important files there that I cannot find anymore.

My PC crashed and when it rebooted (alone) all the file from my ~/ were on my desktop. There was a message about convert (i think). When I check the content of my ~/ I notice that ~/Desktop wasn't there. I try creating the folder and reboot, no dice.

So I edited the file user-dirs.dirs

```
vi ~/.config/user-dirs.dirs
```

And added the /Desktop.

Now my Desktop is empty. How can I get the files I lost?
No, they are NOT in the Trash.

Thanks

---

### Post by ajgreeny on 2012-06-21
As you're on 11.04 have a look in gconf-editor > apps > nautilus > preferences to see if the crash has changed the setting shown on my screenshot for **desktop_is_home_dir** which by default should not be selected.

If you can remember the names of any of your missing files you could also use ```
sudo updatedb
``` to update the database of all files, then```
locate -i *filename* | grep home/*username*
``` Just use a part of filename if you can not definitely remember the names.

Apologies if you know al this already; I'm simply trying to help out.

---

