---
title: "[SOLVED] Conflicting permissions when sharing home partition between Fedora 10 and Ub"
date: 2008-11-15
forum: Desktop Environments
---

### Post by jvincent08 on 2008-11-15
I'm not sure if this is due to Fedora 10 or not, but the problem didn't start until after I installed it, so here goes.

I have my /home on a separate partition so I can share it between different distributions. First I had Ubuntu 8.10 installed and everything was working as it should. Then, I installed the preview of Fedora 10 yesterday alongside Ubuntu. Everything worked at first (well, not everything, but everything relevant to this situation), but then when I booted back into Ubuntu, I began seeing errors when I sign in through X. Here they are in order, starting from when I type in my password and hit enter:

First, error 1
```
Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others.
```

Click ok and then error 2,
```

Could not update ICEauthority file /home/justin/.ICEauthority

```

Continue on, and error 3
```

There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

```
Okay, then error 4
```

There was an error starting up the screensaver: failed to change to directory /home/justin (permission denied). Screensaver functionality will not work in this session.

```

And finally, error 5
```

Cannot create the directory /home/justin/.gnome2/share/fonts.
This is needed to allow changing the mouse pointer theme.

```
After that last error, the desktop refuses to load any further. The background is loaded and the cursor is responsive, but the menus and such don't appear. So off to the terminal I go. After hitting Ctrl+Alt+F1 and logging in, I get:
```

No directory, logging in with HOME=/
```
and, naturally, I'm presented with a bash prompt at /. However, /home/justin *does* exist. ls -l /home/justin reports
```

drwxrw-r-- 108 500 500 (last modified, etc)

```
Executing 'sudo chown -R justin:justin /home/justin' eliminates error 1. 2 and 3 appear, but after that the screen goes black with only a cursor. 4 and 5 do not appear.

Now, all of that was in Ubuntu. If I boot back into Fedora, I get error number 2 and the same freezing desktop. At this point, permissions are 1000 1000 for /home/justin and all files within it. 'chown -R justin:justin /home/justin' doesn't help here. 

The only way I can log into X is by logging in with the root account. I'm not sure whether or not this should be posted on Fedora or Ubuntu forums, so I've posted on both. Any help would be greatly appreciated, and thanks in advance for taking the time to read all this.

---

### Post by taurus on 2008-11-15
You could probably have guessed what is wrong with it.  Your user ID in Fedora is 500 while your user ID in Ubuntu is 1000.  Therefore, it will get changed each time you boot into whichever distro you plan to use.  

So, you have two options:

1.  Edit /etc/passwd (in Fedora) and change your UID & GID from 500 to 1000.  You also need to edit /etc/group as well.

-or-

2.  Edit /etc/passwd (in Ubuntu) and change your UID & GID from 1000 to 500.  You also need to edit /etc/group as well.

---

### Post by jvincent08 on 2008-11-15
Ahh, that did the trick! Thanks :)

It seems as though Fedora is one of the very few, if not the only one, to use 500 as a starting UID. Most other distros start at 1000. I'll keep this in mind for future reference.

After changing the UID's, I also had to (re)give executable permissions to all directories and subdirectories in my home folder (including hidden . directories). After doing these two things, I was able to log into X just fine and everything was back to normal. Thanks again :)

---

### Post by taurus on 2008-11-15
Gentoo uses 500 for the first user on the system too.  I don't recall about OpenSUSE since haven't used/installed it for a while now.

---

