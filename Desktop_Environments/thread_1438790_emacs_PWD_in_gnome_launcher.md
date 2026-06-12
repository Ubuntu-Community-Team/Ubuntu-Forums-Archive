---
title: "emacs PWD in gnome launcher"
date: 2010-03-25
forum: Desktop Environments
---

### Post by Cooner on 2010-03-25
First, my apologies as I'm not sure if this is an emacs question, a gnome question, an ubuntu question, or just a linux question :D

I wanted to set a custom keyboard shortcut to launch an emacs editor (I've set a few of these using the "Super" key prefix... Super-F = firefox, Super-T = terminal, Super-E = emacs, etc.  It's quite handy.)

It works great through the keyboard shortcuts, but I have a bit of an issue once emacs has started (one that is easily replicated with just a command line).  Emacs has some knowledge of the current working directory when you start... to see this, if you open emacs in a terminal, hit C-x C-f to open a file, it starts searching for that file from the current working directory.  When I use my launcher, PWD is set to /, which kind of sucks.  Now, once I'm in emacs, it's easy to do a "M-x cd ~", which changes the PWD to my home, but I'd love to be able to set that somehow in the command line for the launcher.

Is it possible to fake the env in a one-liner for a launcher to make emacs think it's starting from ~?

Thanks, and my apologies if I've guessed incorrectly as to where this should go.

---

### Post by Alan James on 2010-03-25
I think you can do this by writing a shell script that will “cd ~” and then launch emacs. After creating it you should “chmod 777” so it can be executed. If you can make your keyboard shortcut run that shell script it will change the working directory, then launch the program, which should solve your problem. I use KDE and thus don't know if this will work on gnome.



Attached is the shell script to do it. This is one of many options.

---

### Post by krismatth3 on 2010-03-26
What about the command "CWD=~ emacs"?

---

### Post by Cooner on 2010-03-30
my initial guess was the "CWD=~ emacs", but that doesn't work... it gives a generic error message of: "Error using the command 'CWD=~ emacs' which is bound to Mod4-e" (or something like that).

However, the script does work, so I'll run with that.

Thanks!

---

