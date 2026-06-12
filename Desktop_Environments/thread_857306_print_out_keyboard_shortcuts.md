---
title: "print out keyboard shortcuts?"
date: 2008-07-12
forum: Desktop Environments
---

### Post by mrodent on 2008-07-12
hi all, 

you know how you can customise the settings of the keyboard shortcuts...?  How can you then print these settings to a piece of paper?  Presumably they must be contained in a file somewhere!

also be interested in knowing more about the best way to increase keyboard use and decrease mouse use, in addition to 1) command line 2) currently available commands to which you can assign keyboard shortcuts - (in WXP I use autohotkey quite a bit, and am missing it in Linux)

---

### Post by pauper on 2008-07-18
System--Preferences--Keyboard Shortcuts

```
gconf-editor
```

Then go to apps--metacity: global_keybindings and keybinding_commands
Well, files are here:

~/.gconf/apps/metacity/global_keybindings/%gconf.xml
~/.gconf/apps/metacity/keybinding_commands/%gconf.xml

You can use xbindkeys as well:

```
sudo apt-get install xbindkeys

man xbindkeys

xbindkeys-config
```

If you want to stick with keyboard and CLI, then welcome to TTY (press
Ctrl-Alt-F2, for example). To switch back to X session press Ctrl-Alt-F7.

---

### Post by mrodent on 2008-10-05
Thanks for the reply...

You obviously know quite a bit about Linux... but your answer is a bit cursory...

Sys --> Pref --> Keyboard Shortcuts: yes, I know how to set them up...

gconf -editor: presumably this is how to set them up by the CLI... but I didn't ask about that

- two directories: thanks for pointing these out... these currently list 4 changes which I have made to the set of default hotkeys... but my question was "how do I print out all the hotkeys, including the defaults which I have left as is"

- "You can use xbindkeys as well:" ... to do what?  To set up bindings?  But that wasn't the question.

- "if you want to stick with the CLI"... I specifically mentioned the command line in my question, and anyone reading my question can really see that this is not what I'm asking

The reason I find this answer a bit annoying is because a beginner wants more experienced users to help them out with simple requests, not needlessly to complicate things with irrelevant details or stuff the newbie already obviously knows.

I am still hoping to find a way of printing out these shortcuts (all of them).  When learning shortcuts it is very helpful to have a PAPER list of them... the fact that it is quite difficult to get an answer to this is one reason for saying that much of Linux is still needlessly un-user-friendly.

Mike

---

