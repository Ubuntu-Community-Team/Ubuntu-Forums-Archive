---
title: "problems with synaptic package manager...."
date: 2006-06-26
forum: Desktop Environments
---

### Post by cwncool on 2006-06-26
also, i need a media player to play wmv's....MPlayer is way to hard on this computer because I'm to updated in my compiler, etc... What other player can play wmv's? are there windows ones any that I can run in the Wine enviroment? Thanx!

---

### Post by jaypeasy on 2006-06-26
Try browsing the applications menu and submenus. Else you can run it by typing the application name in a terminal.

---

### Post by cwncool on 2006-06-26
also, i need a media player to play wmv's....MPlayer is way to hard on this computer because I'm to updated in my compiler, etc... What other player can play wmv's? are there windows ones any that I can run in the Wine enviroment? Thanx!

---

### Post by cyracks on 2006-06-26
Right click on package (in SPM) and select installed files. Look for files inside bin directory and then execute them in the shell

---

### Post by BoneKracker on 2006-06-26
Supported applications intended for use in the graphical environment generally create menu entries.

If the good suggestions above don't work, you can try searching for the executable program.  Sometimes they are installed in a location that is outside your normal path, in which case you have to type the whole path and name to get them to run from the terminal/shell.

You can update the index of your files like this:
```
sudo slocate -u
```

Then you can search for the program like this:
```
sudo slocate app_name
```
(substitute your best guess as the the "app_name")

For more detail, you can read the slocate manual:
```
man slocate
```

---

