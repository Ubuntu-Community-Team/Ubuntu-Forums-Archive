---
title: "Remove all panels"
date: 2007-10-15
forum: Desktop Environments
---

### Post by Stibily on 2007-10-15
[FONT="Trebuchet MS"]Hi.

I have recently installed Avant Window Navigator on my Ubuntu 7.04.
I have set up all the launchers that I require, therefore I have no need for the top panel anymore.

How can I remove the last panel on my desktop? The option is greyed out as if it's saying you must have at least one panel present. Is there a way around this? Also, if I were to remove, could I then bring it back or would this prove awkward?

Many thanks.
::Tom[/FONT]

---

### Post by spekkie on 2007-10-16
Go to preferences --> sessions. Click on the 'Current Sessions'-tab and search for gnome-panel. Remove gnome-panel and on the 'Session Options'-tab click on 'Remember currently running applications'. The next time you log in the currently running applications will start up. So, before you click on 'Remember currently running applications' make sure that there are no applications running you don't want at startup.

---

### Post by Stibily on 2007-10-16
Brilliant! However, I just tried bringing up the command box (ALT+F2) and it doesn't load! I have terminal access as I added it to avant but that's all I have. Do you know why?

Many regards.
::Tom

---

### Post by spekkie on 2007-10-17
I didn't notice it. I have the same problem. It's the 'gnome panel run application dialog' and part of the gnome-panel. 

You can install [gmrun]("http://sourceforge.net/projects/gmrun") and use [this]("http://www.captain.at/howto-gnome-custom-hotkey-keyboard-shortcut.php") guide to setup your keyboard shortcut.

---

### Post by jfinkels on 2007-10-17
When I wanted to remove all panels from the GNOME desktop, I just removed all except one, and then made that one autohide so that it was completely offscreen. I sat the auto-unhide timeout to a very large integer, so the panel existed but was offscreen and would never unhide itself!

---

### Post by LaRoza on 2007-10-17
If you are like me, and don't want icons, panels or things on the desktop, you might like Fluxbox.

---

### Post by Stibily on 2007-10-18
Thanks for the replies.

spekkie, I installed gmrun and strictly followed the keyboard shortcut instructions but never works. I have tried this with all combinations with disabling the default Alt+F2 run command, restarting the computer, and even trying other key variants but all to no avail. Any ideas?

Regards.
::Tom

---

### Post by spekkie on 2007-10-20
I disabled the default shortcut with 'preferences' --> 'Keyboard shortcuts'. After that, I followed the guide to enable the new shortcut. I didn't need to restart the system.

---

