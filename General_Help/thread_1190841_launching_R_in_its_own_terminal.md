---
title: "launching R in its own terminal"
date: 2009-06-18
forum: General Help
---

### Post by Prium on 2009-06-18
I prefer the command-line version of R but I would like it to have its own terminal just like it does in Windows, because I don't like using ctrl-z to put it on hold every time I need to use the terminal for something else. I would also like to launch R directly from the menu, if possible. Using 'R' or the full path '/usr/lib/R/bin/R' as a command does nothing. Is guess because I am not telling it to load the terminal first, right? How can I do this?

---

### Post by sdennie on 2009-06-18
In the properties dialog of the launcher, there should be a combobox at the top that says, "Application".  Changing that value to "Application in Terminal" should do what you want.

---

### Post by drs305 on 2009-06-18
sdennie has told you how to make it run from a shortcut.

The pure command line way to do what you want to open a new terminal and run an app within the new terminal window would be to run:
```

gnome-terminal -x <appname>

```
Example:
gnome-terminal -x top

The "-x" switch tells the command to run whatever follows in a new terminal.

---

### Post by Prium on 2009-06-18
Perfect! 
Thank you drs305 & sdennie

---

