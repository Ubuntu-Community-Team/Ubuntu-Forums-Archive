---
title: "Two X sessions at once"
date: 2006-07-11
forum: Desktop Environments
---

### Post by christooss on 2006-07-11
How can I make my computer to run with two xsessions. On would be on "F7" and other on "F8"

Thanks for the anwsers. If I didn't make my self clear enough please ask for other information about question

---

### Post by mattkenn4545 on 2006-07-11
You sure can.

What I do is add 

[Servers]
1=Standard 
in my /etc/gdm/gdm.conf-custom file

(note doing this at work and things are probly not right.)

---

### Post by Dr. Nick on 2006-07-11
Try Applications, System Tools. New Login.

If you dont see it the go to applications - accessories -alacarte menu editor and hit the checkbox for "new login" under system tools, I know their is a command line way to do this aswell, just dont recall at the moment.

---

### Post by christooss on 2006-07-11
Thanks

New Login works. But I have to try with start up. If two sessions are started.

Now there is new question. How to start single (no gnome just X and One aplication) application in one session and Gnome in other

---

### Post by aysiu on 2006-07-11
I installed the *xnest* package and then ran the command ```
gdmflexiserver --xnest
``` to get another X session running. More details [here](http://www.ubuntuforums.org/showpost.php?p=1206700&postcount=3).

---

