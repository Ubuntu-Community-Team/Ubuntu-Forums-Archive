---
title: "Alternative to BabasChess?"
date: 2009-09-03
forum: Gaming &amp; Leisure
---

### Post by MrNatewood on 2009-09-03
I'm looking for a native linux alternative to babaschess, any ideas?
Yes, It does work with Wine, but there are crashes and glitches, so I'm looking for something native.

So far i couldn't find another program offering the combination of two features that I need:

a. Playing at FICS
b. Analyzing the game I just finished instantly with a chess engine

---

### Post by 569874123 on 2009-09-06
> **MrNatewood said:**
> I'm looking for a native linux alternative to babaschess, any ideas?
Yes, It does work with Wine, but there are crashes and glitches, so I'm looking for something native.

So far i couldn't find another program offering the combination of two features that I need:

a. Playing at FICS
b. Analyzing the game I just finished instantly with a chess engine

I get the following in appdb
> 
will cause program to crash without native riched20.dll

---

### Post by rafita on 2009-09-07
scid: [http://scid.sf.net](http://scid.sf.net)

---

### Post by MrNatewood on 2009-09-11
I tried replacing the riched20.dll in system32, it didn't help.

Thanks for the advice on scid, I am able to analyze with it. What I was looking for though is an app that integrates playing in FICS and analyzing the games when they are done, "on the fly". without having to open the game in another application. Like in babas, to click on a button after a game is done and have it analyzed.

---

### Post by BFris on 2010-02-28
I know this is an old thread, but thought I'd respond anyway. I've been using BabasChess for a while in wine. 

To get it to work, you have to
[INDENT][LIST=1]
[*]copy riched20.dll to fake windows\system32 directory
(~/.wine/drive_c/windows/system32 or similar)
[*]tell wine to use native version of riched20. under
"Configure wine" program, select BabasChess application,
then switch to Libraries tab and select riched20.dll and 
specify Native(Windows)
[/LIST][/INDENT]

Some folks have said they had trouble with gdiplus.dll. Has the same fix -- use native.

---

