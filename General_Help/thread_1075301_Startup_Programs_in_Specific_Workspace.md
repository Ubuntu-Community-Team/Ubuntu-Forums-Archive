---
title: "Startup Programs in Specific Workspace?"
date: 2009-02-20
forum: General Help
---

### Post by Kissell on 2009-02-20
After Ubuntu opens, I always do the same thing, I load up the common programs I use, and then I move them to their own workspace. For instance, I like to have a terminal window always open already, but I don't want it cluttering up the open programs bar on my main workspace.  So I've manually been opening it at reboot, maximizing it, then moving it to workspace 3.

Is there a way to automate this?  I know I can auto-start programs via the SESSIONS editor, but I don't know how to make it start on Desk 3.  Everything I edit in SESSIONS ends up on Desk 1 at startup.  

NOTE: I'm using default gnome config of Ubuntu 8.10.

---

### Post by heindsight on 2009-02-20
I've often wondered about this, but I've never seen any way of actually doing it. What I'd also like is to be able to configure things in such a way that if I'm currently on Desk 3 and I launch firefox, and then immediately switch to Desk 2 (before firefox completely starts up), then I want firefox to start on Desk 3 instead of having the firefox main window open up on Desk 2.

---

### Post by yeleek on 2009-02-20
Not done it - but I know kstart works in KDE.  How about the Compiz place windows plugin with fixed window placement?  That appears to allow viewpoints.

[http://wiki.compiz-fusion.org/Plugins/Place](http://wiki.compiz-fusion.org/Plugins/Place)

Regards

---

### Post by Kissell on 2009-02-20
I've wanted that with firefox too...

As far as the compiz thing...  Place Windows looks like it might be able to do this...  not sure...  if it can then it's not obvious to me how to make it do it.

---

### Post by yeleek on 2009-02-20
Give it a go - create via compiz a rule either for a specifically named window (title) or class (all conky for example).  And then specify where you want them to start in relation to X / Y.

Regards

---

### Post by heindsight on 2009-02-20
hmmm, such a pity that my 4 year old lappy is just too weak to run compiz.

---

### Post by sdennie on 2009-02-20
It's possible that there is a better way to do this but you can do it with metacity if you use wmctrl and wrap commands in scripts.  For example, to make firefox always be on workspace 2, I use:

```

#!/bin/bash
wmctrl -s 1
firefox --new-tab $@ &

```

That's just an example but, wmctrl is a very useful tool for managing windows and workspaces.  Check the man page.

---

### Post by Kissell on 2009-02-20
I wouldn't mind doing it this way, but it didn't work for me.

I installed wmctrl and copied your script to a new file and made it executable.  I think ran the file and firefox opened in my current workspace (not workspace 2).

---

### Post by Scubdup on 2009-02-20
Utter n00b here, but thought this sounded like something I'd like to do and found this:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=969424](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=969424)

---

### Post by yeleek on 2009-02-20
That confirms Place Windows works - good spot :)

---

### Post by Scubdup on 2009-02-20
It also mentions something called [devilspie]("https://help.ubuntu.com/community/Devilspie") which might help.

---

### Post by Kissell on 2009-02-20
Place windows worked for me...  although it only lets me position the window, I'd prefer it open maximized.

Anyway, much closer to my goal now.  

I've attached a screenshot of my settings.  These settings will cause the terminal to open on workspace 3 and system monitor to open on workspace 4.

NOTE: This has nothing to do with "at startup", you still have to load the programs to startup in the sessions launcher.  Also, this controls where that app loads, so EVERY time you load gnome-terminal or open a terminal window it will ALWAYS open it on workspace 3.  I'm okay with that, but thought it was important to mention, cause some people might not like that.

---

### Post by Scubdup on 2009-02-20
Sorry to harp on, but [this tutorial about devilspie]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/") says it will maximise windows.

---

### Post by spedax on 2009-02-20
anyone got this working decently? 

Would be nice.

edit: tried that tutorial, didn't work for me.

---

### Post by Kissell on 2009-02-20
Actually, what was screwing mine up from maximizing was I configured both of those boxes...  you only need to configure the bottom box for fixed viewport...  and not the top box for fixed window positions. 

Also, on the previous tab I set placement mode to maximize.

This now opens each of the programs I have specified in the workspace (viewport) i want them to open on, and opens them maximized.

The toughest thing for me that made this non-obvious, was that I didn't realize what a viewport was.  I was calling them workspaces.  If I change my terminology to call them viewports, then it becomes more intuitive on how to use compiz place windows.

---

### Post by TehLuckOne on 2011-09-05
I still don't understand what viewport I need for which workspace. And do I need to edit both the X and Y or only X. I was actually wondering if someone could give the viewport values voor workspace 1,2,3 and 4? I would appreciate that.

(I'm running ubuntu 11.04 btw)

---

### Post by ManualSparrow on 2011-09-05
You can use Devil's Pie to do that easily - just set a rule for Firefox, for example, that says to move it to workspace 3 when it launches. GDevilsPie is in the software center - it's about 4MB and let's you set it up graphically. It's the same result as compiz, but lighter if you're not going to use the other effects.

---

