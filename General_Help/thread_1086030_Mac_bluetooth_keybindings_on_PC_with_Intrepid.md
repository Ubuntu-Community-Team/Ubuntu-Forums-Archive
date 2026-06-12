---
title: "Mac bluetooth keybindings on PC with Intrepid"
date: 2009-03-03
forum: General Help
---

### Post by demothen on 2009-03-03
I'm having a bit of a problem with my wireless mac keyboard, it's the silver model with no number pad.  My direction arrow keys do not see to be doing anything correctly.  This is a fresh Intrepid install, and I used the bluetooth configuration icon to set up the keyboard (after several tries, it successfully linked up).  The up arrow key was originally set to print screen, but I disabled that keyboard short cut, the other buttons still do not work.  I'm not real sure where to find key binding configuration in Ubuntu.
Thanks!

---

### Post by wet-willy on 2009-03-03
Likely the appropriate section of /etc/X11/xorg.conf file needs to be adjusted/edited.
You can search available packages through synaptic using the search utility for software that allows you to manipulate this file to use the proper keyboard layout and set up keybindings.
One thing you can try is to run the actual configuration tool by running this command: *sudo dpkg-reconfigure xserver-xorg*, this will ask all types of questions regarding video card, monitor refresh rates, keyboard type, mouse etc. This configuration utility set's up the /etc/X11/xorg.conf file, you can just hit enter to accept default answers to questions you don't understand, or if you prefer to leave things as they are and just make neccessary changes to the keyboard section. You will be asked if you want to write the changes or not at the end, so no need to worry about messing things up running it, you can abort.

---

