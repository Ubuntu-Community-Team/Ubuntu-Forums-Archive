---
title: "Diablo 1 Linux via Cedega"
date: 2005-08-20
forum: Gaming &amp; Leisure
---

### Post by Mishura on 2005-08-20
**_Diablo 1 in Ubuntu Hoary using Cedega 4.4_**

That's right, folks.. I actually got Diablo to work, and its playable to an extent.  This is the first time Diablo has been playable in Linux, ever.

_Things you will need:_

1.  Diablo CD
2.  Transgaming's Cedega 4.4 (CVSCedega untested)

_Recommended:_

1.  Patience
2.  1.09 patch.

_What to do:_

Make sure Cedega is installed and fully functional.  Once you feel that it is, **mount** your Diablo CD.

In your Diablo CD, run the setup program with Cedega.
```

$ cedega ./autorun.exe
```

Install the full game.

Now go to [http://blizzard.com](http://blizzard.com) and find the latest patch (1.09).  It's not necessary, since 1.00 worked as well, but I personally recommend it.  Run it through Cedega.

Now.  I hope you remembered where you installed it.  Go to your diablo directory and launch it:
```

$ cedega ./Diablo.exe
```

Before you even THINK of creating your character, you will need to create some useless NULL characters.  Create 6 or 7 of them (Name em:  Null0, Null1, Null2, etc.. but it doesn't matter.)  If you want to know why, check this:  [http://digital-conquest.ath.cx/wiki/index.php/Diablo](http://digital-conquest.ath.cx/wiki/index.php/Diablo)

Once you created your null characters, and you can scroll through the list (You will probably need to click on a name, and use your keyboard to scroll.);  Then you can create your character.  Play it.

Now if you want to load your character, Go to Load Game, and scroll through the list once, then select your character.  You know you did good, when you can see your Character's Skill sheet on the left side.  If you don't see it, then scroll ALL THE WAY, and try again.

_Major issues:_

1.  When you go to name your character, you will need to click in a invisible box, but you know you hit it when you can see pentagrams on both sides of the input box.

2.  Keep your null characters.  They are only there so you can load your real ones up.

3.  Battle.net seemed to work, but I didn't join or start a game to really test it.  The chat interface seemed to work without any graphic glitches or anything.

4.  I played a Warrior character all the way to Level 5 and Dungeon level 3.  No problems, no crashes or graphical glitches.  It's as if you are playing it in Windows.  No performance problems either.

5.  Neither WineHQ's Wine or Codeweavers' Wine will work.  Only the official Cedega 4.4 has been tested to work.  I tested using Wine 20050725.  Previous versions of Cedega or WineX should not work at all.  (Why?  Cuz getting Diablo 1 to work has been a side-project of mine for 4 years!)

_Things I'd like to know:_

I'm interested in how many people can actually play Diablo well in Linux with different varieties of emulation or anything else.  What I'd like to know is, if you can get it to work:

1.  What version of Wine/Cedega used
2.  Can CVS Cedega do it?
3.  What about WineCVS or DX9Wine?
4.  How about QEMU and Windows?
5.  Most important:  A way around the null character scroll hack.. so I can just load save games like I do in windows.

_Disclaimer:_

I can't guarantee that this will work for you.  It worked for me and that's all.  If it works for you, let me know.  If it doesn't work, then there is little I can do.

I'd like to credit the Unofficial Transgaming Wiki for the help in dealing with loading save games.

Also, if it crashes your computer, neither Blizzard, Transgaming, Me, Canonical, Linus Torvalds, or the Bush Administration is responsible for it.  Its your problem, so don't go blaming people!  Don't worry, the chances of Cedega destroying your filesystem is very very slim.

---

