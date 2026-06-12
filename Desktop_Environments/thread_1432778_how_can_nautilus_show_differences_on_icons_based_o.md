---
title: "how can nautilus show differences on icons based on permissions?"
date: 2010-03-18
forum: Desktop Environments
---

### Post by tanoloco on 2010-03-18
Hello! :)

I open a test_folder with nautilus with rw permissions and it shows me on files and folders contained:
an icon: if I have rw permissions on it
an icon plus a lock: if I have r- permissions on it
an icon plus an x: if have -w permissions on it
an icon plus a lock and a x: if I have -- permissions on it

If I chmod the test_folder to r- (loosing the write permission) nautilus will keep only the x symbol
on a contained file / folder if not readable but it will loose the lock symbol!

I find this very confusing because:
1. I  can still modify a file if it has the w permission even if contained in a folder without the w option
so this file shouldn't have the lock while another one without the w option must show the lock because in fact I cannot modify it. Instead they areboth shown without the lock.

2. I don't know the permissions set on folders!!! only looking at the nautilus folder but I have to check them through a teminal window!!! f

And what about the x permission? (execute) sometimes it could be easy to know if a  x permission is set on a file only looking at it on a nautilus folder .. instead I  have  again to check it through the terminal.

Is there a way to fix it?

I mean is there a way to get nautilus show alway a lock if not witable an x if not readable and something if not executable depending on the specific file / folder permissions and not on the permission of the folder from where I'm looking!

It's as I cd with terminal on a folder without w pemission for example and ls -l command would stop showing me the w permission on the files /folders contained!
or never have the x permission shown

It has no sense IMO

nothing against the terminal: I like it, only if I work with the gui I would like to be able to work with it and not to be obliged to use the terminal because there's no info with the gui.

Hope it makes sense for you :)

---

### Post by Morbius1 on 2010-03-18
I don't have an answer on how to fix all that but I'm wondering why you're going to the terminal to find permissions and ownership. Why not just change nautilus to look like this:

---

### Post by tanoloco on 2010-03-18
Thank you! :)

This helps me!!

At least I won't be obliged to use the terminal if working with the gui :)))

But I'm still thinking that symbols on icons don't work good .. maybe in the future releases they can fix it.

Could it be an idea to send it as a bug to launchpad ?

---

