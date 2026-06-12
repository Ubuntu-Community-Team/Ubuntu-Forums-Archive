---
title: "[SOLVED] Sudoku Won't Load"
date: 2008-12-26
forum: General Help
---

### Post by stndrdsnz on 2008-12-26
I tried posting this earlier, but it doesn't seem to have worked...probably something I did, but I'm going to try it again.

I'm not a complete linux newbie, but still getting my feet wet. This isn't any critical issue, but my wife and I enjoy playing Sudoku as a passtime, but recently I haven't been able to get Sudoku to load. It didn't seem to stop working with any change I made, but seemingly randomly. Although, I've been around computers enough to know that when something stops working it's usually your own fault. 

Anyhow...here's what is going on. If I go to Applications -> Games -> Sudoku, the button appears at the bottom that says "Starting Sudoku", it then switches to say "Sudoku" and then disappears. This all happens within a matter of seconds.

Reading in the help file it says I can start Sudoku from the command line by typing gnome-sudoku and pressing enter. I tried this and it gives me some additional text, but I don't know what to do with it, and hoping someone here can lend me their expertise. Below is the response from the command line:

```
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 50, in <module>
    start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/gnome_sudoku.py", line 21, in start_game
    main.start_game()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 1051, in start_game
    u = UI()
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 195, in __init__
    if self.select_game():
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 60, in _
    ret = fun(ui,*args,**kwargs)
  File "/var/lib/python-support/python2.5/gnome_sudoku/main.py", line 209, in select_game
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

sh: bug-buddy: not found

```

Thanks in Advance - 

David

---

### Post by powe309 on 2009-01-01
Sorry, I don't have any suggestions. but I can confirm that I am having the same issue.  Sudoku was definitely working yesterday, but today it is behaving exactly as you describe.  I have not made any changes or installed any software or updates recently, so I don't know what might have triggered the problem.  If you figure anything out, please post your solution.  I will be sure to do likewise.

---

### Post by kokkus on 2009-01-01
That happend to me but with Bejeweled. I reinstalled the package with the package manager and now it works fine again if that helped you out.
If not, you can always try some of the other many sudoku games you can find in the add/remove section. there are at least 3 of them.

---

### Post by powe309 on 2009-01-01
> **kokkus said:**
> That happend to me but with Bejeweled. I reinstalled the package with the package manager and now it works fine again if that helped you out.
If not, you can always try some of the other many sudoku games you can find in the add/remove section. there are at least 3 of them.

I have already uninstalled and reinstalled the gnome-games package.  Unfortunately, that didn't seem to have any affect.  It's not that I have a desperate need to get it working, I would just like to figure out what caused it to quit in the first place.

---

### Post by Copernicus1234 on 2009-01-01
No idea, the game works for me.

Maybe delete your ~/.sudoko folder just to see if it helps? You can always take a backup first.

---

### Post by powe309 on 2009-01-01
Apparently it is a known bug.  Here is the link:

[https://bugs.launchpad.net/gnome-games/+bug/270644]("https://bugs.launchpad.net/gnome-games/+bug/270644")

Deleting ~/.sudoku fixes the problem as long as you don't mind losing your saved games.

---

### Post by stndrdsnz on 2009-01-01
I sort of followed the directions to remove the ~/.sudoku folder. Instead though, I went in and deleted the ~/.sudoku/saved directory and then tried it and it worked. Since I was able to keep my ~/.sudoku/finished directory I believe my record is saved. Anyhow...I appreciate the suggestions. I felt kind of silly asking about a game, but on the flip side it gets really frustrating when things just stop working.

Thanks,

David

---

