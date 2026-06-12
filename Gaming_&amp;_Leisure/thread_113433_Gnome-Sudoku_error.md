---
title: "Gnome-Sudoku error"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by blueturtl on 2006-01-06
Hi,

downloaded and installed a deb for Gnome-Sudoku.
Now that I try to run it I get this type of error through the terminal:

Traceback (most recent call last):
  File "/usr/bin/gnome-sudoku", line 11, in ?
    start_game()
  File "/usr/share/gnome-sudoku/gnome_sudoku/gnome_sudoku.py", line 876,
in start_game
    u = UI()
  File "/usr/share/gnome-sudoku/gnome_sudoku/gnome_sudoku.py", line 134,
in __init__
    self.main_actions.add_actions([
AttributeError: 'module' object has no attribute 'STOCK_FULLSCREEN'

Does anyone have a clue on how to fix this? I hear Gnome-Sudoku is a part of Breezy, but I can't install Breezy because of several problems it causes...

---

