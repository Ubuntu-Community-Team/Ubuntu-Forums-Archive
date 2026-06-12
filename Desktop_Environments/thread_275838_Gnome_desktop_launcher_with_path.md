---
title: "Gnome desktop launcher with path?"
date: 2006-10-11
forum: Desktop Environments
---

### Post by djcinsb on 2006-10-11
I have an executable file that needs to be run from a specific folder.  I'd like to create a desktop launcher under Gnome that changes to the folder and then launches the application.  I can write a one line shell script to do it from a console window -- basically it looks like this:

    cd /home/user/progDir;prog

Can anyone give me a clue about how to do the same thing from a launcher?  I've tried putting the full text in the launcher, and setting it to run the shell script, but so far no luck.

Thanks.

---

### Post by encompass on 2006-10-12
Right click on the background select create launcher...
Then fille it out like this picture shows...
[[IMG]http://img209.imageshack.us/img209/9007/createlauncherit4.th.gif[/IMG]](http://img209.imageshack.us/my.php?image=createlauncherit4.gif)
From there you can take that launcher and put it jsut about anywhere including in your menus using alecarte menu editor.

---

### Post by djcinsb on 2006-10-12
That was my first attempt -- I built a launcher, but don't see any way to set the startup directory to the one I need.  

The problem is that the launcher doesn't start the app with its local working directory set to the correct folder.  There is startup data required to launch the program in that folder -- when the app does not find that startup data, the app terminates immediately.   

Yeah, it's a design problem for the program, but one I need to work around.  I can make this all work on KDE/Mandriva, but don't see how to make Gnome/Ubuntu do it.

---

### Post by s_p_a_r_k_y on 2006-10-12
how about create another file, called launcher

```

#!/bin/sh
cd /to/folder/
program

```

and then make that executable,
```

chmod 755 launcher

```
then put the path to the launcher in the gnome desktop file

---

### Post by djcinsb on 2006-10-12
Thanks for the suggestion, but still no luck.  (I'd tried that before, but just finished trying again, in case I missed something.)  

I have the shell script, written as you suggest.  It works fine from a console.  But when I run it from a launcher, it doesn't work.  I tried both with "Run in terminal" selected and deselected.

---

### Post by s_p_a_r_k_y on 2006-10-12
are you putting the entire path into the gnome desktop file?

---

### Post by djcinsb on 2006-10-12
Yes.  Here's the launcher:

[INDENT][Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=GMAT
Type=Application
Exec=/home/djc/launchGMAT.sh
TryExec=
X-GNOME-DocPath=
Terminal=true
Name[en]=GMAT
GenericName[en]=
Comment[en]=
GenericName=GMAT
Comment=
[/INDENT]
and the shell script (/home/djc/launchGMAT.sh):
[INDENT]#!/bin/sh
cd /home/djc/GMAT/bin/
gmat[/INDENT]
The executable is named "gmat" -- as if you couldn't parse it from this!  :-)  When I run with "Run in terminal" selected, I do see the terminal flash on screen.

---

### Post by encompass on 2006-10-13
So this program needs to work with many different places... hmm... could this guy use a nautilus script?
what is this program... maybe it would help to know what it does... links would help.

---

### Post by djcinsb on 2006-10-14
It's a spacecraft modeling package, still under development, used for satellite mission planning.  OS agnostic (Windows, Linux, Mac), but won't be publically available for another six months or so.  It's useful to launch it from the desktop for demo purposes, and all of the other OS's support it (including KDE on Mandriva).  I could install KDE on the demo machine, but the case is stronger for the tool if I can make it look the same everywhere.

Of course I could add a startup option to the code, but that is a pretty low priority -- system stability and precision numerics are far and away much more important.

---

### Post by encompass on 2006-10-14
Have you tried putting a linux based linux on the desktop?
ln -t original_file name_link
run that at ~/Desktop/

---

