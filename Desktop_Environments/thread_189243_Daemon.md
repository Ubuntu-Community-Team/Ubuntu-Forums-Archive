---
title: "Daemon"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Dave N on 2006-06-05
Hi Folks,

Is it possible to have an icon displayed when a daemon is running?
Just want a visual reference to see whether a specific daemon is running or not.

Thank you

---

### Post by nanotube on 2006-06-05
[QUOTE=Dave N]Hi Folks,

Is it possible to have an icon displayed when a daemon is running?
Just want a visual reference to see whether a specific daemon is running or not.

Thank you[/QUOTE]
hmm, well, it seems the easiest way to do it would be to edit the daemon startup script (probably located in /etc/init.d), and add to the startup procedure a "zenity --notification" command ('man zenity' for more details on how to use zenity), and also add a kill command to remove the zenity notification to the stop procedure.

well, maybe it's not all That easy, but that's all i can think of, if the daemon doesn't come with its own applet. maybe someone else has a better idea.

what's the daemon in question, anyway?

---

### Post by Dave N on 2006-06-05
>  what's the daemon in question, anyway?

Thanks I'll look at that.
It's no-ip running as a daemon, starting script is no-ip.conf

Appreciate the help..

---

### Post by 23meg on 2006-06-08
I once accomplished this via detecting whether the daemon is running or not with a script, and using its output to determine which icon is displayed on the desktop. If the daemon was off, it would display a transparent image (thus in effect, no image), and if it was on, an opaque one that's descriptive for the task. 

It was a very rough hack; I used the cp command to overwrite the desktop launcher's icon every time and since there's no command to tell Nautilus to refresh the desktop that I know of, I had to manually refresh it with F5 to see the most recent status of the daemon at any time. Although perhaps not the most comfortable method, it worked. Here's the part of script used to check whether the daemon is running: 

```
#!/bin/bash
ps -e | grep PROCESS_NAME
x=$?;
if [ $x -eq 1 ]; then
        DO THIS
else
        DO THAT
fi
```

PROCESS_NAME is obviously the process name of your daemon. It will "do this" if the daemon isn't running, and "do that" if it is. You can insert the appropriate cp or other command to your liking.

Note that the check is only done at the time the script is run. I used this to toggle the daemon **and** to have some kind of indication of its running status. If you just want the latter you'd have to run the script every time you wanted the status checked. It can perhaps be integrated into conky via its shell mode to do periodical updates and thus show the latest status; I haven't tried this but it would be cool.

---

### Post by scxtt on 2006-06-08
cons are good at running scripts in the background ...

---

