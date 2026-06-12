---
title: "FLUXBOX: Help write simple launcher shortcut!"
date: 2008-06-13
forum: Desktop Environments
---

### Post by oleksus on 2008-06-13
I've been reading the docs on fluxbox.keys and tried several things, but the only shortcut I've been able to set was Alt-F1 to launch xterm (which opens very small sized!).

I need to launch a command in order to start an application in a certain directory. Usually I do it in terminal:

*cd home/me/program/frontend *

*wxlua program.lua*

Whatever I tried with *ExecCommand* never worked.
What am I missing here?

And how do I launch a normal terminal, not xterm, and in a normal size, like it has when opened from the menu?

Thanks in advance!

---

### Post by kerry_s on 2008-06-13
> wxlua program.lua

this is the command to start it?

i going to assume you have wxlua is in /usr/bin or /usr/local/bin, so it's in the path?

```
Mod1 ? :Exec wxlua ~/program/frontend/program.lua
```

the program.lua is executable right?

---

### Post by urukrama on 2008-06-13
In addition to what kerry_s wrote:

Have you seen cknight's excellent post ["The power of Fluxbox keys"]("http://ubuntuforums.org/showthread.php?t=617812")? It shows extensively how to use Fluxbox keys and what you can do with them.

---

### Post by oleksus on 2008-06-14
Thanks, the problem was that wxlua was not in the path.

I still don't know the correct terminal command though...

---

### Post by kerry_s on 2008-06-14
> **oleksus said:**
> Thanks, the problem was that wxlua was not in the path.

I still don't know the correct terminal command though...

the command would be:
```
wxlua ~/program/frontend/program.lua
```

in term:
sudo updatedb
locate wxlua

will tell you where it's at, it should be in the path if this worked-> wxlua program.lua
unless you have them both in the same place.

---

