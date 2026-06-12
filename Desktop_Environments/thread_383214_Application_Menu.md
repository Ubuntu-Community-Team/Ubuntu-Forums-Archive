---
title: "Application Menu"
date: 2007-03-13
forum: Desktop Environments
---

### Post by Gorbachev on 2007-03-13
So, I have a few questions for everyone.

I decided to move my installation of WolfET to /home/Games, and I want to make the following links link to the new location but I do not know how to edit them.

/usr/local/bin/et and etded

How do I fix this?

I have a few more questions but I forgot them.. so I'll be back.

Ok, so. Let's say I hit CTRL + ALT + Shift F1, how do I get gnome to load back up?

Also, I cannot get Nvidia Settings to make my computer remember what resolution to use. It always resets itself after a restart.

edit: I just realized this is the wrong area to post this. Way too many places to post!

---

### Post by Gorbachev on 2007-03-13
:confused: help??

---

### Post by Gorbachev on 2007-03-14
Once again, I find myself bumping my unanswered thread..

---

### Post by 16777216 on 2007-03-14
While I am not sure about the WolfET links, I would suggest searching for information on "symlinks".

I can however tell you about the TTY switching. (  Ctrl+Alt+F1 ) 
Ctrl+Alt+F1 through F6 I believe are text terminals I could be wrong.
Ctrl+Alt+F7 is the default X server and thus how you return to Gnome.
I can't rember about F8 though F12 and as I am currently playing a movie for my kids I am unable to test it to see but I recommend you do as it can cause no harm.
I believe in some cases they are used as different user X logins so that a quick hotkey is all that is needed for fast user switching , I am not sure about Gnome with Xnest but I know this is how KDE does user switching.

To get nVidia settings to remember your settings  you have to run it with root  permissions in a terminal type or cut and past this ```
sudo nvidia-settings
```  [ Tip: you can select text with the mouse then put the text cursor where you want to paste and just push the mouse wheel like a button to paste. ]
Your changes should stay then.
The reason for this is that the configuration file for the X server is a protected file that is owned by root, so for nVidia settings to make changes it needs to be run as root also called the super user thus sudo. ( Super User DO )

---

