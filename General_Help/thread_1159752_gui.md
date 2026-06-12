---
title: "gui"
date: 2009-05-15
forum: General Help
---

### Post by kuipou on 2009-05-15
how could i create a gui for a command like shut down

---

### Post by mb_webguy on 2009-05-15
What sort of GUI do you want?  The User Switcher Applet and several other panel applets already handle that for you.

You can use zenity to display GUI dialogs from shell scripts...

---

### Post by kerry_s on 2009-05-15
first you need to put a visudo for no password or it will lock.

in terminal:
**visudo**
put:
**%users ALL=NOPASSWD: /sbin/shutdown**
or
**gksudo your-editor /etc/shutdown.allow**
put your name

then for your command use:
halt> **sudo shutdown -h now**
reboot> **sudo shutdown -r now**

use> man shutdown <in the terminal to learn more.

---

### Post by kuipou on 2009-05-18
well it was more in the line of displaying a box with how much hour/min i wanted it to shut down in or when i wanted to make it autoshut down

---

### Post by mb_webguy on 2009-05-18
Here's a very simple version of what I *think* you want to do.  I saved the following script as "shutdown_timer".```
#! /bin/sh
dowhatjohn=`zenity --list --title "Shutdown Timer" --text "Please select an action"  --column "Action" Reboot Shutdown Cancel`
if [ $dowhatjohn != "Cancel" ]
then
   dowhenjohn=`zenity --entry --title "Shutdown Timer" --text "Please enter when the computer should $dowhatjohn"`
   if [ $dowhatjohn = "Reboot" ]
   then
      dowhatjohn="shutdown -r"
   else
      dowhatjohn="shutdown"
   fi
   gnome-terminal -x $dowhatjohn $dowhenjohn
fi

```
Note that there's not really any validation of the time given.  If you give it an invalid time, the script will simply fail.  You could modify this script easily to use a list dialog instead of an entry dialog to give some options when to shutdown/reboot, which would make it a bit more robust at the cost of flexibility.  Also, unless you allow shutdown to be run by a normal user (as described by kerry_s), the script must be called with "sudo".  

(And in case you're wondering, I'm throwing up a terminal because the shutdown message is a broadcast message, and you can't simply direct the output of the shutdown command to a zenity dialog.)

You could add a launcher for this script on your Gnome panel by simply using "sudo /path/to/shutdown_timer" (substituting the actual path to the script, of course) as the command.  And remember to make the script executable with "chmod +x /path/to/shutdown_timer".

---

### Post by HermanAB on 2009-05-18
Well, if you want to go totally overboard, use Perl, Glade and Gtk2+.

---

