---
title: "TAB Completion in BASH - Sudo Issues"
date: 2009-01-17
forum: General Help
---

### Post by Arabica Bean on 2009-01-17
Okay I've installed a fresh version of 8.10, which I upgraded to the 9.04 alpha. All seems well but when I am using the terminal I run into an issue.

When I type in a few letters of an app and hit the TAB button twice, I get the usual TAB completion

```
richey@richey-desktop:~$ open
open        openoffice  openssl     openvt
```

All well and good, however, if I place a sudo command before the letters "open", tab completion refuses to work.
```

richey@richey-desktop:~$ sudo open  
```

I have ubuntu 8.10 on another partition and that runs fine with tab completion running normal when sudo is used.

Any pointers?

---

### Post by RealPSL on 2009-01-17
There is most likely something broken in the bash-completion package. More specifically in /etc/bash_completion which governs the command completion. There is a section of that script that controls how bash completes commands preceded by sudo. Sounds like you have uncovered a bug which you should probably report.

---

### Post by Arabica Bean on 2009-01-17
I'll report it. Thanks

---

### Post by vanadium on 2009-01-17
Does it work when you press <tab> twice?

---

### Post by Arabica Bean on 2009-01-17
No, but tabbing twice works using a non sudo command.

For the record I've tried completely uninstalling then installing bash and bash-completion in synaptic, but with no success.

---

### Post by 1/0 on 2009-01-19
> **RealPSL said:**
> There is most likely something broken in the bash-completion package. More specifically in /etc/bash_completion which governs the command completion. There is a section of that script that controls how bash completes commands preceded by sudo. Sounds like you have uncovered a bug which you should probably report.

I doubt its a bug. First check that bash_completion is properly configured. Are you using a local or system wide bashrc-file? I.e. is there a *.bashrc* or are you only using the */etc/bash.bashrc*? 

Either way check that one or both of these files are properly configured. That is, look for the lines with:

```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

These lines should be enabled, i.e. no "*#*" at the start of each line.

I would start by checking that before submitting a bug report but I suspect its only that.

PS. You might have to reboot or reload bash in order for it to work

---

### Post by noworry on 2009-03-19
Thanks a lot...

---

### Post by kokendy on 2009-12-20
Same problem, same solution.
Thanks!

---

