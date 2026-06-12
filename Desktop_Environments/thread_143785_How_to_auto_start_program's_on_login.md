---
title: "How to auto start program's on login?"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Peturrr on 2006-03-13
I have been looking at the forum but I can't find it.

I want several apps to automagically startup when I log in. In windows you can make a link to the startup folder. How should I do this in Gnome?

---

### Post by Dullin on 2006-03-13
You can go the System -> Sessions and then there should be a Startup Programs Tab. Click add and there you go.

---

### Post by ardchoille on 2006-03-17
how would one do this if they run WindowMaker, or openbox or any other environment that doesn't include gnome?

---

### Post by Ramses de Norre on 2006-03-17
Adding an init script for it is the best way to do it then I guess.

---

### Post by ardchoille on 2006-03-17
[QUOTE=Ramses de Norre]Adding an init script for it is the best way to do it then I guess.[/QUOTE]
what would be the script filename and path? What is the syntax for the content?

---

### Post by Kagey on 2006-03-17
put a file called .xinitrc in your home directory, its contents are just commands, eg:

gkrellm2 -w &

---

### Post by taurus on 2006-03-17
Or just add the scripts to ~/Desktop/Autostart!!!

---

### Post by 5-HT on 2006-03-17
[quote=taurus]Or just add the scripts to ~/Desktop/Autostart!!![/quote] 
Wondering if most WMs look for this directory?
For DEs, I know XFCE and KDE do...guess GNOME's the odd one out?

---

### Post by Swab on 2006-03-18
[QUOTE=Kagey]put a file called .xinitrc in your home directory, its contents are just commands, eg:

gkrellm2 -w &[/QUOTE]


How about if I wanted to execute commands when a new user first logs in?  For instance, adding the user to a group.

---

### Post by syklitengutt on 2006-03-18
how to do it in xfce?

---

### Post by 5-HT on 2006-03-19
[quote=syklitengutt]how to do it in xfce?[/quote] 
Just put a script containing the executables you'd like run on XFCE boot into ~/Desktop/Autostart.

Make sure to make the script executable, and it's best to run each of the executables in the background (append '&' after each in the script).

HTH

---

