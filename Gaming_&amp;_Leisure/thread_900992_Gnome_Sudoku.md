---
title: "Gnome Sudoku"
date: 2008-08-25
forum: Gaming &amp; Leisure
---

### Post by mosestruong on 2008-08-25
About last week, Gnome Sudoku started crashing whenever I try to start it. The only thing I've changed was installed two other games - widelands and warezone2100, so I'm not sure if that might have caused Sudoku to crash. 

Anyone out there know what might have gone wrong?

---

### Post by Perfect Storm on 2008-08-26
Please, start the game via the terminal and post the output.

---

### Post by mosestruong on 2008-08-27
The terminal output is as follows:

```
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 55, in <module>
    start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 1039, in start_game
    u = UI()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 200, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 64, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 214, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 191, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 76, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 151, in make_saved_game_model
    sudoku.sudoku_grid_from_string(g['game'].split('\n')[1].replace(' ','')).grid,
  File "/var/lib/python-support/python2.5/gnome_sudoku/sudoku.py", line 232, in sudoku_grid_from_string
    assert(len(s)<=GROUP_SIZE**2)
AssertionError

```

---

### Post by kagashe on 2008-08-28
I have used sudoku (installed through gnome-games) for many days but now it fails with the same errors as posted above.

I have also tried deleting files the folder .gnome2/gnome-sudoku/puzzles in my home directory and reinstall after complete removal. But it does not work.

kagashe

---

### Post by jecker on 2008-09-21
Have you found a solution to this problem?

---

### Post by mosestruong on 2008-10-01
A workaround is to remove the ~/.sudoku directory and it should start normally... (but you will loose any saved games... so you might want to back it up just in case they found a solution to this problem if you really want to keep your saved games)

---

### Post by lesterbolen on 2008-10-02
I have the same problem:

```
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 55, in <module>
    start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 1039, in start_game
    u = UI()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 200, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 64, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 214, in select_game
    choice = game_selector.NewOrSavedGameSelector().run_swallowed_dialog(self.swallower)
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 191, in run_swallowed_dialog
    self.setup_dialog()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 76, in setup_dialog
    self.make_saved_game_model()
  File "/var/lib/python-support/python2.5/gnome_sudoku/game_selector.py", line 151, in make_saved_game_model
    sudoku.sudoku_grid_from_string(g['game'].split('\n')[1].replace(' ','')).grid,
  File "/var/lib/python-support/python2.5/gnome_sudoku/sudoku.py", line 232, in sudoku_grid_from_string
    assert(len(s)<=GROUP_SIZE**2)
AssertionError
```

> A workaround is to remove the ~/.sudoku directory and it should start normally... (but you will loose any saved games... so you might want to back it up just in case they found a solution to this problem if you really want to keep your saved games)

I don't understand what you're saying...could you be more specific.  I've only been using Ubuntu for a couple of days and don't understand the syntax (~/.sudoku directory?)

Thanks.

---

### Post by mosestruong on 2008-10-03
open gnome-terminal (Applications > Accessories > Terminal)
Type ```
rm -r ~/.sudoku
``` and press [ enter ]

Then you should be able to restart gnome-sudoku.

The '~' is a shorthand for your home directory.

---

### Post by Sef on 2008-10-03
> open gnome-terminal (Applications > Accessories > Terminal)
Type  	Code:
 	rm -r ~/.sudoku 
 and press [ enter ]

Then you should be able to restart gnome-sudoku.

The '~' is a shorthand for your home directory.
 		                   		  		  		  		  		  	   	 		
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=5898016")

Easier than typing is copy and paste that command.

---

### Post by lesterbolen on 2008-10-03
It worked!

I read up on the 'rm' and '-r' terms and decided to use the following:

```
rm -ir ~/.sudoku
```

Thanks for the clarification!

---

