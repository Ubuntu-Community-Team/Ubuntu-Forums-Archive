---
title: "Can I assign a program to a mouse button?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by anil_robo on 2006-07-09
I have a five button logitech mouse. Four are already configured (left click, right click, two browser buttons) but I was thinking if there was a way to assign a program to run when I click the fifth mouse button?

---

### Post by strabes on 2006-07-09
yes. First you have to know the command to run the program. (usually just the name for the program). Then Hit Alt+F2, type gconf-editor. Then go to apps, metacity, global_keybindings. Under the 'name' column, you should see things like cycle_panels, run_command xx, etc. Select one of the run_commands, and click your mouse button. That will put nomething in the 'value' column for the command you selected. Once that's done, go to keybinding_commands, and select the command # which you used in the previous step. Then in its 'value' box type the command to open the program.

Now when you click the mouse button it should open the program. If not then I don't know what to tell you

---

### Post by anil_robo on 2006-07-09
No it didn't work.

I open the configuration editor and "click" on the commands. the "disabled" field becomes highlighted for editing. What to do?


[ATTACH]12466[/ATTACH]

---

