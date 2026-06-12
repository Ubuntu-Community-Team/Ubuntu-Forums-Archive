---
title: "Gnome-panel does not run at boot"
date: 2009-04-26
forum: General Help
---

### Post by ralewis on 2009-04-26
I just upgraded to Jaunty today, and noticed when I boot into the system that gnome-panel no longer runs.  When I run gnome-panel& in a terminal, it loads and runs fine, giving the following output at the terminal:

$ gnome-panel&
$ ** (gnome-panel:3938 ): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3938 ): DEBUG: Adding applet 0.
** (gnome-panel:3938 ): DEBUG: Adding applet 1.
** (gnome-panel:3938 ): DEBUG: Adding applet 2.
** (gnome-panel:3938 ): DEBUG: Adding applet 3.
** (gnome-panel:3938 ): DEBUG: Adding applet 4.

Any ideas what might be wrong?

---

### Post by fooman on 2009-04-26
don't know if it makes any difference,  but i believe the command should have a space between panel and &

like this:

```
gnome-panel &
```

any help? :confused:

---

### Post by ralewis on 2009-04-26
Sadly, nope.

So, I went and added gnome-panel to System>Preferences>Sessions, and now I can get it to display at boot-up.  I'm not sure if that's a crude fix that I'm applying though, of if it's a good solution.

---

### Post by fooman on 2009-04-26
hmm,  you updated to jaunty and still have sessions listed in system > preferences ?

on my install,  "sessions" was replaced by "startup applications".

anyways,  try this:  in sessions...*uncheck* what you added,  then close the sessions box.

next open a terminal and run:

```
gnome-panel &
```

next,  *close any running applications*....then open the sessions preference box again and go to the options tab.  click on "remember currently running applications" if the line is there,  if it is not,  then put a check next to "automatically remember running applications".  close the sessions box again.

then restart the computer.

see if the panel opens up normally.  

whether it worked or not,  go back to sessions and under options...  *uncheck* the box you checked previously.  if it did not work,  go back to what you added before to get it to load at startup.

hope that helps.

---

