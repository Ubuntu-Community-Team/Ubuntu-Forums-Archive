---
title: "Creating custom logout action from gnome"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by JetPack on 2007-12-01
I am running Ubuntu 7.04 (with gnome) and I would like to be able to run a custom comand just before the default action when I click on the Logout button (the "power" button on the top right tool bar).

I see in gnome configuration (using terminal command gconf-editor) that there is an option for Logout, but I don't want to muck about with this until I know what I'm doing (yeah, like that's ever stopped me before..!).

I want to be able to insert a command just before gnome executes it's default "logout" script (as well as applying that to restart and shutdown).

Any ideas..? Thanks in advance.

---

### Post by mike2357 on 2008-04-12
This is not too hard to do if you can work a bit with the command line.  The strategy is to make a new button that calls a script that performs your custom actions first, and then invokes the regular gnome logout window.  Here's how:

1.  Make a new file (I'll call it /home/yourname/bin/logout) with the following:

#!/bin/sh
#Put your custom commands after this line

# The next line is the regular gnome logout command
gnome-session-save --kill --gui




2.  Set permissions on the script:     chmod 755 /home/yourname/bin/logout
3.  Right-click on an empty area of your panel and select "Add to Panel"
4.  Click on "Custom Application Launcher" at the top of the window.
5.  In the Command box, type your script name, which in this example was
    /home/yourname/bin/logout
6.  In the Name box, type Logout or Quit or some other name of your choosing
7.  Optional:  Click on the icon area to the left and just above of Name, and choose a new icon.  The one I picked was /usr/share/icons/Human/24x24/apps/gnome-logout.png
8.  Click on close.

Your panel should now show a new icon.  If you click on it, it should execute your custom commands and then invoke the regular logout window.  The only glitch I've found is that if after the logout window shows you click "Cancel", your custom commands will already have run.

If you wish, you can remove the original Quit icon from your panel.

---

### Post by russo.mic on 2008-04-12
Kudos on the great instructions!

---

