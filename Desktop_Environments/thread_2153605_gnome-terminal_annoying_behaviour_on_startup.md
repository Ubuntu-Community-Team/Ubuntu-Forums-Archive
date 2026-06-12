---
title: "gnome-terminal: annoying behaviour on startup"
date: 2013-06-11
forum: Desktop Environments
---

### Post by George Heine on 2013-06-11
Confession: this one is my own fault.  
Recently needed to reinstall 12.04 LTS on one of my computers, thought I would save the step of configuring a terminal profile, copied the contents of
~/.gconf/apps/gnome-terminal/profiles from an existing machine to the new system.  

Not only did the profiles not copy over, but now the following message pops up every time I start a terminal with any profile:
```
x: command not found
A: command not found
A: command not found
```Prresumably there is a configuration item somewhere that is telling the terminal on startup to try to run the "commands" x, A, A.   
But cannot find it in any of the files in ~/.gcont/apps/gnome-terminal. 

So, how can this problem be fixed?
And the larger issue is, is there anyway to configure the behaviour of terminals from the command line, or by editing configuration files?
(So that, say, it could be added to a script when configuring a new system)

Using 12.04 LTS with GNOME Terminal 3.4.1.1.  Have made no changes to the default desktop (Unity).

This is not a show-stopper, but it is annoying, and any help would be appreciated.

---

