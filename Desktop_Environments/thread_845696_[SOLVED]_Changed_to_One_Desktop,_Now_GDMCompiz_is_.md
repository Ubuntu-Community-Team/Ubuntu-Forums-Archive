---
title: "[SOLVED] Changed to One Desktop, Now GDM/Compiz is broken"
date: 2008-06-30
forum: Desktop Environments
---

### Post by burgerearl on 2008-06-30
Hi,

Running gutsy with compiz enabled. I started with four desktops using cube animation to move between them.

I accidentally moved a window to an adjacent desktop, then got quite jumbled trying to move everything back (my problems were aggravated by the use of super+D to push all windows to the corners and show the desktop).

In any case, I attempted to resolve the problem by changing the number of desktops to "1". Big mistake. Immediately I was presented with a zoomed out view of one desktop (as if I was rotating the cube and held it in one position). I was inconsistently able to perform some actions by clicking.

I restarted GDM with Ctrl + Alt + Backspace, logged in, and immediately got the same view. Pressing ctrl+alt+delete got me a responsive shutdown menu - I was able to click restart and boot XP to post about the problem.

Any tips? I'm guessing I'll need to boot safe mode or a command line and manually edit some config files, but I have no idea where to start...

Thanks!

---

### Post by immerohnegott on 2008-07-02
Well, you could try to boot up log in, hit CTRL+ALT+F2 (or any of the F keys 1-6 will work) to bring up a TTY, and use

```
top | grep compiz
``` 

you may have to CTRL+ALT+F7 after you run that to get back to the GUI, and then go back to the TTY for top to find Compiz (I ran into that particular trouble when Compiz was acting up on one of my machines. This is the process I used to at least get X to a working state so I could fix things).

when top spits out the Compiz' PID number, hit q to get out of top and do

```
sudo kill *pid here[I]*[/I]
```

I can't remember if the sudo is necessary, but I figured I'd put it in there just in case.

ANYWAY, once Compiz is stopped, you should be able to CTRL+ALT+F7 back into X and switch the settings back to where they should be in the comfort of a graphical environment ;-)

Sorry it seems complicated, but this way you shouldn't have to fuss with config files and all that jazz.

---

### Post by burgerearl on 2008-07-02
Thanks for the reply.

I tried this, but it didn't work. I was able to access a command line with ctrl+alt+F2, but top didn't return compiz as running.

I have gnome-do installed and tried using it to run compiz. Running compiz from gnome-do caused the desktop to temporarily appear as normal, but it returned to the single cube face after 1-2 seconds.

My best guess is that I need to change the number of desktops back to four, can I do that from the same command line?

---

### Post by burgerearl on 2008-07-05
After rereading your post and mine, I came up with an idea that worked.

After starting top, I returned to the GUI, started compiz with gnome-do, and returned to the command line. Voila - I now had PID's for compiz. Killing them allowed me to gain a properly functioning GUI.

I couldn't locate the option for changing the number of desktops (it seems the context menu for the workspace icon in the bottom right of the screen runs off of compiz), so I just disabled the cube completely.

This is fine with me because I never really used multiple workspaces anyway, but if somebody could post how to fix the number of spaces it might help somebody with the same problem in the future.

Thanks!

---

