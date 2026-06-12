---
title: "Aaargh! Applications shutting down when I type?!"
date: 2005-12-18
forum: Desktop Environments
---

### Post by lupine_nickt on 2005-12-18
Really weird, this one, lol. Whenever I press any character key in certain applications (the two which come to mind right now are gksudo & gedit), the application just... shuts down. Any body any ideas why it might do this? Or how to fix it? :)

I think I might have caused it by trying to set up a shortcut (for 3ddesktop) - I opened the Configuration Editor, went to apps->metacity, and changed the global_keybindings/run_command_1 & keybinding_commands/command_1 keys as specified. Restarted my PC, and it's now doing this to me (sulk).

Obviously, I've looked back into gconf-editor to change the values back, but no joy! global_keybindings is "disabled", whereas keybinding_commands is just blank.

Bah, lol.

xF,

...Nick

---

### Post by adwait on 2005-12-18
This sometimes happens with a segmentation fault. Try running these applications from the terminal and observe the error messages. Chances are the last message before exiting reads "Segmentation Fault". Now these errors go away after I restart KDE on my PC.......if not, maybe you are short on memory or something.

---

### Post by lupine_nickt on 2005-12-19
Thanks for the reply. Finally got a terminal running (had to copy & paste the password, lol). Strangely, I don't have the problem when I run the program from terminal. Weird. 

I might try changing metacity for something else. Might solve the problem...

xF,

...Nick

---

