---
title: "Kubuntu: Where is &quot;Sessions&quot; manager?"
date: 2007-05-13
forum: Desktop Environments
---

### Post by Shinobi326 on 2007-05-13
When I was using straight forward Ubuntu there is a sessions manager that allows you to modify what is being loaded on a reboot.  For the life of me I can't find the equivalent in Kubuntu desktop.

I was to be able to start Beryl-Manager on startup but I can't figure out where it is.

HELP!

---

### Post by Nythain on 2007-05-13
kde's actual session manager isnt as great as gnomes...
in the session manager (located kmenu----> system settings------->advanced tab) all you can set really is 
wether to reload the last session (wich will reload any apps that were running when you closed the session)
start a new session
start a manually saved session

but kde does have an autostart directory where you can put .desktop links, or create symlinks to existing .desktop files that will run when kde loads. its located
home----->user----->.kde----->Autostart
or
~/.kde/Autostart

---

### Post by Shinobi326 on 2007-05-14
Thanks... that did the trick!  I had to figure out where the .kde folder is for a bit until I figured out it was a hidden folder....

THANKS!

---

