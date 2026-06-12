---
title: "How to run multiple lines of code via one comand or program"
date: 2008-12-17
forum: General Help
---

### Post by -Cluster- on 2008-12-17
I have a set of commands that change drivers and blakclist odl download new upack install and set to a certain mode. I need to do this every now and again and it gets labourious to type each one in.

So is there a way to run one command to run several, one after the other

---

### Post by taurus on 2008-12-17
Why not create a script file and run the file to execute all those commands?  Call it whatever you want, e.g. filename.sh.

```

#!/bin/bash
first_command
second_command
third_command
fourth_command

```
Save it and change the permissions.

```
chmod 755 filename.sh
```

---

### Post by -Cluster- on 2008-12-17
Sorry where do i write this

in a notepad file? and where?

---

### Post by taurus on 2008-12-17
Applications -> Accessories -> Terminal
```
gedit filename.sh
```
Do you need to run those commands as root, sudo?

---

### Post by -Cluster- on 2008-12-17
Ok i rote it in a notepad and saved it as whack.sh

i did chmod 755 whack.sh

tried to run it and it said bash:whack:command not found

Some codes are sudo, as in sudo apt-get install XXXX

---

### Post by jenkinbr on 2008-12-17
try running it as ./whack.sh  Security reasons require the ./ to be there.

---

### Post by adult swim on 2008-12-17
you need to cd to the directory you saved it in and run it like ```
./whack.sh
```

---

### Post by Slim Odds on 2008-12-17
> **taurus said:**
> Save it and change the permissions.

```
chmod 755 filename.sh
```

I know that we're all geeks here, but we should really show it this way:```
chmod +x filename.sh
```It's a little more intuitive than using octal (I think). Especially if you're taking to a non-geek.

---

### Post by -Cluster- on 2008-12-17
ok. Yeah my bad about the running off it but now the next step

I want to be able to put in variables into a bash script

I found out about the $VAR thing, but the tutorial doesn't really show an example of the variable being set by running the script so is this possible. I am thinking of it being like a function in programing an example in VB would be

Function whack.sh(X=variable)

the program would then use that x in the code when refered i am guessing this would be

apt-get $x

so how do i do this in linux?

---

### Post by jenkinbr on 2008-12-17
use $<num> as the variable. for example, if you ran ```
./whack.sh foo bar
```, the text 'foo' would be stored in the variable $1 and the text 'bar' would be stored in the variable $2 .

---

### Post by -Cluster- on 2008-12-17
Last question.....I think, is there a way to open a new terminal and run commands in it?

---

### Post by jenkinbr on 2008-12-17
> **-Cluster- said:**
> Last question.....I think, is there a way to open a new terminal and run commands in it?

You mean from within the script or before running the script?  And in either case, do you need to review what happened, or is it to supply input?

---

### Post by -Cluster- on 2008-12-17
> **jenkinbr said:**
> You mean from within the script or before running the script?  And in either case, do you need to review what happened, or is it to supply input?

Well i need to open another terminal to run code in and leave the first terminal running a piece of code in that

---

### Post by adult swim on 2008-12-17
you could add the line 
```
gnome-terminal
``` to your script

---

### Post by |{urse on 2008-12-17
You might want to replace all instances of sudo with gksudo.

---

### Post by jenkinbr on 2008-12-17
you could use job control - it will let you push a command to the background, so it still runs.  For example:
```

command-1 &

```

will drop the running 'command-1' into the background and bring you to a prompt, where you could then type:
```

command-2
```

which will then run alongside of command-1.

This will, however, dump any and all output these commands produce to the screen at the same time.  You can use output redirection to send the output to a file, or if you don't want to view the stuff at all, you could send it to /dev/null.

This:
```
command-1 >/dev/null &
```
will start command-1 running in the background, with the standard output being directed to /dev/null, which is known as the bit-bucket, or black hole.  Any data written to /dev/null will be discarded. To redirect error messages as well, try:
```
command-1 >/dev/null 2>&1 &
```
which will also direct error messages to /dev/null.

If you would rather send it to a file, simply replace /dev/null with the filename you want to write to.

---

