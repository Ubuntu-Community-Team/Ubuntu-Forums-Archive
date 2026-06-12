---
title: "Login screen not appearing with login box"
date: 2008-04-28
forum: Desktop Environments
---

### Post by xeonxeon on 2008-04-28
This is a suggestion to assist with anyone who is getting a login screen that shows no login space.

This was happening on my 2x xeon with Nvidia Quadro set up.

It was impossible to reposition the display to show more than "Ubu" and reinstalling video drivers showed that this seemed to be behind the problem - but would not cure it.

However - if you type in your normal login - then tab - then your password - then return - although you see nothing you are typing - it still logs you in.

---

### Post by k_dv700 on 2008-05-12
You probably have a login resolution problem similar to me.  
I got it solved by a hint of Max Schukin:
First log on (blind if necessary: user name <enter> then password <enter>)

Press Alt+F2 and enter:
gksudo gedit /etc/X11/xorg.conf
(you are prompted for the root password now)
Scroll down to the Screen section and add the following lines:
        SubSection "Display"
             Depth 24
             Virtual 1024 768
        EndSubSection

Change 1024 768 to your resolution.  
In my case the lines were already present, but for some reason it said 1600 1200

---

