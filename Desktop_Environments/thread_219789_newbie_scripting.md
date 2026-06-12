---
title: "newbie scripting"
date: 2006-07-20
forum: Desktop Environments
---

### Post by bedog on 2006-07-20
Being a new convert to the linux platform, I'm not used to the scripting (even if I try to learn).

Are there any way to make the linux equivalent of windows batchjobs?
Eg, a simple script that runs commands in the order they appear in the file.

Example:

/bin/tuncfg
/bin/hamachi start
gedit anyfile

again, I'm a complete newbie to the scripting and would like to learn, but need to do this in very small steps...

---

### Post by Lord Illidan on 2006-07-20
Like this?

```

#!/bin/bash

gedit somefile
vi some file
./somefile


``` 
[http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html]("http://pegasus.rutgers.edu/%7Eelflord/unix/bash-tute.html")

EDIT : After you save the file, then run it like this..

Say you saved it as script.
From the terminal, type this command : ```
sh script
``` and press enter.

---

### Post by Paerez on 2006-07-20
The scripting language you will use is called "bash". Here is how to write a very simple bash script:
```
#!/bin/sh
echo hello

```
you can replace "echo hello" with any commands you want that can be run in the terminal, like this:
```
#!/bin/sh
/bin/tuncfg
/bin/hamachi start
gedit anyfile
```
not so tough huh?

EDIT: I forgot to tell you how to run it!
save it as file.sh (replace the "file" with whatever) then run "chmod +x file.sh" this makes it eXecutable (runnable). Then in the terminal type "/path/to/file.sh". If its in the current directory, just type "./file.sh" because "." = current directory.

---

### Post by bedog on 2006-07-20
alright, that dowsn't seem to bad...

but do they always have to be run from terminal?

Not that I have anything against it, I'm just wondering if you can create scripts as easily and then run them by clicking them?

---

### Post by Paerez on 2006-07-20
you can click them too, but ubuntu will say "would you like to display or run this?"

but you can create an application launcher on the desktop or panel whose application is your script. Then you can give it a cool name and an icon.

---

### Post by bedog on 2006-07-20
Yay, excellent help.

The script is created, and it performs the tasks I want it to.

Now, for the launcher.

I've created a launcher, but should I keep anything special in mind? Or should I just give it a name, point it to the script and find myself a nifty icon? ;)

---

### Post by Paerez on 2006-07-20
I like to keep my scripts in /home/me/bin, then I edited my PATH variable to include /home/me/bin. This means that if I have /home/me/bin/file.sh, I can be in any directory and type "file.sh" on the command line and I can run it, I never need to find it. Thats handy if you use the terminal often.

As for the launcher the only reason I make a launcher is so that I can keep my scripts all in one folder (/home/me/bin) and then put launchers wherever I need them. And of course the icon. Gimp is good at making icons. Any PNG can be the icon.

---

