---
title: "Login dialog delay"
date: 2013-08-24
forum: Desktop Environments
---

### Post by akoskm on 2013-08-24
I prefer suspend over complete shut down when it comes to my work PC.

Sometimes, when it wakes up from suspend, the login dialog isn't the first thing what appears (as I expected, maybe I totally wrong about what screen locking means) but the desktop! I have enough time to type command into the terminal, to look at my browsers, etc.

After a few second the login dialog finally comes up, preventing any interaction with my desktop and asking for the password.

I would like to help Ubuntu developers to solve this issue so I'll describe how things should happen (in my opinion):

[LIST=1]
[*]weake up from suspend
[*]show login dialog, ask for password
[*]if 2 OK 4, else return to 2
[*]show the desktop
[/LIST]

NOT 1, 4, 2, ... !

Sadly all of  our development PCs running Ubuntu 12.04 LTS and I have to come up with a solution. Going for another *nix would take to much time, but I'm not sure that simply switching to another desktop environment would solve this issue.

---

