---
title: "Launching a shell script"
date: 2011-08-04
forum: Desktop Environments
---

### Post by gargoyle60 on 2011-08-04
[SIZE=2]I have a shell script that starts some custom software (a CinCom VisualWorks image) and I want to be able to launch the .sh directly from a panel/launcher (sorry, uncertain about terminology here) that will then run, presumably within a terminal window, but without having to actually start up a terminal window beforehand.

In other words, how can I simply run my shell script by clicking on an item on my panel (or from an item within the main menu)?

I've tried adding a new panel item as both type Application and type Application in Terminal. Neither works. I've also tried specifying "bash" and "run" and "shell" followed by the qualified path and file. I'm going around in ever-decreasing circle here.

I believe I did something along these lines before under previous versions of Ubuntu but I've forgotten and now I can't figure out the correct way to run a .sh directly.

---
Ubuntu 11.04 Natty Narwhal
with Classic Desktop - Gnome version 2.32.1
Desktop PC for home use, single user, dual boot with WinXP

[/SIZE]

---

### Post by fdrake on 2011-08-04
see how to
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

make sure you got the right path of your program.
ex if it's on the desktop it should be:
command: ~/Desktop/myProgram.sh or /home/yourUserName/Desktop/myProgram.sh

---

### Post by gargoyle60 on 2011-08-04
I've followed the instructions at the address but all that happens is a terminal window quickly appears and then disappears, but nothing else.

The file permissions on my shell script are set correctly for execution.

---

### Post by fdrake on 2011-08-04
> **gargoyle60 said:**
> I've followed the instructions at the address but all that happens is a terminal window quickly appears and then disappears, but nothing else.

The file permissions on my shell script are set correctly for execution.

on the command field write

```
gnome-terminal --command="/home/your_username/Desktop/myProgram.sh"
```

---

### Post by gargoyle60 on 2011-08-04
That did it. 
Many thanks.

---

### Post by fdrake on 2011-08-04
> **gargoyle60 said:**
> That did it. 
Many thanks.

i am glad it worked out. Don't forget to mark this thread as SOLVED.

---

