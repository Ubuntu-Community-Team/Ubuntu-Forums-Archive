---
title: "Window manager not working?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by kflorek on 2006-09-06
Windows do not have the top bar (no minimize, maximize, close. Can't move windows. Can't resize windows unless they have a corner resizer at the lower right. Can't get at windows behind other windows. The 4 desktops applet is not in the lower panel.

There are a lot of messages about this no title bar problem when you install Compiz. What they say to do is select a theme, and that fixes all. But I got rid of Compiz and changing themes does nothing.

  Here is how I got to this point. I installed Xgl/Compiz with Synaptic. It didn't work at all. Even the panel bars were gone. (Control-Alt-backspace time!) After copying back the backup config files for the ones I changed, I now have the symptoms I mention. It should be back to the original, but somehow it isn't. The addition to the startup programs for the session, to run a script for Compiz, has been removed.

 I have been tracking this down for many hours. Here are the relevant results:

 I reinstalled a zillion base gnome files. I have no idea which ones should do the trick, if any, but it made no difference.

 Stumped, I installed the Xfce desktop files and switched to it as the session at logon. Magically, everything was normal. But logging on with a gnome session gave the same problem.

 I created a new user, and logged onto gnome, and everything worked. !!! Log-on as myself and it does not. I doubt if installing Xfce did anything but put me on a different train of thought.

 In the non-working sessions, System -> Preferences -> Windows produces an error dialog box:
" Window manager "unknown" has not registered a configuration tool."

 In the working sessions you get a normal setup box.

 If I log-on to "failsafe gnome", everything is working and the Windows setup box does come up.

 What does this tell me? Not enough. But it does seem that the configuration files ARE fine, and there is some script that executes only when I log-on as myself, which causes the window manager to not start. So how is this possible?

 It doesn't seem like it should be hard.

---

### Post by Jussi Kukkonen on 2006-09-06
Maybe your session is saved at each login?

Anyway, running
```
metacity --replace &
```
should start metacity (and stop any possibly running non-working WM.

---

### Post by kflorek on 2006-09-07
Thanks, it worked. As soon as you run metacity, the title bar and everything else pops back on. I doubt if I would have figured it out on my own.

 Here's what I found out:

 When logging on as myself, and checking the session preferences:
[COLOR="Red"] System -> Preferences -> Sessions -> Current Session[/COLOR],
 metacity was not there. With other log-ons, it was.

Just running metacity without parameters also starts metacity, and it shows up in "Current Session." But when I logged off and logged on later I needed to run metacity again. I thought I was going to have to find out the location of the file, whatever it is, that you change the settings in. But...I changed to "Automatically save changes to session" once, and then metacity showed up on its own next time. The only thing that was going wrong was that the window manager was not being run at start up.

 I had turned "Automatically save changes to session" off at some point in debugging. I know I had it turned on for convenience at one time. It is cool to log on and see what you had open come back as you left it.

 But seeing how this works in practice, if you have "save session" turned on, and something crucial crashes, like metacity, it will not be set to run the next time you log on. That is what must have happened when I tried Xgl/Compiz and crashed everything.

 So having "save session" turned on is not a great  idea when you are experimenting! :-? IAC I know how to get back if I ever try Compiz again.

---

### Post by xmux on 2006-09-07
Hi I have the same Problem and i tried with metacity --replace , but its coming back to Desktop without Compiz, and there is a message:
Window manager warning: Log level 32: could not find XKB extension.

What can i do to get my Compiz like before?

---

