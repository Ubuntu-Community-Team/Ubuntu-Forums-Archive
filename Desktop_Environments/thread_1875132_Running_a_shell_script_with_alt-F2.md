---
title: "Running a shell script with alt-F2"
date: 2011-11-04
forum: Desktop Environments
---

### Post by agnul on 2011-11-04
In gnome2 "Alt F2" used to bring up the "run command" dialog and I could run things just typing a command line. This worked also for shell scripts, i.e. I was able to enter "/some/path/script.sh". If I try this in unity nothing happens, even if the script appears in the suggestions/search results. How could I fix that? (or even better how can I create a "launcher" and dock it in the dash?

---

### Post by W.McL on 2011-11-04
The alt+F2 run dialog of Unity doesn't look in the shell path for executable files like Gnome's alt+F2 dialog, but scans /usr/share/applications and ~/.local/share/applications for *.desktop launcher config files. You could write a .desktop file for your script and place it there, not sure if there is any other way to make this work.

---

### Post by Simian Man on 2011-11-04
Krunner, which serves this purpose in KDE, looks for the .desktop files so it can provide icons and descriptions, but also will scan your PATH for other programs.  Krunner blows away other Alt-F2 programs.

---

### Post by stinkeye on 2011-11-04
You might like to have a look at kupfer.
It will load any of your installed programs.
You can choose folders to catalogue so you can bring up your scripts 
by entering the name.
You can add items to favourites so it's added to the top of the list
when you start typing.
If you press the "." key you can type in the full path and choose 
to open or run using the tab key.

Also has a lot of plugins.
One tip, if you open kupfer and start typing you can't delay too
long between keystrokes because it will revert to a new search.
When entering a full path use the "." key first.

---

### Post by agnul on 2011-11-07
> **W.McL said:**
> The alt+F2 run dialog of Unity doesn't look in the shell path for executable files like Gnome's alt+F2 dialog, but scans /usr/share/applications and ~/.local/share/applications for *.desktop launcher config files. You could write a .desktop file for your script and place it there, not sure if there is any other way to make this work.

I'm entering the full path to the script, and an icon for the script shows up in the suggestions for the script, so I assume it will let me run it. Obviously I'm wrong :-) but it used to work just fine with the old gnome. Also I'm not really sure about .desktop files, since it seems I can pass arguments to the command I'm entering (e.g. I can alt-f2 gnome-terminal --geometry=... -e ...)

Oh well, I'll read up on .desktop files.

---

