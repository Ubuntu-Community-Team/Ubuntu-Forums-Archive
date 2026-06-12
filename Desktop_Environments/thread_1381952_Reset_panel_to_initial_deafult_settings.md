---
title: "Reset panel to initial deafult settings"
date: 2010-01-15
forum: Desktop Environments
---

### Post by Geir B-J on 2010-01-15
Hi. My panels have disapeard, and it`s my display is not filling the screen. The largest resolution i can get is 800x600. I`m quite new to linux, but i`we tried to reset the panels the most obvius ways. I watnt to reset to deafult settings whidout reinstaling. The tips i found on the net didn`t help, probably because of my lack of programing. So if you awnser me, pleas discribe it sipley.

Hoping for awnsers
Geir

---

### Post by d3v1150m471c on 2010-01-15
[http://ubuntuforums.org/showthread.php?t=1381916](http://ubuntuforums.org/showthread.php?t=1381916)

read what i wrote on my post on that thread. that should help

---

### Post by hariks0 on 2010-01-15
Delete the following folders from your /home:-

.gconf, .gconfd, .gnome2 

[Note the period before each foldername] They will be hidden by default. Press Ctrl+H to diplay them. If you do not have a GUI way to access these try Crtl+Alt+F1 to use the CLI.

On restart the settings and panels will be the default after fresh install. I have done this myself after messing things up with a theme.

---

### Post by Geir B-J on 2010-01-15
Thanks, but i get question about my password, that i have forgotten. Are there any other ways?

---

### Post by d3v1150m471c on 2010-01-15
system > administration > users and groups. Make a new user and don't lose your password. Hopefully from the new user when you login to it, you can transfer most of your files in your home folder that you need. *crosses fingers*

---

### Post by hariks0 on 2010-01-15
Then you need to access [this post]("http://ubuntuforums.org/archive/index.php/t-3609.html") first to reset your password.

Don't worry. You can do this as I have done this.;)

---

### Post by d3v1150m471c on 2010-01-15
> **hariks0 said:**
> Then you need to access [this post]("http://ubuntuforums.org/archive/index.php/t-3609.html") first to reset your password.

Don't worry. You can do this as I have done this.;)

.......*facepalms* so much for security. that makes ophcrack look like a joke...

---

### Post by Geir B-J on 2010-01-15
It worked! Thank you alot! :D. 
But my other problem is still there... :(
The largest resolution of my window is still 600x800 dots, and my screen is a bit larger.

---

### Post by Geir B-J on 2010-01-15
I tried to fix the reselution in settgs > display, but the largest chois is 800x600, and it do not fill my screen.. Got a tip?

---

