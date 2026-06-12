---
title: "help  using kill command"
date: 2006-06-11
forum: Desktop Environments
---

### Post by syxbit on 2006-06-11
if i run a program such as ```
dc
``` and want to kill it, i would just run ```
ps
```, see the PID, and type ```
kill -9 <PID>
```
but a guy on this forum mentioned this
> "kill -9" is a bad habit and can cause you problems. Only use -9 if you know exactly what you are doing and nothing else works.

When you kill a process you want it to "clean up". kill -9 does not let it clean up

but when i type kill <PID> nothing happens.
It doesn't give an error, but with i type ```
ps
``` dc is still there
i'm still not very good at understanding the manuals and --help, so if someone could explain
thanks

---

### Post by Lokken on 2006-06-11
Generally, the best way to find a process is to pipe ps (or ps aux) through grep, like so... (I'll use ESD, because I've always had to manually kill it on a fresh install to log in for the first time ;))

ps aux|grep esd
ps|grep esd

Filters out some spam. kill <PID> should work fine for most things. killall processname (like... killall gnome-panel) is useful sometimes.

You really shouldn't have to use any other arguments for the kill command.

Sorry if it's not much help.

---

### Post by InsanePenguin08 on 2006-06-11
I find, if what you're trying to kill is visible in the GUI, just do:

```
xkill
```

And it will ask you to click on the toolbar of whatever you want to kill, simple as that.

---

### Post by syxbit on 2006-06-11
thanks for the input.
i know a bit about xkill, but i need to do this in the terminal, so i can kill bg stuff
i don't see a difference betwee running it through grep or not, i still get very limited answers
if i run "ps -e" then i get tons, but if i run just "ps" it only lists this
  PID TTY          TIME CMD
25453 pts/1    00:00:00 bash
25797 pts/1    00:00:00 units
25896 pts/1    00:00:00 ps

after i type 
kill 25797
it accepts it (doesn't give an error) but if i type "ps" again, it still displays the same thing
only when i do
kill -9 2579 does units stop showing up in "ps"

any ideas ?

---

### Post by syxbit on 2006-06-12
come on guys.
help me out

---

### Post by elbryan on 2006-06-12
A nice way to look for your process in background is to use pstree..

Usually I associate this command with killall (that kill the process and his child processes).

Maybe you can try this way, otherwise you could do a ps aux that gives you more information about the process you are running...

---

### Post by dglock on 2006-06-12
I don't know if you are in kde or gnom but in kde, press ctrl esc and you will get a nice process table. 
 
  For processes running as root you can then use a console and as root use kill pid.

don

---

### Post by DoktorSeven on 2006-06-12
To answer your question: yeah, if nothing else you try kills the process, go with the -9 (SIGKILL) signal.  Basically, people warn against using it for every occasion because it does shut down the process very suddenly, which can cause some problems with applications that need to clean up properly.

But if it's just some random, stuck process that you need to destroy, go ahead with the -9.  Just make sure you always try other, more gentle methods first.

---

### Post by syxbit on 2006-06-12
i'm not too good at reading man pages.
so 
kill -SIGKILL <PID>
is the same as 
kill -9 <PID>
?

---

### Post by DoktorSeven on 2006-06-12
Yep.  Same thing.

---

### Post by syxbit on 2006-06-13
i just read recently about the command
jobs
this is essentially the same as 
ps
but instead of listing jobs by a PID, it lists them as a job #
to kill jub #1 you'd type
kill %1
from what i've read, this is identical to doing 
kill <PID>
but it doesn't seem to work the same way for me.
if i kill by PID it accepts the command, but doesn't kill it (i need to do a kill -9) but if i kill by job#, it works perfectly.
is this a bug ?

---

