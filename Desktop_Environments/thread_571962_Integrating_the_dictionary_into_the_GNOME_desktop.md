---
title: "Integrating the dictionary into the GNOME desktop"
date: 2007-10-09
forum: Desktop Environments
---

### Post by tyrion2323 on 2007-10-09
Well, I've searched and haven't found anything, so here goes.

Firstly, I'm quite exciting to truly be joining the Linux/Ubuntu fold.  I'm pumped to be part of a real community, and I want to try to do my best to give back in order to feel like I've "carried my own weight."

This might be a problem, as I don't have an ounce of Shell-Script-Coding experience.  But I am buying a book, so that will soon be a thing of the past.

Here's my idea.  One of my favorite things in the Mac OS is that I can [Cmd-Ctrl-D] over any word and the definition pops up in a small window!  Quite cool.  So I want to try to write a script that will do that, BUT my kicker is that it will also allow for other dictionaries to work as well!

It's not nearly as fancy as some of your other ideas, but I'm pumped.  Whaddya think?

---

### Post by Namtabmai on 2007-10-10
Easy enough, if you want a easy way of getting this functionality add the deskbar applet to your panel, and you can configure the keybinding to show this and also select that it automatically searches for selected text+enable the dictionary plugin.

If you want something that more closely resembles Mac way, then
```

sudo apt-get install xsel

```
Open up Applications->System->Configuration Editor
Got to /apps/metacity/global_keybindings
Now find a entry such like "run_commandX" where X is a number and the command is currently shown as disabled. Double click on the disabled part and enter a string such as 
```

<Super><Alt>D

```
Now go to /apps/metacity/keybinding_commands and find the command_X that corresponds to the X you found before. So if you used run_command3 then you'll need to edit command_3, double click on the space to the right and enter.
```

gnome-dictionary `xsel`

```

Voila! Highlight a word and hit Windows+Alt+D and you'll get the dictionary entry for the highlighted command.

Oh if you're running compiz, you'll need to use compiz configuration manager rather than Configuration Editor, but the method is similar.

---

### Post by tyrion2323 on 2007-10-10
Well, hrm.  I didn't know it was doable...there goes my grand contribution :(

On the other hand, it's awesome that it already exists!

---

### Post by Namtabmai on 2007-10-10
Well it's doable certainly, but not exactly the easy or quick for a new comer to set up. It would be nice if Gnome Dictionary had a option to set up all of this for you in it's preference.

---

