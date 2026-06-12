---
title: "Audacity Problem"
date: 2006-03-25
forum: Desktop Environments
---

### Post by mojohn on 2006-03-25
I have installed and uninstalled Audacity 3-4 times today. 

When I run Audacity from the command line immediately after install, it works fine. I can exit and restart Audacity several times and everything works until I close the Terminal window.

When I reopen the Terminal window and run audacity, I get the following error message:
[INDENT]
There was an error initiating the audio i/o layer. You will not be able to play or record audio. Error: Host error. [/INDENT]

Interestingly, I get this same error if I try to start Audacity from the Applications ... Sound & Video menu even if I haven't closed the Terminal window after an install. And yet, when I close Audacity and re-start it from the Terminal, it works fine. That is, of course, until I close the Terminal and re-open it.

Any ideas why it works from command line until I close the Terminal window but not under any other circumstances?

Thanks John

---

### Post by Mustard on 2006-03-25
I wonder if its an esd process running in the background for the sound server.  You might try going to System>>Preferences>>Sound and disabling the sound server and then explicitly killing any esd process that might be running.

To look for any running esd process do this..

```
ps -e | grep esd
#ps with the -e option will list all process. 
#grep will filter that list to only show those process 
#that contain the string 'esd'
```

To kill the esd process (if it exists)..

```
killall esd
#killall kills running processes by name
```

Then test audacity from the menu.

---

### Post by mojohn on 2006-03-26
Mustard, I tried your suggestion and it worked!  Thanks much.

If I could impose for another question. In order to make this work full-time, what is the convention to have Gnome run killall esd before the audacity command in the menu editor? 

Thanks!

---

### Post by Mustard on 2006-03-27
[QUOTE=mojohn]Mustard, I tried your suggestion and it worked!  Thanks much.

If I could impose for another question. In order to make this work full-time, what is the convention to have Gnome run killall esd before the audacity command in the menu editor? 

Thanks![/QUOTE]

I think if you just disabled the sound server altogether, then there shouldn't be any esd processes running.  Of course this means that you won't get all those drum sounds and stuff when you navigate around your menus etc.  I'm not sure what the permanent answer is, but I will keep playing around and see what I come up with.

---

