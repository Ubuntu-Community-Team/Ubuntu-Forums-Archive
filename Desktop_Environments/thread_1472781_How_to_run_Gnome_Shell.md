---
title: "How to run Gnome Shell"
date: 2010-05-04
forum: Desktop Environments
---

### Post by tomreid on 2010-05-04
Hi

I wanted to try this out. 

Installed it by running: 
sudo apt-get install gnome-shell


But how do you actually start Gnome Shell?


How do I switch from my current environment to Gnome Shell and back again?


cheers

---

### Post by Naitsirhc Hsem on 2010-05-04
in a terminal <CODE>gnome-shell</CODE>

---

### Post by tomreid on 2010-05-04
Hi

Wasn't sure if you meant for me to add the text "Code" or not, so I tried it both ways, but neither worked. Here's the output from the terminal:

tom@tom-laptop:~$ <CODE>gnome-shell</CODE>
bash: syntax error near unexpected token `newline'

tom@tom-laptop:~$ gnome-shell
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.


cheers

---

### Post by Naitsirhc Hsem on 2010-05-04
the <Code> should have ```
looked like this
```

try ```
gnome-shell --replace
```

---

### Post by tomreid on 2010-05-04
thanks that worked. I'm assuming it'll default back to regular Gnome on a re-boot?

cheers

---

### Post by Naitsirhc Hsem on 2010-05-04
Yes, if you like it, you can set it as a start up application in System > Preferences > Startup Applications. 

 Click Add

Name : Gnome Shell

Command : gnome-shell --replace

Comment : Auto Start Gnome Shell

---

### Post by tomreid on 2010-05-04
Thanks, I'm kinda enjoying it so far. I never liked that clutter down the bottom of the screen that all those open or minimised applications caused. I like having the additional free space now. 

It's a bit like using a Mac with the Dock minimised.

cheers

---

