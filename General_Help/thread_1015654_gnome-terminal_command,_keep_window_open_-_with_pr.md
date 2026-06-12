---
title: "gnome-terminal command, keep window open - with prompt"
date: 2008-12-19
forum: General Help
---

### Post by BartInTN on 2008-12-19
The old thread:
[http://ubuntuforums.org/showthread.php?t=509463](http://ubuntuforums.org/showthread.php?t=509463)

talks about how to keep the terminal open, with a prompt, after running gnome-terminal.

AnRa gave a great tidbit to create a script, which I call keepopen:
```
#!/bin/sh
$1
bash
```
that one can use to launch another script with the desired effects.

I'd like to add that one can use the --working-directory= option in gnome-terminal command to have the bash open in the desired directory.  I'd suggest using full paths when executing.

so my setup is (8.10 Intrepid, for the record):
/usr/bin/gnome-terminal --working-directory=/whereiwanttobe -e "/home/me/scripts/keepopen /home/me/scripts/helloworld"

OK, here's my question for ya'll: is there a better way to do this???

I have tried setting terminal window options to "hold the terminal open," but that does not give a new prompt after running the command in the terminal.  I've checked these forums and others with no better solution than the above... except maybe to use xterm.

---

### Post by Elcid247 on 2010-03-27
u could try this, its a play on the code u posted above.

make a script file, and put this
```
#!/bin/bash
"$@"
read
```

don't forget to make it executable :D

then issue

```
gnome-terminal -x "KeepOpen.sh COMMAND"
```

u could also add to the script

```
echo "Press enter to close"
```

;)

---

### Post by BiffHenderson on 2010-09-10
This is a slightly old post, but I found a pretty good solution to this issue.  It's really just an expansion of the script referenced earlier in this post:

```
#! /bin/bash
WD=`dirname $1`
USER=`whoami`
cd $WD
$1;sudo -s -u $USER
```

I used to have just 'sudo -s', but I got sick of always having to enter my password.  This seemed to dodge that requirement by supplying the username of the active user.  

In the Main Menu editor i just put: 

gnome-terminal -e "sh /path/to/launcher.sh /usr/bin/nmap" &

It doesn't seem pretty, but it does the trick.  The entire reason I wanted to achieve this behavior in the first was place to mirror the functionality of BackTrack's Menu (apparently KDE has features that make the process far more direct).  I hope this helps someone.  It saved me a bunch of trouble.

---

