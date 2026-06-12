---
title: "i don't even know what to call this problem... something wrong with X session"
date: 2006-09-06
forum: Desktop Environments
---

### Post by shoagun on 2006-09-06
Sorry ahead of time if I don't provided the information needed to solve this problem, but I'm not even sure what information to provide, other than my own observations.

I just moved and hadn't used my Ubuntu machine for a week or so.  Then, yesterday, I started it up and found that when I open an X session (with XGL+compiz) i not longer have 4 desktops.  Also, windows I open do no have the top bar (the one with the minimize,maximize,close), and I can't move windows around.  The only thing I could think to do is update everything.  But that didn't work.  

Since I didn't do anything to cause this problem, I'm guessing it was some update I got last time I had used the machine.  I've tried looking on the forums for similar problems, but it's hard because I don't even know what to call this.

---

### Post by kflorek on 2006-09-06
There are a lot of messages about this no title bar problem when you install Compiz. What they say to do is select a theme, and that fixes all. I hope that helps :)

  I installed Xgl/Compiz with Synaptic. It didn't work at all. Even the panel bars were gone. After copying back the backup config files for the ones I changed, I now have the same symptoms you mention. It should be back to the original, but somehow it isn't. The addition to the startup programs for the session, to run a script for Compiz, has been removed.

 I have been tracking this down for many hours. Here is the relevent result:

 I reinstalled a zillion base gnome files. I have no idea which ones should do the trick, if any, but it made no difference.

 I installed the Xfce desktop files and switched to it as the session at logon. Magically, everything was normal. But logging on with a gnome session gave the same problem.

 I created a new user, and logged onto gnome, and everything worked. !!! Log-on as myself and it does not. I doubt if installing Xfce did anything but put me on a different train of thought.

 In the non-working sessions, System -> Preferences -> Windows produces an error dialog box:
" Window manager "unknown" has not registered a configuration tool."

 In the working sessions you get a normal setup box.

 If I log-on to "failsafe gnome", everything is working and the Windows setup box does come up.

 What does this tell me? Not enough. But it does seem that the configuration files ARE fine, and there is some script that executes only when I log-on as myself, which causes the window manager to not start. So how is this possible?

---

### Post by bulldog on 2006-09-06
this is because compiz relies on csm instead of gconf now...
so you must start compiz differently, basically...

Go to system -> prefs -> sessions -> startup programs and put in "/usr/bin/compiz-start" and remove all other options pointing to compiz.(instead of whatever you use to start compiz currently)
Do the same in tab current session of your session menu.


Logout and login again.

Also make sure you have "csm" installed and all other packages are upto-date....
This app. csm is used to alter the plugin settings.

Then run "csm" in the terminal to change any of the settings for any plugin....

If changes in csm don't have any effect, then go into the terminal and type "sudo chmod 755 ~/.compiz -R"
If it complains about a folder being missing, then create a ".compiz" folder in ur home folder and run the command again....

Then it should all work again....

---

### Post by shoagun on 2006-09-06
Thanks bulldog, your solution worked.  

Though, I'm getting a little annoyed by compiz.  Everytime I update, it causes problems.  Do they even bother to test their udates before distributing them??

---

