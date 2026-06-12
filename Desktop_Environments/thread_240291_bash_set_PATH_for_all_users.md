---
title: "bash set PATH for all users"
date: 2006-08-20
forum: Desktop Environments
---

### Post by hoodwink on 2006-08-20
I've searched the forums and googled for Debian help as well, but I've not found much.

What script constructs the standard PATH settings for all users?

Please don't suggest ~/.bashrc, since I want to add to the PATH settings for all users.

/etc/profile and/etc/bash.bashrc have nothing, but the PATH has lots of components that must have come from somewhere.

---

### Post by lupine_nickt on 2006-08-20
There's no one script, as such... the PATH variable is built up progressively down the fork() hierarchy.

To give an e.g... the kernel starts up, possibly begins the path variable (maybe the library locations?) and loads init, which will EXPORT PATH= (whatever). That runs an instance of login on each terminal, each of which will add something to the PATH variable (PATH=$PATH:(whatever)). Once you login, it'll set up an instance of bash (or whatever), which will *also* add some stuff to the PATH. 

If you're interested in finding out which binaries do what, then 'strings <somebinary> |grep PATH' will work wonders. Try /bin/bash, /bin/login, /sbin/init for starters. 

If you're looking for a way to add something to all users' paths, the easiest way is to reference a script in /etc/ in all ~/.bashrc files (including /etc/skel, for users created in the future). 

xF,

...Nick

---

### Post by waldschm on 2006-08-20
couldn't you set the path in /etc/bash.bashrc or /etc/profile? Why wouldn't that work?

edit: I also think /etc/login.defs does part of this

---

### Post by hoodwink on 2006-08-20
> **waldschm said:**
> couldn't you set the path in /etc/bash.bashrc or /etc/profile? Why wouldn't that work?

edit: I also think /etc/login.defs does part of this
I certainly could (and probably will) do that. I was just interested in knowing where the standard PATh gets built. On Red Hat systems, the code is in /etc/profile and X startup adds to it.

The question is, if I add something like

exportPATH=$PATH:/my/new/bin/path to /etc/profile

will this do the trick, ie add the path to the end of the list? Which still begs the question: where is the PATH built on Debian systems?

---

