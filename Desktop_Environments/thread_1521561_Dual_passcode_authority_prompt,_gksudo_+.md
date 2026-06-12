---
title: "Dual passcode authority prompt, gksudo + ?"
date: 2010-07-01
forum: Desktop Environments
---

### Post by gimfred on 2010-07-01
I installed Kubuntu, then Ubuntu desktop, Ubuntustudios.

However, since signing into Gnome, I seem to have two sudo type applications installed. :confused:
If I do the following:
> 'Alt+f2' > gksudo $insertprogramname
I get the standard gksudo passcode prompt. It accepts my passcode and I can run synaptic etc...


[IMG]http://dl.dropbox.com/u/1123646/gksudo.png[/IMG]


If I use gnome-do*, I get a different passcode prompt, and it doesn't accept my passcode (I've tried variations; thank NULL that it doesn't lock the authorisation!) What ever the program is, it also affects the ubuntu menus because the same occurs with using them... :(




[IMG]http://dl.dropbox.com/u/1123646/gksudo2.png[/IMG]

I don't even know what the program is called. How do I go about uncovering it and removing/setting it up properly?
sudo gksudo kdesudo all accept my passcode.

> Second Post:
It seems gksu (not gksudo though ... ) brings up the alternative sign in. Why it doesn't accept my password is beyond me.

gksu -S runs in gksudo mode so when various launchers are accessed they must use gksu not gksudo. Why?
I haven't set root password, and I'd prefer to be able to fix this sans root.
> 
Third Post:
From the man page:
```
Notice  that  all the magic is done by the underlying library, libgksu. 
Also notice that the library will decide if it should use su or sudo as backend  using  the  /apps/gksu/sudo-mode gconf  key, if you call the gksu command. 
You can force the backend by using the gksudo command, or by using the --sudo-mode and --su-mode options.
```

To change this I opened the gconf editor:
```
$ gksudo gconf-editor &
```
Then found /apps/gksu/sudo-mode gconf key
and ticked the sudo-mode box.

All done!

---

### Post by gimfred on 2010-07-01
NO one replied; so deleting post.

---

