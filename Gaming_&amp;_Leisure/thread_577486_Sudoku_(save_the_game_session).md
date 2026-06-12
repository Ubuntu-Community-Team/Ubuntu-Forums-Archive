---
title: "Sudoku (save the game session)"
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by Depressed Man on 2007-10-16
I've been playing Sudoku in Gutsy. However, I've noticed that whenever I close it and open it up the game is reseted. So is there any Sudoku game that saves my game session till I'm done with it?

---

### Post by kerohazel on 2007-10-19
I checked the original source from the gnome-sudoku site () and found a couple lines that have been removed from gnome_sudoku.py:

            else: #always save the game
                self.gconf['current_game']=self.sudoku_tracker.save_game(self)

These would be on line 534, after these:
        if not self.won:
            if not self.gsd.grid:
                self.gconf['current_game']=''

I was able to have gnome-sudoku print a string of numbers which represent the state of the game, and save it to gconf, but the problem is that save_game only returns the *original* state of the grid.

sudoku_maker.py has the source for save_game, and it calls game_from_ui. I poked around and found that ui.gsd.grid.to_string() gives two lines of numbers, the first is the "virgin" grid, the second is the grid's current state. So I tried changing the body of game_from_ui to this:

return ui.gsd.grid.to_string().split('\n')[1]

That's about as far as I got. It saved the game into gconf. But now I'm not even sure that this was supposed to be saved in this fashion. I'm just mimicking what I found that the old Feisty gnome-sudoku saved in that key.

God I hate gconf.

---

### Post by glennric on 2007-10-19
I just discovered this.  That sucks that they remove this feature as well as the feature to resume an old game.  Now if you don't finish a game you have to start all over.  Why did they remove such a good thing?  It is annoying that there is a regression in features.

---

### Post by kerohazel on 2007-10-20
[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/154761)

I'd like to work on this some more, especially since I already spent a good deal of time reading the source. But if I don't get a chance, maybe someone else will.

---

