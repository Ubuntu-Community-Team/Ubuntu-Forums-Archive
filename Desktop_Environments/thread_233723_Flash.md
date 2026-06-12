---
title: "Flash"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Slippers on 2006-08-10
What is the code to take me to the directory and then to install flash and where do i insert this code???

---

### Post by Ramses de Norre on 2006-08-10
Uhm this should install flash for you:
```
sudo gedit /etc/apt/sources.list
```
and remove the # from the lines starting with "deb" and ending with "universe" also add "multiverse" to the end of these lines when not it's allready there.
Save the file, do ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
``` and follow the questions on the screen.

You need to type all this lines in the terminal, Applications > system tools > terminal or something like that.

---

