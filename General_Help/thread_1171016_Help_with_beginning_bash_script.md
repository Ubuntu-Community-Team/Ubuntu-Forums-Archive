---
title: "Help with beginning bash script"
date: 2009-05-26
forum: General Help
---

### Post by rugburns499 on 2009-05-26
If I write a script that looks like this:

#!/bin/bash
firefox &

and run it, it opens firefox.  However, if I run "xterm ~/script", xterm opens and runs the script, but I don't get firefox.  How come?  Can I make it work, so that when I run "xterm ~/script" xterm closes but firefox stays open?

---

### Post by HereInOz on 2009-05-26
Not sure what you are wanting, but this may help. 

Write your script, making sure that you set the permissions for it to be executable by you, then right-click on the desktop, select "Create Launcher", select Application, browse to the script and enter that as the command.

You will then have an icon on the desktop which will launch Firefox (or whatever your script does), and it will not be dependent on a terminal window remaining open.

Is this what you seek?

---

