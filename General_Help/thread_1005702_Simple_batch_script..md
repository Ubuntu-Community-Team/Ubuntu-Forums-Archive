---
title: "Simple batch script."
date: 2008-12-08
forum: General Help
---

### Post by whyisitalwaysme on 2008-12-08
Hi, i've just put together a simple script to compile a source file then run bochs:

```

#!/bin/bash

~/fasm/fasm system.asm 
/usr/bin/bochs | /dev/null

```

nice and simple and it works but i have some problems:

1. PATH=$PATH:. when inside the fasm folder doesn't seem to enable me to call fasm without its full path. Not that i particularly care in this instance but i'd like to know.

2. why do i need to pipe the output somewhere?

3. How can i get rid of the message "do you want to run *script* or display its contents?", is there anyway i can set the default action to just run the script?

---

### Post by geirha on 2008-12-08
1. You need to export the variable for it to be inherited by a child process.
```
export PATH=$PATH:~/fasm
```
I do not recommend adding . to the PATH. Add the directory instead.

2. You don't. If you are doing it just to skip the start menu, then read the man-page (man bochs)
```

OPTIONS
       When you run bochs without one of the following options, it will search
       for a configuration file called .bochsrc in the current  directory  and
       your home directory and display the start menu.

       -q     With  this  option  the start menu will be skipped after loading
              the configuration file.

```

3. Create a launcher for the script. Right click the desktop and choose create launcher. Provide the full path to the script as the command.

BTW, if you want to ignore the output of a command, the proper way is to use redirection 
```

command > /dev/null  # redirect stdout to /dev/null
command 2> /dev/null # redirect stderr to /dev/null
command &> /dev/null # redirect stdout and stderr to /dev/null

```
You use the pipe if you want two commands to communicate. In your case, you are attempting to run /dev/null as a command and dump the output of bochs to its stdin.

---

