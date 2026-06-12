---
title: "compiz issues"
date: 2007-11-29
forum: Desktop Environments
---

### Post by twist2b on 2007-11-29
[PHP]craig@craig-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
inotify_add_watch: No such file or directory
A handler is already registered for the path starting with path[0] = "org"

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20070917' loaded

/usr/bin/compiz.real (3d) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin '3d'
[/PHP]

also in that code i didnt paste this:

[PHP]A handler is already registered for the path starting with path[0] = "org"
[/PHP]

theres like 50 of those... so what did i do.... i have beryl but i dont think its active?

the only way to get compiz working to show all that up there showing is when i type

compiz -- configure
and then i have to type that every time i log on or start ubuntu up... AND i have to leave the terminal open for everything to work :'(


help!!!!

---

