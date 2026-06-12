---
title: "peculiar problems with apps in launchers"
date: 2009-12-07
forum: Desktop Environments
---

### Post by akashiraffee on 2009-12-07
I just installed ubuntu 9.10 last week and have added a few launchers  for my favourite programs -- mc, which is a terminal app and so did not install on the menu, and notelist, a gtk app which does not have a ubuntu package so is built from source.

They both run fine when I was  starting them from the command-line.  When I added a panel launcher for mc tho*, something gets screwed up:  mc uses F3 to view files with whatever $VIEWER is set to.   This should be less (and "echo $VIEWER" shows as less in the terminal), but instead, it uses vim in readonly mode.  F4 should edit a file with whatever $EDITOR is set to.  Again, echo shows it correctly as vim.  But F4 does nothing.

All this works properly if I just start a terminal and use the command-line.  **Does anyone know what the difference is?**

Notelist lists an index of note files and calls another program, "note", to display them.  It runs fine from the command line too, but when used with a launcher it disappears when you go to view a note.  I compiled -g and changed the launcher to "Application in Terminal" with the command "gdb notelist"; run inside the debugger this way, tho, the problem does not occur, so I cannot find the fault.

*this is the same whether I use "gnome-terminal --e mc" or "Application in Terminal"

---

### Post by akashiraffee on 2009-12-07
If you try running a shell script, either as "run in terminal" or using a command "gnome-terminal -e", you get a popup:

[B]There was an error creating the child process for this terminal
[/B]
[moment later]
Turns out the reason for that is the PATH is not set right, ie, the launcher is I think running as a different user.

---

