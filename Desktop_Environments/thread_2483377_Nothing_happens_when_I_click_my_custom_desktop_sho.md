---
title: "Nothing happens when I click my custom desktop shortcut"
date: 2023-01-28
forum: Desktop Environments
---

### Post by kinstonian2 on 2023-01-28
This custom desktop shortcut has an icon but when I click it nothing happens.  Everything including the path looks correct to me.  The ghidraRun file is a shell script which works if I run it in a terminal.  It just won't run when I click the shortcut.

```
[Desktop Entry]
Name=Ghidra
GenericName=Reverse Engineering Framework
Comment=Ghidra is a software reverse engineering (SRE) framework
Exec=/opt/ghidra_10.2.2/ghidraRun
Terminal=false
Type=Application
Icon=/opt/ghidra_10.2.2/docs/images/GHIDRA_1.png
Categories=Utilities

```


ghidraRun
```
#!/usr/bin/env bash

#----------------------------------------
# Ghidra launch
#----------------------------------------

# Maximum heap memory may be changed if default is inadequate. This will generally be up to 1/4 of 
# the physical memory available to the OS. Uncomment MAXMEM setting if non-default value is needed.
#MAXMEM=2G

# Resolve symbolic link if present and get the directory this script lives in.
# NOTE: "readlink -f" is best but works on Linux only, "readlink" will only work if your PWD
# contains the link you are calling (which is the best we can do on macOS), and the "echo" is the 
# fallback, which doesn't attempt to do anything with links.
SCRIPT_FILE="$(readlink -f "$0" 2>/dev/null || readlink "$0" 2>/dev/null || echo "$0")"
SCRIPT_DIR="${SCRIPT_FILE%/*}"

# Launch Ghidra
"${SCRIPT_DIR}"/support/launch.sh bg jdk Ghidra "${MAXMEM}" "" ghidra.GhidraRun "$@"
```

---

### Post by ne29914 on 2023-01-28
Flavour? Version?
This is not Twitter.

---

### Post by monkeybrain20122 on 2023-01-28
Did you make the .desktop file executable? 

Are you using stock Ubuntu? Is the .desktop file placed in ~/.local/share/applications? I think nautilus now doesn't allow user scripts to be launched from gui in $HOME.  If this is the case you have two options

1) move the .desktop file to /usr/share/applications or /usr/local/share/applications

2) use a different file manager as default such as nemo. Nautilus is PITA to use now.

---

### Post by kinstonian2 on 2023-01-28
> **monkeybrain20122 said:**
> Did you make the .desktop file executable? 

Are you using stock Ubuntu? Is the .desktop file placed in ~/.local/share/applications? I think nautilus now doesn't allow user scripts to be launched from gui in $HOME.  If this is the case you have two options

1) move the .desktop file to /usr/share/applications or /usr/local/share/applications

2) use a different file manager as default such as nemo. Nautilus is PITA to use now.

Yes, Ubuntu 22.04 and it's executable.  I right clicked and selected Allow Launching.  I just moved the .desktop file to /usr/share/applications and /usr/local/share/applications.  Still no luck. :(  I'd like to try a different file manager as a last resort.

---

### Post by monkeybrain20122 on 2023-01-28
> **kinstonian2 said:**
> **The ghidraRun file is a shell script which works if I run it in a terminal.**  It just won't run when I click the shortcut.

```
[Desktop Entry]
Name=Ghidra
GenericName=Reverse Engineering Framework
Comment=Ghidra is a software reverse engineering (SRE) framework
Exec=/opt/ghidra_10.2.2/ghidraRun
**Terminal=false**
Type=Application
Icon=/opt/ghidra_10.2.2/docs/images/GHIDRA_1.png
Categories=Utilities

```




Maybe you should set Terminal=true?

---

### Post by kinstonian2 on 2023-01-28
> **monkeybrain20122 said:**
> Maybe you should set Terminal=true?

Ah that was a good guess, but changing it to true has no effect.

---

### Post by monkeybrain20122 on 2023-01-28
what if you run just run
```

/opt/ghidra_10.2.2/ghidraRun
```

in the terminal? Does it launch?

---

### Post by kinstonian2 on 2023-01-28
> **monkeybrain20122 said:**
> what if you run just run
```

/opt/ghidra_10.2.2/ghidraRun
```

in the terminal? Does it launch?

Yup, runs fine if I launch it manually in the terminal with that command.

---

### Post by QIII on 2023-01-28
What is the full text of the command in the shortcut properties?

Is there more than

```
/opt/ghidra_10.2.2/ghidraRun
```

---

### Post by kinstonian2 on 2023-01-28
> **QIII said:**
> What is the full text of the command in the shortcut properties?

Is there more than

```
/opt/ghidra_10.2.2/ghidraRun
```


No that's all there is to the command in the shortcut.

---

### Post by monkeybrain20122 on 2023-01-28
I cannot see what is wrong with it.

But did you edit .bashrc to set environmental variables when you installed the script? Or did it ask permission to write there? (it is not just a script from their website, you have to install a bunch of things apparently)

---

### Post by kinstonian2 on 2023-01-28
> **monkeybrain20122 said:**
> I cannot see what is wrong with it.

But did you edit .bashrc to set environmental variables when you installed the script? Or did it ask permission to write there? (it is not just a script from their website, you have to install a bunch of things apparently)


I have no idea what's wrong with it either.  I just added the path to java in $PATH to the .bashrc.  Ghidra is a java program that is started by that script.  Unless someone else has any ideas on what could be wrong I'll just have to start it in a command prompt.  Thanks for your help though.  We've ruled some things out.

---

### Post by monkeybrain20122 on 2023-01-28
> **kinstonian2 said:**
>  I just added the path to java in $PATH to the .bashrc.  Ghidra is a java program that is started by that script.  Unless someone else has any ideas on what could be wrong I'll just have to start it in a command prompt.  Thanks for your help though.  We've ruled some things out.

I think that is the problem. If the environmental variables are added to .bashrc it won't work on gui such as your .desktop file. You should add it to your .profile then logout and login for it to take effect. Or you can add it to your desktop file with for example Execs=env LD_LIBRARY_PATH=/... command_to_start program, or you can create a wrapper script and put it in your $PATH and use it to invoke your script. The wrapper should take care of the environmental variables.

[https://askubuntu.com/questions/144968/set-variable-in-desktop-file](https://askubuntu.com/questions/144968/set-variable-in-desktop-file)

---

### Post by kinstonian2 on 2023-01-29
> **monkeybrain20122 said:**
> I think that is the problem. If the environmental variables are added to .bashrc it won't work on gui such as your .desktop file. You should add it to your .profile then logout and login for it to take effect. Or you can add it to your desktop file with for example Execs=env LD_LIBRARY_PATH=/... command_to_start program, or you can create a wrapper script and put it in your $PATH and use it to invoke your script. The wrapper should take care of the environmental variables.

[https://askubuntu.com/questions/144968/set-variable-in-desktop-file](https://askubuntu.com/questions/144968/set-variable-in-desktop-file)

Still doesn't work. You're right though, Nautilus is PITA!  I think it's time to give nemo a try.  Thanks for your help. :)

---

