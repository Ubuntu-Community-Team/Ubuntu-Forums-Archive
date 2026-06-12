---
title: "Shell Script Execution"
date: 2005-03-12
forum: Desktop Environments
---

### Post by dave9191 on 2005-03-12
Ive written a shell script that i would like i would like to execute from an icon on my panel. I have tired to put the command to execute as " xterm -e myscript.sh & ".  When typed into any kind of terminal it launches the xterm and the scritp runs (first thing it does is ask for a password). But when I click the icon or type that command into the gnome run window it just flahes the xterm at me and then vanishes. 

Has anyone got any ideas on how to run the script from an icon?

---

### Post by lorap on 2005-03-12
hi buddy!
try this:
sudo sh /home/youruserfolder/yourscriptname
have a nice day!
pavel

p.s.:
let me know if it worked.

---

### Post by dave9191 on 2005-03-12
Im affraid that it didnt work. Again works fine from a terminal, but not from the run command window or as the icon command. From the icon it does nothing at all :(

---

### Post by bored2k on 2005-03-12
[QUOTE=dave9191]Im affraid that it didnt work. Again works fine from a terminal, but not from the run command window or as the icon command. From the icon it does nothing at all :([/QUOTE]
 Remember to make the script executable [755, 777, whatever].

---

### Post by WW on 2005-03-12
To add an icon to the top panel: right-click in the panel, select "Add to panel", select "Custom Application Launcher" and click on "Add"

In the Create Launcher window, enter a Name (this will appear as a "tool tip" when you hold the mouse cursor over the icon) and a Command.  To run a script like you mentioned, try putting this in the Command:

```
xterm -hold -e full-path-to-script-directory/myscript.sh
```

Replace "full-path-to-script-directory" with the appropriate path. For example, I tested this out with a script in my bin directory, so I would use "xterm -hold -e ~/bin/myscript.sh".  Without the "-hold" option, the xterm will close as soon as the script is finished.

If you don't select an icon, you will get a generic "gnome foot"--at least that's what I got.

Be sure you have made the script executable by running

```
chmod u+x myscript.sh
```

in the directory where the script is located.

Note: The above is based on using warty and gnome 2.8.  I don't know how much will be different in hoary with gnome 2.10.

---

### Post by dave9191 on 2005-03-12
Ok, thanks a lot guys, i just needed to spesify the full path of the script. I assumed that it would work since i have its location in the bash path. The -hold keeps the window open even after the script finishes which can be kinda annoying. Its all working as it should be now :D

---

