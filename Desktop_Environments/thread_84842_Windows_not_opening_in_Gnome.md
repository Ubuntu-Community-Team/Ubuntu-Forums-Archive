---
title: "Windows not opening in Gnome"
date: 2005-11-01
forum: Desktop Environments
---

### Post by psyguy92 on 2005-11-01
Hellos

I have a problem that's becoming somewhat frequent.  Often when I'm using Gnome and I try to start a new program, the mouse pointer will change indicating it is loading, but the window will never show up.  After I get this error, no program window will open.  I can't even open a terminal window! 

To try to fix this I did Ctrl-Alt-Backspace and after logging in, I get this:
Greeter failed - trying another
Greeter failed - trying another
Greeter failed - trying another (etc.)
Then it says it's failed 6 times in the last 90 seconds, and will wait 2 minutes to try again.

This kept me from being able to read man pages and the like to see about fixing it.  Finally I did this:

```
ps -C gdm
kill *process ID of gdm*
sudo gdm restart
```

This seems to fix the probem, but it's very annoying.

Q1:  What might be causing this?
Q2:  Am I 'fixing' it the best way?  What am I actually stopping by doing this? Gnome? X? 

Thanks for reading

psyguy92

---

### Post by rlange on 2005-11-01
I don't know what is causing this but I am having the exact same problem.

---

### Post by psyguy92 on 2005-11-03
Does anyone know anything about this?  Everyone seems so helpful here on the forums.  I'm sure someone must have at least an idea of what might be going on?

It just happened again.  I'm reading several web pages in tabs (8 or so) and tried to run a terminal to check the version number on an installed program, and the terminal failed to open.  I sighed, and went on to something else.  A few minutes later, I tried to run synaptic to install something I found referenced in the forums, and sighed again.  I hadn't yet killed gnome/X nor rebooted and had forgotten that my windows were not opening.

Now I must either close/save everything and kill gnome/X, or not be able to open anything and I'm stuck with only the programs I already have opened.

:confused: 

Please help! 

:???:  psyguy92

---

### Post by jvictor on 2005-11-03
if nothing works just try to remove you gnome's config files from your home directory 

This may create new fiels and solve the issues u r facing

---

