---
title: "Shortcut - Execute in Directory"
date: 2010-01-26
forum: Desktop Environments
---

### Post by temporalmaniac on 2010-01-26
Hello, all!

I've been using Ubuntu for two or three weeks after coming off Fedora 12 KDE, and I'm trying to figure out how to get a shortcut in GNOME to "cd" to a certain directory first. In KDE, one can configure shortcuts to run in a specific directory, such as starting up GNU Octave inside ~/octave instead of some other default location.

I've run into an issue in Wine where a program behaves differently depending on my current directory. Specifically, it only works when I'm inside the same directory as the exectutable and I execute Wine. Anywhere else, it won't work, even if I give an absolute pathname to Wine.

In Nautilus, I can double-click the .exe inside of its folder and it *will* work, just as if I were in that folder and did "wine *program*.exe". I want to make a shortcut in my GNOME menu to run this program inside its directory, but it always seems to call it from somewhere else, so it won't work. I can't be sneaky and have it execute "cd /path/to/program/; wine program.exe", as it will complain about the cd.

My question: Can I have a shortcut in GNOME that will execute a command inside a specific directory? Is there an easy way to do it, or must I go in and start tweaking the .desktop files on a text level (assuming they exist)?

Thanks!

---

### Post by sisco311 on 2010-01-26
Run the commands in a sub-shell (sh or bash):
```
sh -c "cd /path/to/dir && wine ./program.exe"
```

---

### Post by freebeer on 2010-01-26
Why not just run a little bash script?  It'll accept the cd command just fine.

---

### Post by temporalmaniac on 2010-01-26
Thanks! I hadn't thought about doing the sub-shell method, but that works just fine.

The script method would have worked, too, but I opted for the sub-shell technique as it was new to me (and I didn't feel like making a script file).

Thanks!
Mischief managed.

---

