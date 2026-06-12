---
title: "Terminal in current directory"
date: 2008-03-24
forum: Desktop Environments
---

### Post by terrordrone on 2008-03-24
Hi

i have a nautilus script to open the terminal in current directory

but i would prefer the same happening through the keyboard

i switched from kubuntu.. where presessing f4 when dolphin/konqueror (file browser) is in focus, the terminal would open up in the current directory?

how do i bind that to f4?

thanks in advance

---

### Post by heikaman on 2008-03-25
1-open a terminal and type gconf-editor

2-select aps->metacity->global_keybindings
   set the value for key "run_command_1"  to "F4" (or any other empty run_command_# key)

3-select aps->metacity->keybinding_commands 
   set the value for command_# where # is the number you selected from step 2,  to "your script".

you're done  :)

---

### Post by terrordrone on 2008-03-25
thanks for the reply

I tried what u said .. the terminal was opening only in ~

then u double checked my nautilus script.. and found out that even that wasnt working

plz do gimme a link where i can get a working script..

---

### Post by heikaman on 2008-03-26
sudo apt-get install nautilus-open-terminal
this will install a Gnome extension that will allow open terminals in the current directory from a mouse right click, you will have to restart I think...
this is the best I could do, good luck.

---

### Post by crocowhile on 2008-03-26
Go Preference-Appearance-Interface
Check the "Editable menu shortkeys" true.

Now in nautilus go File-Open in Teminal 
While hovering with the mouse over Open in Teminal,  press the shortcut you want to use.

---

### Post by terrordrone on 2008-03-26
> 
1-open a terminal and type gconf-editor

2-select aps->metacity->global_keybindings
set the value for key "run_command_1" to "F4" (or any other empty run_command_# key)

3-select aps->metacity->keybinding_commands
set the value for command_# where # is the number you selected from step 2, to "your script".

    
     cant i make it run nautilus-open-terminal, as the script i downloaded (as part of NScripts) works in a few folders and not in others. nautilus-open-terminal works for everything. So, it would help if i can map f4 to to do that

---

### Post by terrordrone on 2008-06-01
> **crocowhile said:**
> Go Preference-Appearance-Interface
Check the "Editable menu shortkeys" true.

Now in nautilus go File-Open in Teminal 
While hovering with the mouse over Open in Teminal,  press the shortcut you want to use.
i didnt get the second part..

i checked editable menu shortkeys

didnt get what to do after that

---

### Post by terrordrone on 2008-06-03
bump...

---

