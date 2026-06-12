---
title: "bash buzzer sound"
date: 2008-01-24
forum: Desktop Environments
---

### Post by newsman on 2008-01-24
How do I disable error buzzer sound in bash... (sounds if you press backspace too often [already bigenning of line] , or down arrow key to often [already end of history] etc)

Its bit annoying cos i have the habit of pressing backspace too much or down key too much.

---

### Post by erginemr on 2008-01-24
If it is the Gnome Terminal, not the real text-mode, from where you have been working, then it is easy to disable that sound. 

Open Gnome Terminal, use its Edit menu to reach the Profiles section, and uncheck the tick beside "Terminal Bell".

---

### Post by erginemr on 2008-01-24
And to disable the Bash sound feedback from the real terminals (Alt+F1-F6), edit /etc/inputrc with:
```
gksu gedit /etc/inputrc
```
or
```
sudo vim /etc/inputrc
```
Find the line:
```
# set bell-style none
```
and remove the comment (#) before it. 

Logout and back in and you should be all set.

EDIT: Alternatively, you can add:
```
setterm -blength 0
```
to either: /etc/profile (global) or ~/.bashrc (user level)
to get to the same effect.

---

### Post by newsman on 2008-01-24
great thanks.:KS

hopefully nobody has yet to write a book on ubuntu annoyances, but if they were to write a short article.. this should be there. hahah.

---

### Post by erginemr on 2008-01-24
:lolflag:
Have fun in silence!!

---

### Post by newsman on 2008-01-25
yeah, now i got to disable the sound in firefox (it comes up in edit > find in this page > phrase not found). After that, in office, and then close the windows, put flat sheets of towel on the window sill when it rains, and oil the door, and then I am done.

---

### Post by erginemr on 2008-01-25
I am currently running Windows, but it should be under Gnome Main Menu -> Preferences -> Sound 
"Disable System Beep" or something.

Hush...;-)

---

### Post by newsman on 2008-01-25
what ya know, 

system > prefernces > sound 

tab called "system beep"


thanks.

---

