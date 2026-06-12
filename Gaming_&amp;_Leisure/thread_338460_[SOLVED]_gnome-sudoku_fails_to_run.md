---
title: "[SOLVED] gnome-sudoku fails to run"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by ubuntu27 on 2007-01-14
Hi everyone.
I have a little problem.

I've installed gnome sudoku with aptitude

and the game worked good for a while (two days)

But then, whenever I click on the launcher, gnome-sudoku doesn't run at all. It simply changes the cursor to waiting pointer, and then "plop!" it dessapairs. And nothing else happens.

Here is the output on the terminal:

```
ubuntu27@heaven:~$ gnome-sudoku
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 11, in ?
    start_game()
  File "/var/lib/python-support/python2.4/gnome_sudoku/gnome_sudoku.py", line 915, in start_game
    u = UI()
  File "/var/lib/python-support/python2.4/gnome_sudoku/gnome_sudoku.py", line 355, in __init__
    self.sudoku_maker = sudoku_maker.SudokuMaker()
  File "/var/lib/python-support/python2.4/gnome_sudoku/sudoku_maker.py", line 309, in __init__
    self.load()
  File "/var/lib/python-support/python2.4/gnome_sudoku/sudoku_maker.py", line 394, in load
    loaded = pickle.load(ifi)
  File "/usr/lib/python2.4/pickle.py", line 1390, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.4/pickle.py", line 872, in load
    dispatch[key](self)
  File "/usr/lib/python2.4/pickle.py", line 935, in load_int
    val = long(data)
ValueError: invalid literal for long(): 
ubuntu27@heaven:~$ 
```

Any ideas on how to solve this?

---

### Post by ubuntu27 on 2007-01-18
**bump!!**

No ideas at all? :confused: 

I need your help guys. 

I will just wait for your reply. :)

---

### Post by elamericano on 2007-02-20
Broken here too. Hasn't worked in months.

I think something I updated broke it. The ubuntu package is version 4.0. I tried the 6.3 debian package and compiled the 7.1 from source, but nothing works. That python error is useless to me, so I'm not going to worry about it. There are a couple other sudoku packages available.

Sorry I can't help.

---

### Post by elamericano on 2007-03-06
What do you know, I got this working today:

```
 rm -rf ~/.gnome2/gnome-sudoku/*
```

It makes sense that it would be dependent on a config error, since the code works for most people, and a reinstall of the latest code didn't fix it.

You'll probably never see this since it's been months since you asked the question.

---

### Post by Somenoob on 2007-03-06
I think it's deb file is corrupt, better install it from source. I installed it from it's setup.py file from the tarrball. It works perfectly on my machine. 

```
tar -zxf gnome-sudoku-0.3.1.tar.gz
cd gnome-sudoku-0.3.1
sudo python setup.py install
```

[http://sourceforge.net/project/showfiles.php?group_id=142841&package_id=156818]("http://sourceforge.net/project/showfiles.php?group_id=142841&package_id=156818")

---

### Post by elamericano on 2007-03-09
> I think it's deb file is corrupt...

He said it worked for two days, so that can't be the problem. I'm sticking with my corrupt configuration file theory.

---

### Post by ubuntu27 on 2007-03-09
> **elamericano said:**
> What do you know, I got this working today:

```
 rm -rf ~/.gnome2/gnome-sudoku/*
```

It makes sense that it would be dependent on a config error, since the code works for most people, and a reinstall of the latest code didn't fix it.

You'll probably never see this since it's been months since you asked the question.


Hey thank you, haven't tried that code yet, what does it do?

rm = remove
-rf =   ???


I submited a bug report for Gnome-Sudoku... But looks like nobody wonders around that bug tracker.

[Gnome-Sudoku Bug N. 1675507]("http://sourceforge.net/tracker/index.php?func=detail&aid=1675507&group_id=142841&atid=753666")

> **Somenoob said:**
> I think it's deb file is corrupt, better install it from source. I installed it from it's setup.py file from the tarrball. It works perfectly on my machine. 

```
tar -zxf gnome-sudoku-0.3.1.tar.gz
cd gnome-sudoku-0.3.1
sudo python setup.py install
```

[http://sourceforge.net/project/showfiles.php?group_id=142841&package_id=156818]("http://sourceforge.net/project/showfiles.php?group_id=142841&package_id=156818")



Looking at:
[http://gnome-sudoku.sourceforge.net/](http://gnome-sudoku.sourceforge.net/)

I see that the current version is 0.7.1
and the version that Ubuntu Edgy ships is 0.5.0

@Somenoob: That tar, it contains an old version os Gnome-Sudoku (0.3.1) better upgrade it ;)

---

### Post by elamericano on 2007-03-12
> Hey thank you, haven't tried that code yet, what does it do?

rm = remove
-rf = ???
-rf is recursive (for directories - there probably aren't any) and force (just to avoid being prompted for confirmation) You could leave these off and you'd get to the same point.

The .gnome2 folder is a hidden subfolder in your home directory which stores the config information for your user account for many gnome applications. The command will empty the gnome-sudoku folder. The program will recreate these files when it runs, but will forget all saved information for this application, which is what you want.

I've tried the latest version and it looks exactly the same as 0.5. I would just stick with the repository version unless you have a reason to bother with the upgrade.

---

### Post by ubuntu27 on 2007-04-06
Bug reported at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/103602](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/103602)

---

### Post by ubuntu27 on 2007-08-26
Just wanted to say that the problem has been solved thanks to elamericano

with this

> **elamericano said:**
> What do you know, I got this working today:

```
 rm -rf ~/.gnome2/gnome-sudoku/*
```

It makes sense that it would be dependent on a config error, since the code works for most people, and a reinstall of the latest code didn't fix it.



This thread was created when I was using Edgy. In feisty so far I haven't found any problems.

I'm going to mark [SOLVED] for this thread.

---

