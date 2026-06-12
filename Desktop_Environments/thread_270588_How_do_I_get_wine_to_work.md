---
title: "How do I get wine to work?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Trifid on 2006-10-03
I have installed the latest version, and checked with terminal with winecfg but there is no option under applications for it? I am a little confused as to why this has happened. 

What I want to do is change the permissions of a program that has to be done through this program. 

Thanks for the help.


(Sorry it is a little vague.)

---

### Post by meatface on 2006-10-03
I just installed wine last night and have never used it before. What I found was that I go into the terminal and cd to the directory with the program that I want to run then, I would type 'wine' a space and then the program name. Lets say it is called 'trial.exe', and it is on the desktop, here is what I would do:

cd Desktop
wine trial.exe

You will find the programs installed under /home/you_username_here/.wine/drive_c

Just remember that the '.wine' is a hidden directory and you will have to hit ctrl-h when in your home directory to make it visible.

I hope this helps

Cheers

Meatface

---

