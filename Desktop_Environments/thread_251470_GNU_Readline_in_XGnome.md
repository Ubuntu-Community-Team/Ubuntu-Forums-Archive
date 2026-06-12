---
title: "GNU Readline in X/Gnome?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by erikcw on 2006-09-05
Hi all,

I use GNU Readline's ~/.inputrc file to create command shortcuts (hotstrings) in the shell.

> 
Example:
"ssh1":"ssh 192.168.168.211 -p 9922 -l myuser\C-M"


So whenever I type out ssh1 in the Terminal it launches ssh with the above arguments.

This makes for really handy shortcuts!  Unfortunately, readline doesn't seem to work in X by default.  Is there a way (or another package) to create these sort of hotstrings for my desktop?

In windows their is a great open source macro package called "AutoHotKey" - but it relies really heavily on the WinAPI so a port is not possible and it doesn't work in wine.

Thanks!
Erik

---

### Post by pgmario on 2006-09-22
If you use bash, you could create an alias. Just add something like this to your .bashrc
```
alias ssh1='ssh 192.168.168.211 -p 9922 -l myuser\C-M'
```
In order to activate the changes you have to reboot or enter ```
source .bashrc
```

---

### Post by erikcw on 2006-09-22
Yes, an alias would work well on the command line, but I've already got readline do this for me on the command line.

I want to setup something like readline or an alias inside gnome.  So I can be in firefox, type ssh1, and have that alias start running.  Basically a "hot-string" instead of a "hot-key".

Any ideas?

Thanks!

---

### Post by pgmario on 2006-09-22
The only thing I could think of would be to press alt+F2 and enter the command. If you use a commandline tool like ssh it might be necessary to include "xterm -e" in your alias.

```
alias ssh1='xterm -e "ssh 192.168.168.211 -p 9922 -l myuser\C-M"'
```

---

