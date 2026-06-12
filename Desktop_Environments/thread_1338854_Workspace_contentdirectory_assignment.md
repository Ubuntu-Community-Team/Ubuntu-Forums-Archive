---
title: "Workspace content/directory assignment"
date: 2009-11-26
forum: Desktop Environments
---

### Post by arvevans on 2009-11-26
Using Ubuntu 9.10 Gnome with 8 workspaces enabled.  By default every workspace is focused on $HOME/username/Desktop...and shows all files in that directory as icons on the screen.

Is there a way I can have each workspace focused on a different directory, and thus have the file icons from that directory shown on the screen?

Why...?  If one has several physical job oriented workspaces which are focused on doing specific tasks, these individual workspaces will probably have task-specific tools.  I would like to have the same functionality in Linux.  When I switch to a particular workspace I would like to have the tools available that are focused on function of that particular workspace.

I'm not going to go into also having the top-bar icons reflect individual workspace focus.  That can wait until we have ability to configure individual workspace personalities.

Arv
_._

---

### Post by arvevans on 2009-11-27
daily bump...

---

### Post by arvevans on 2009-11-29
bump

---

### Post by zlatkart on 2009-11-30
1. This could be done with some scripting. It wont be a real solution, it just would switch the desktop and the directory at the same time. I have two little python scripts to start with.
2. Some problems can come with this. You should be prepared.
3. I'm planning to implement this in my app. It would be nice if you would test it then (if I manage to do this).
4. This will not work with compiz. Anyway it's not a real solution (1)

---

### Post by arvevans on 2009-11-30
zlatkart

It would be interesting to see your approach to this situation.  Where would you make the changes to re-home a single desktop to something other than $HOME/[username]/Desktop?  I have tried some of the more obvious looking things in hidden config files at $HOME/[username], but the changes are not persistent, and usually break something else.

Then of course the other part of this is to allow different app-launcher icons to appear on the Gnome top-bar for each different desktop.

Short of mucking through a lot of source code, I have not yet found appropriate hooks for making the desired changes.  It does not help that there apparently is not a simple "How Gnome Works" (Gnome For Dummies...?)  document that provides a description of the desired configuration options.

Arv
_._

---

### Post by zlatkart on 2009-12-01
This script creates a symlink named Desktop to a symlink in ~/.Desktops to any directory you want (Default ~/.Desktops/Original Desktop but you can add more)

```
#!/usr/bin/env python
import os
import shutil
os.mkdir(os.path.expanduser("~/.Desktops"))
shutil.move(os.path.expanduser("~/Desktop"), os.path.expanduser("~/.Desktops/Original Desktop"))
os.symlink(os.path.expanduser("~/.Desktops/Original Desktop"), os.path.expanduser("~/Desktop"))
```You may have to log in/out after that.

Giving the name of the wanted directory-symlink as an argument to the next sccript, you can change the Desktop directory. 

```
#!/usr/bin/env python
import os
import sys
import commands
x = sys.argv[1]
os.remove(os.path.expanduser("~/Desktop"))
os.symlink(os.path.expanduser("~/.Desktops/") + x, os.path.expanduser("~/Desktop"))
commands.getstatusoutput('wmctrl -k on')
commands.getstatusoutput('echo -e "KeyStrPress Control_L\nKeyStrPress r\nKeyStrRelease Control_L\nKeyStrRelease r" | xmacroplay ":0.0"')
```Could be you'll have to press F5 after that. 

This script worked perfectly in intrepid, but somehow i have problems with Jaunty.
Maybe it's better to erase the last two lines.

Anyway this is a good start, and now you could write a script for switching the dirs with your own keystrokes. Or...

---

### Post by arvevans on 2009-12-06
Agreed that this is a start, but what is really needed is some changes to Gnome itself so that we would not have to manually swap the .Desktop definition and then re-start X to make it happen.

Hopefully, some of the Ubuntu System Programmers are watching this and might take a look at providing a way to personalize individual Desktop or Workspace environments.

When I go to my Welding and Metal Working workbench, I don't expect to see electronics test equipment (oscilloscopes, voltmeters, etc.), and when I go to my Electronics workspace I don't expect to see a Plasma Cutter, Arc Welder, and Metal Bending Brake.  Individual Workspaces or Desktops on Ubuntu should be no different.

Thanks for the ideas and code work.  It is a start, but needs to be integrated into Ubuntu.

Thanks,
_._

---

