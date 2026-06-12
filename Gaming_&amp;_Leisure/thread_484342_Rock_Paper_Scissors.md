---
title: "Rock Paper Scissors"
date: 2007-06-25
forum: Gaming &amp; Leisure
---

### Post by leetcharmer on 2007-06-25
I just created a Rock Paper Scissors game with python in the command line.  It's my first program :D!  I want to know if you can break it, also, what do you think would make it better?  Try it out.  I want to increase my skills at programming.  Is it fun?

Download it and give it a shot :D!

If you can't figure out how to play it, try this first:

```
user@host:~$ chmod +x rps.py
user@host:~$ ./rps.py
```

K thx :D!!

---

### Post by Dylnuge on 2007-06-26
First off, congratulations, and welcome to the world of programming!

Unfortunatly, I can't seem to open the file-probably a corrupted download on my end, I will try again when I get home. (Tried it with UTF too, still have a encoding error).

Re-downloaded, it works now. A few things you might want to fix:

```
PREPARE FOR BATTEL!!
```

That's Battle.

```
Must be an odd number of rounds and more than 1, try again!
```

Why the odd number? Why more then one? Try to remove those limitations.

Other than that, it is fine.

PS: I think this belongs in cafe or some other discussion thread, since it is not a support topic.

---

### Post by Motoxrdude on 2007-06-26
It's a game. Why wouldn't it be in the gaming and leisure section?

---

### Post by cogadh on 2007-06-27
Because this forum is generally used for getting community tech support for gaming on Ubuntu, not advertising/soliciting beta testers. Personally, I think it's OK to leave it here.

Oh, and I'll be giving the game a shot tomorrow when I get back to my 'Buntu box. :)

---

### Post by Motoxrdude on 2007-06-28
Hahah, that's pretty neat. Thanks for the upload ;)

---

### Post by leetcharmer on 2007-07-26
> **Dylnuge said:**
> Re-downloaded, it works now. A few things you might want to fix:

```
PREPARE FOR BATTEL!!
```

That's Battle.

```
Must be an odd number of rounds and more than 1, try again!
```

Why the odd number? Why more then one? Try to remove those limitations.

lawl.  Haven't you seen old Japanese films of fighting?  They always go battel ... anyway, what is a rock paper scissors game without best two out or three? or best 5 out 6, etc?

---

I want to add graphics soon, should I get plugged into pygame to do so?  or learn how to work with GTK?

---

### Post by Dylnuge on 2007-07-30
I would try Tkinter-don't know tons about Pygame.

Only one match should be a possibility no matter what you think of it. The odd number restriction seems to be so that the player and computer do not tie-however, I think allowing ties would be fine. Oh, and there is no such thing as best 5 out of six. It is half of an odd number plus .5 (with that, you have won more then hald). IE: Half of three is 1.5, you can't win 1.5 matches, so the next highest whole number is 2. Half of 15 is 7.5, so its best 8 out of 15. It would be best 4 out of 6, since both players could win exactly three matches-resulting in a tie.

Back to graphics-try a simple dialoge interface before adding any animation. Also, some more things you could consider adding:

1. Right now, this is essentally a coin flipper game-the computer randomly chooses a winner. While this is fine, try giving the player a choice between Rock Paper or Sissors. Yes, I know it won't effect the computer's decision, and therefore is still random, but why not?

2. Create a tally system. I don't care how it works-that is up to the designer (you). Two ideas-keep track of each indivdual game, keep track of each set (who wins in a best of three, etc). Maybe keep a log file. Clearly high scores are not a part, but whatever.

3. Scrap this project and move on. I know it sounds weird, but right now you have succeded in making your first game. It involves (some) user interaction, may soon have a GUI, and uses a RNG for more complex purposes then just getting a number (it chooses both the player and computer's hand, then compares those). It lacks any skill though-all the user can do is type a number and hope. There is nothing you can do to change this. Trust me, you will have more fun starting a new project.

Good Luck,
Dylan

PS: Be careful in your new projects. Don't go crazy, but try to challenge yourself-try something you don't think you can do, but that is close to the edge-no MMORPGs, no coin flipping simulations.

---

### Post by Xuewen on 2009-01-21
Is there any new version of [scissors](http://www.scissorsforsale.com/) game?

---

