---
title: "Games think I am holding down a key when I am not?"
date: 2010-03-24
forum: Gaming &amp; Leisure
---

### Post by whein on 2010-03-24
Like the title says, there are some games I've installed from the repos and when I go to play them they behave as if I am constantly holding down one or more keys.  For example, kq thinks I am holding down whichever key advances the menu (probably down arrow) and SDL-Ball thinks I am constantly moving the paddle to the left (left arrow?).  Only seems to affect games that run in full-screen mode (i.e. no Gnome desktop decorations visible) though that could just be a matter of too small a sample.  So far all the non-full screen games I've tried work as expected, if they work at all.  Thoughts/suggestions?

-Will

9.10 on AMD64 with Gnome + Compiz

---

### Post by Carpentr on 2010-03-25
Have you tried another keyboard? As silly as this sounds, is there perhaps something stuck inside your keyboard? 

I used to have this issue all the time with my keyboard and it turned out something was wrong with the connector. I had to take it out and plug it back in a few times to get it working.

If it works in all windowed games, then I'm guessing it's a software problem.

EDIT: Also, try going to System --> Preferences --> Keyboard  and uncheck the repeat keys option. See if that helps. Try fidgeting around with the other settings too.

---

### Post by whein on 2010-03-25
Well, given that the only time I EVER see this phenomena is with a handful of games, and they are always the ones that take over the entire screen I don't think it's a bad keyboard.  I never see "sticky keys" when I use a text editor or play a windowed game so I think it has something to do with whatever happens when Gnome goes away (or hides in the background) and the game takes over the graphics/mouse/keyboard.  Problem is I have exactly zero experience with any of that stuff other than Java programming, which runs in a window, so Gnome still manages the back end.

:(

-Will

---

### Post by Carpentr on 2010-03-25
You could try switching to KDE and see if that makes a difference. Maybe you could even upgrade to Lucid and see if that fixes anything? Lucid seems a lot more stable than Jaunty and Karmic IMHO.

EDIT: Problem is that you will lose your data if you don't back it up. I mean, the two options above will probably help, but they involve a big upgrade on your machine. If it's worth it to you, then I'd say go for it. Otherwise, just tinker around with your system and try and find a solution. Granted, messing around with your computer's settings to try and find a fix can take hours, weeks, maybe even months depending on the issue.

---

### Post by themusicalduck on 2010-03-25
You don't happen to have a Microsoft keyboard do you? I had this problem with mine, and it turns out Ubuntu thought the keyboard was a joystick (for some really weird reason).

Try running this command see if it fixes it ```
jscal -c /dev/input/js0
```

It doesn't last though, you have to repeat it when you want to play a game, or when it is playing up. I've just made a launcher on my panel with that code in.

---

### Post by whein on 2010-03-25
> **themusicalduck said:**
> You don't happen to have a Microsoft keyboard do you? I had this problem with mine, and it turns out Ubuntu thought the keyboard was a joystick (for some really weird reason).

Try running this command see if it fixes it ```
jscal -c /dev/input/js0
```

It doesn't last though, you have to repeat it when you want to play a game, or when it is playing up. I've just made a launcher on my panel with that code in.

Bingo!  I have a Microsoft USB keyboard and entering the above into a terminal (after installing the joystick package) made the problem go away for both the games mentioned previously.

So my next questions for the group are:
1) why the hell does Ubuntu think that my keyboard is a joystick?
2) how do I convince it otherwise?

Thanks for the help.  :)

-Will

---

### Post by themusicalduck on 2010-03-26
> 1) why the hell does Ubuntu think that my keyboard is a joystick?
2) how do I convince it otherwise?

I have no idea :D

I searched around about how to disable a joystick and made a thread about it a while back but got no answers.

Eventually I filed a bug report about the keyboard here - [https://bugs.launchpad.net/ubuntu/+bug/390959](https://bugs.launchpad.net/ubuntu/+bug/390959) though it hasn't had much attention in the last year.

---

