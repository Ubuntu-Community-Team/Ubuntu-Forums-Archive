---
title: "Panel freezes"
date: 2009-08-17
forum: Desktop Environments
---

### Post by Hans-N on 2009-08-17
I've been recently frustrated to have my top menu freeze (I believe this is run by GNOME Panel).  If the freeze occurs before the screen saver kicks in, the menus are all displayed but clicking on them does nothing . If the screen saver activates, the top menu comes back as blank when the screen saver deactivates.

I have not noticed any particular application which causes the problem.  Almost always I have a terminal window running python code (which usually runs one processor core at 100% and the lion's share of my RAM), and often have Kile, JabRef, Firefox, System Monitor, and document viewer open.  Curiously the problem seemed to only start a few weeks ago, so I can't imagine what has changed.

GNOME 2.26.1, Ubuntu 9.04 .  

Is there a workaround, fix, or other suggestions?

(Edited to add, when I shut down, I get a message saying Panel is not responding.)

---

### Post by Hans-N on 2009-08-22
I have a partial solution which does not involve restarting every few days.  I put a script on my desktop which runs the command "killall gnome-panel".  This restarts the panel.

1. Create a text file with a name like restartPanel.sh with the following commands:
#!/bin/bash
killall gnome-panel

2. Save it to the desktop (unless there's a way to ensure other windows will be open, the desktop may be the only accessible place).

3. Make the file an executable by running the command in the terminal
chmod +x /Desktop/restartPanel.sh

4. If the panel freezes, run restartPanel.sh.

I would still like to know what is causing the problem.  It seems to happen when I have very little memory left, but otherwise I don't see a specific cause.  My commandline-fu is not strong, so there may be some slick and easier way to do this, but it does seem to work for my problem.
[FONT=Courier New]

[/FONT]

---

### Post by dynamics on 2009-09-04
I too am facing the same problem and the applications I use are similar to yours.... It started a couple of weeks ago, say 1st or 2nd week of August 09. I thought its because of combination of python-Qt4 applications (Don't ask me what made me to think like that, because even I don't know)....
What I do is, I had set up a shortcut key for gnome-terminal invocation. I use that to open a terminal and search for the 'gnome-panel' process id and then
$ kill -9 [process id of gnome-panel]

By the way I can navigate between the windows using Alt+Tab when the panel is frozen.

---

### Post by dynamics on 2009-09-04
I learnt from Prof Google and tested the fact that gnome-panel freezez when I open more than 8 windows when it is in vertical position......
and also found that patches are available for this....
have to for dig more details... will post here if it get fixed...

---

### Post by dynamics on 2009-09-05
Hey,

I found that the bug is revisited in Aug-09 update of Jaunty.....Geeks are working towards fixing this..
I tested it also. The description is...
When you have a vertical gnome-panel and try to open more 7 windows (means when you open the 8th window) the Panel Freezes. Then you have to close windows to make the total number of open windows down to 7 and kill gnome-panel in terminal.
The maximum number of windows is 7 per Desktop.....
The bug has a fix and you have to apply the patch discussed in this thread

[http://ubuntuforums.org/showthread.php?t=968901](http://ubuntuforums.org/showthread.php?t=968901)

Then lock the panel update so that it will not be altered in later updates.

---

### Post by AsoSako on 2009-09-22
I have the exact same issue as the one described by the thread creator, however I do not happen to have any vertical Gnome-Panels open or 8 windows open when it happens as proposed by dynamics.  I don't know if both of these are the same issue, but it appears they may be different since some other posters too did not describe anything such as a vertical bar.  

From what I have noticed the freezing seems random, but appears to usually happen close after login, but not every time, it just seems entirely random.  Both my top and bottom bar freeze, except surprisingly the top right section where I have my name and I can Shut Down/Restart and all that stuff.  This does not include the task-bar or the calendar, they freeze as well.  killall gnome-panel seems to do the trick, however this can only be a temporary solution.

Does anyone have any idea on how to resolve this issue?

---

### Post by dynamics on 2009-10-19
Hi

Use the script in the following web page

[http://www.osfight.de/archives/92](http://www.osfight.de/archives/92)

Download the script and run the commands.

The down-gradation takes a long time but its worth a try.
Don't forget to lock the future update for panel.
 
You may find Yahoo german to english translator useful ;-)

---

