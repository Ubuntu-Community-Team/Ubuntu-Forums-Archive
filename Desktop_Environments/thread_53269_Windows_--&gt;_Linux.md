---
title: "Windows --&gt; Linux"
date: 2005-07-30
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2005-07-30
- Is there a command like Ctrl+Alt+Del in windows?
- Is there in the terminal a command like "cd.." in windows (to go back to the previous folder)?

---

### Post by jasmuz on 2005-07-30
Ctrl+Alt+Del to kill applications right?...you can use the process manager or type alt+f2 and type xkill and click on the program that is being nasty.

and for the previous folder its cd ..  (notice its separated)

---

### Post by drummer on 2005-07-30
Also, for a list of processes and system usage, etc a bit like in windows:
Applications > System Tools > System Monitor

---

### Post by MetalMusicAddict on 2005-07-30
Look [HERE](http://ubuntuforums.org/showthread.php?t=41174) for CTRL+ALT+DEL emulation. Works great. ;)

---

### Post by Sam on 2005-07-30
[QUOTE=ubuntuubuntu]Is there in the terminal a command like "cd.." in windows (to go back to the previous folder)?[/QUOTE]
Open your bashrc file:
```
$ gedit ~/.bashrc
```
Add the next line somewhere:
```
alias cd..='cd ..'
```

---

### Post by Omnios on 2005-07-30
Links for Linux termainal commands /usages etc.

[http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)

 in termainal cd - will take you back to the last location

---

