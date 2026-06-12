---
title: "startup programs/scripts load erratically"
date: 2011-11-23
forum: Desktop Environments
---

### Post by Jonathan.Dufte on 2011-11-23
Hi there,

I hope I'm posting under the right topic. Here's my issue:

I am executing a script to mount an ssh-fs right after login via the startup-list manager in gnome. Most of the times it executes fine but every now and then it doesn't. The network-interface is long up at that point already. Does anyone know about similar issues with the gnome startup-list? I just want to figure out wether this is a problem with gnome or my own script.
thanks

EDIT: I am using ubuntu LUCID

---

### Post by ajgreeny on 2011-11-23
I suppose it may just all be happening at the same time, and some glitch is causing it to be interrupted occasionally.  You could try adding a sleep option to the command you use in the startup list of something like ```
bash -c "sleep 20; <command>"
``` to delay the command by 20 seconds.

Worth a try, surely?  I had to make a similar startup commands for some things I wanted to start at boot time, though I admit all mine are GUI apps, not something simple like a mount command.

---

