---
title: "update gnome terminal title dynamically from commandline"
date: 2009-04-23
forum: Desktop Environments
---

### Post by alperyilmaz on 2009-04-23
I am running shell-fm in gnome-terminal under profile named "shell-fm". How can I manipulate the terminal window title for that profile from commandline?

gnome-terminal command has --title option but that's for when opening a new terminal. My question is, how can I manipulate existing gnome-terminal's title. PROMPT_COMMAND environment might be used but I'm not sure if it will effect other terminals as well. Also, if that variable is used, I don't know how often it is refreshed.

thanks.

---

### Post by alperyilmaz on 2009-04-23
I found the solution after long search. There's a program named xtermset which allows manipulating xterm settings. The title setting is changed as follows: 

xterm -T 'string'

---

