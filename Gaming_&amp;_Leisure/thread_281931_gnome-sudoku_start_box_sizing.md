---
title: "gnome-sudoku start box sizing"
date: 2006-10-21
forum: Gaming &amp; Leisure
---

### Post by nashjc on 2006-10-21
Starting gnome-sudoku 0.4.0 on Ubuntu Dapper (Gnome interface) gives a display that has the Sudoku grid in a frame that is slightly too small and has a slider at the right. This goes away if exterior window is resized even a tiny amount. I have seen similar errors in other window sizing setups, but a look at the /usr/share/gnome-sudoku files (.svg and .glade) suggested some changes which I tried with no effect. There also seem to be some gnome config files under my home dir. However, I'm reluctant to make too many changes, as I'm not a gtk programmer.

Suggestions please.

J C Nash

---

### Post by Perfect Storm on 2006-10-22
You could try running the game from the terminal and add --help afterwards to see which flag are availble, perhaps there is a --res X flag.

Try check the config files for something that looks like resolution or screen command.

---

### Post by nashjc on 2006-10-22
From terminal ran 
gnome-sudoku -v

This showed the process of setup, but gave same display.I done't see anything to do with resolution or window size. I've saved the output, i.e., 
gnome-sudoku -v >file.txt

I've looked through the glade files in /usr/share/gnome-sudoku, in 
$HOME/.gconf and $HOME/.gnome2 bits for gnome-sudoku and even tried to find general window setup paramters (which I still haven't found, however).

I have found "Decrease size" button in sudoku clears the problem.

Pointers?

JN

---

