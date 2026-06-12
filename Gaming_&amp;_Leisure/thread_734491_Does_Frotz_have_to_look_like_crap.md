---
title: "Does Frotz *have* to look like crap?"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by LodeRunner on 2008-03-24
Am trying to play some text adventure games, but Frotz uses the default Gutsy monospace font, which makes reading any significant amount of text very hard on the eyes (also--is it just me... did monospace fonts *always* look *this* bad?  I swear I'm seeing letters that were actually OVERLAPPING slightly.) 

I asked [here]("http://ubuntuforums.org/showthread.php?p=4252401") how to change the default terminal font to a non-monospaced, and was told it wasn't possible.

So... how is everyone else playing z-code games?  Surely, you can't *all* be putting up with this ugly mess.

---

### Post by DoktorSeven on 2008-03-24
I use WinFrotz through Wine.  We really need a non-terminal based version like they have...

---

### Post by LodeRunner on 2008-03-25
That is so sad... I've come to accept that Linux gaming support sucks, but we can't even get proper support for a decades-old TEXT ADVENTURE format???

Seriously, is there no other Linux-native z-code interpreter?  Is there no terminal program that supports proportional fonts?  :confused:

---

### Post by DoktorSeven on 2008-03-25
Don't be negative about Linux gaming in general just because no one has taken the time to do a different zcode interpreter.  Linux gaming support is awesome, but to get everything you want, someone has to have the motivation and time to do what you want.  At least we have the ability to run some of the things for another platform.

Also, I remember there was a Java-based one available once but can't remember the name.

---

### Post by LodeRunner on 2008-03-25
Linux gaming support is not "awesome" by any objective standard.  The effort that volunteers have given is awesome--I'm not dissing the progress that has been made--but Linux is not superior to any other platform for any type of gaming, period (even for oldschool, Dosbox runs just as well under Windows.)  

And that doesn't have anything to do with the current situation.  This is TEXT we're talking about here, not some proprietary API. It affects more than just games--man pages are similarly painful to read. The consoles (control + alt + F1-F6) are a bit better, but are cumbersome, completely uncustomizable, and very low resolution (plus no subpixel hinting.)

I don't care if proportional fonts break aptitude or some other CLI programs that I **never** use.  It goes against the spirit of Linux to force such ridiculous restrictions upon the user without any possibility of an override.  It's not just *annoying*... it's actually affecting my health by making my eyestrain even worse.

Wine is awesome, yes.  Major kudos to the developers. However... using it to VIEW TEXT because Terminal refuses to render the text properly is--again--very very **sad**.

---

### Post by heartburnkid on 2008-03-25
Have you tried [Kwest](http://kwest.sourceforge.net/)?  I'm not big on text adventures, but it sure seems a lot nicer than terminal-based Frotz from looking at it.  It's KDE-based, but I don't think that's a huge obstacle.

---

### Post by FranMichaels on 2008-03-25
It is possible to modify the terminal font. In gnome-terminal, edit -> profile, choose edit, choose the font.
Not hard. Harangue not worth it.
Anyway, I just gnome-terminal and zoom it in (ctrl ++) As for the settings, custom color scheme.

If you mean the ctrl f full screen terminal, no clue. I still like to multitask, and have the gnome-terminal full screen (can still see my panel etc.)

---

### Post by LodeRunner on 2008-03-25
FranMichaels: Yes, you can change the font.  However, no matter what you choose, the terminal will attempt to make it monospaced, even if it's a proportional (non-monospaced) font.  Some brief experimenting suggests that non-monospaced fonts actually look a **LOT** worse than the monospaced ones, because of the forced monospacing Terminal applies as an afterthought.  Specifically, if you attempt to use a proportional font the result is a monospaced font that's so crappy, the letters are actually ON TOP OF EACH OTHER.  I'm serious--try it.

The problem isn't confined to Ubuntu, either.  I ran into the same problem on my Sharpe Zaurus C1000 running OpenZaurus/GPE--the absurd spacing made doing serious work in the terminal nearly impossible.

So no, there is no way to make the font proportional (i.e. easily readable), and it is most certainly worth the harangue.  In fact, as soon as I have a afternoon to spare I intend on figuring out whomever's responsible (the Terminal devs, maybe) and giving them an earful.

heartburnkid:  Thank you, I will give that a try tomorrow.  I've poked around before for alternatives, but it seemed like absolutely everyone was using Frotz.  I suppose everyone else's eyes are more calloused than my own.

---

### Post by DoktorSeven on 2008-03-26
All I can tell you is that traditionally, console fonts are monospace out of necessity, and really no effort has been made to change this because honestly, monospace is the way many people want to see text in a terminal -- otherwise some things won't line up properly because it's historically used to expecting a monospace font.

As you said, it's probably not the best if you want "nice" fonts, but it's always served me well, since I'm of the opinion that as long as it's large enough to read, I really don't care what the font looks like.

In other words, if you want a nice font, you basically want a GUI window, and again, no one has taken Frotz and converted it to a Linux GUI form.  And by the way, decades ago when these games were new -- they WERE using a "crappy-looking" monospace format on the old computers they ran on!

On another note, I argue that Linux gaming IS quite awesome, thank you.  Struggling with Windows and its terrible memory management that slows down games?   No thanks.  I would much rather have Linux as the PC game platform.  It is quite awesome.  Course, that's my opinion, you're welcome to yours, but I'm just justifying my own statement here.

---

### Post by Vadi on 2008-03-26
... eh? Linux gaming support sucks because of a text game?

XD

---

### Post by heartburnkid on 2008-03-26
> **DoktorSeven said:**
> In other words, if you want a nice font, you basically want a GUI window, and again, no one has taken Frotz and converted it to a Linux GUI form.

Except the guys who made Kwest, apparently.

---

### Post by jjk7288 on 2008-03-26
> **DoktorSeven said:**
> On another note, I argue that Linux gaming IS quite awesome, thank you.  Struggling with Windows and its terrible memory management that slows down games?   No thanks.  I would much rather have Linux as the PC game platform.  It is quite awesome.  Course, that's my opinion, you're welcome to yours, but I'm just justifying my own statement here.

I love Linux just as much as the next guy, but lets not go around making BS devil's advocate statements.

When 95% of commercial games are designed for Windows and have NO Linux port (regardless of how "bad" Windows memory management may be) then Linux is not a viable system for gaming. It works great for everything else - but until Linux gains the mainstream support of developers (or Wine/similar efforts expand their compatibility), it will always be a second class gaming OS.

Although I will say I do enjoy it quite a bit when I can get games to run on Linux.

---

### Post by Grishka on 2008-03-27
> **LodeRunner said:**
> Am trying to play some text adventure games, but Frotz uses the default Gutsy monospace font, which makes reading any significant amount of text very hard on the eyes (also--is it just me... did monospace fonts *always* look *this* bad?  I swear I'm seeing letters that were actually OVERLAPPING slightly.) 

I asked [here]("http://ubuntuforums.org/showthread.php?p=4252401") how to change the default terminal font to a non-monospaced, and was told it wasn't possible.

So... how is everyone else playing z-code games?  Surely, you can't *all* be putting up with this ugly mess.


of course we can't be putting up with this ugly mess. :-) you need [Gargoyle]("http://ccxvii.net/gargoyle/"), buddy. you'll love it.
all the best.

---

### Post by DoktorSeven on 2008-03-27
> **jjk7288 said:**
> I love Linux just as much as the next guy, but lets not go around making BS devil's advocate statements.

It's not "BS", really.  Sure, there aren't a huge amount of games ported to Linux, but the ones that do -- and even many of the ones running in Wine -- perform better for me than they do in Windows.  The only thing holding Linux back as a game platform is its adoption, and since Microsoft has basically set itself up as a majority share, that's where the games will go.  It's backwards to say that Linux is an inferior platform for games just because Microsoft happens to have control of most of the desktops.  And continuing the attitude that Linux is inferior only hurts any future prospects.

I think that gaming on Linux is really going to take off -- with more people going to Linux, it really can't be ignored.  But being negative about the whole thing isn't going to help.

---

### Post by Grishka on 2008-03-28
> **Grishka said:**
> of course we can't be putting up with this ugly mess. :-) you need [Gargoyle]("http://ccxvii.net/gargoyle/"), buddy. you'll love it.
all the best.

oh yeah, sorry for quoting my own post. just wanted to clarify a thing or two. Gargoyle is a frontend for interactive fiction games in various formats. it can run z-code games, those made with TADS, Hugo games, old Level 9 hits and more. and it's not a terminal app. Gargoyle uses custom versions of Frotz and other interpreters, so you can play the game in a gtk window on your desktop.

cheers.

---

### Post by gspawn69 on 2008-06-19
I'm just wondering...

I have Gargoyle installed, and I even updated it with the patch from [http://ifarchive.plover.net/indexes/if-archiveXinterpreters-multiXgargoyle.html](http://ifarchive.plover.net/indexes/if-archiveXinterpreters-multiXgargoyle.html) but I can't get the frontend to work.

When I type 'gargoyle' in the terminal, I get:

```

[: 22: ==: unexpected operator
[: 32: ==: unexpected operator
gargoyle: Cannot access file:

```

But, if I specify a filename, it gives the same error message but then the game loads. Has anyone else had this problem and know how to get the frontend to work?

---

### Post by Grishka on 2008-06-23
> **gspawn69 said:**
> I'm just wondering...

I have Gargoyle installed, and I even updated it with the patch from [http://ifarchive.plover.net/indexes/if-archiveXinterpreters-multiXgargoyle.html](http://ifarchive.plover.net/indexes/if-archiveXinterpreters-multiXgargoyle.html) but I can't get the frontend to work.

When I type 'gargoyle' in the terminal, I get:

```

[: 22: ==: unexpected operator
[: 32: ==: unexpected operator
gargoyle: Cannot access file:

```

But, if I specify a filename, it gives the same error message but then the game loads. Has anyone else had this problem and know how to get the frontend to work?

it's not a graphical frontend and there's no gui. it's function is just that - running the games in a nice window on your desktop.

---

### Post by AprilHare on 2009-02-20
Frotz for the Amiga is different: it supports graphics and is quite arguably the best Z-machine interpreter of them all.
Perhaps someone needs to create a GnomeFrotz along the same lines.
Kwest would be nice but it needs packaging for Ubuntu (I understand there are licence issues). There is a quick and dirty i386 compile of Kwest for Ubuntu floating around but since I'm using AMD64 it's not much use.

---

### Post by farvardin on 2009-04-26
It's annoying not to be able to change the proportional font display. I've filled a bug report on the gnome bugzilla:

[http://bugzilla.gnome.org/show_bug.cgi?id=580298](http://bugzilla.gnome.org/show_bug.cgi?id=580298)

This new interpreter desserves more than monospace fonts:
[http://spellbreaker.org/~chrender/fizmo/](http://spellbreaker.org/~chrender/fizmo/)

---

### Post by Grishka on 2009-04-26
> **farvardin said:**
> It's annoying not to be able to change the proportional font display. I've filled a bug report on the gnome bugzilla:

[http://bugzilla.gnome.org/show_bug.cgi?id=580298](http://bugzilla.gnome.org/show_bug.cgi?id=580298)

This new interpreter desserves more than monospace fonts:
[http://spellbreaker.org/~chrender/fizmo/](http://spellbreaker.org/~chrender/fizmo/)

yay, I didn't know that one. :)
edit: blorb support in a cli app? what's the point?:confused:

---

### Post by farvardin on 2009-04-26
It's for graphical terminal. You get the cover of games with babel (blorb) informations. The cover displays in the terminal, it looks great.

It stores also the games you've played before, so it's a very conveniant application.

---

### Post by Grishka on 2009-04-26
> **farvardin said:**
> It's for graphical terminal. You get the cover of games with babel (blorb) informations. The cover displays in the terminal, it looks great.

It stores also the games you've played before, so it's a very conveniant application.

umm, cover? I'm sorry, I know what a blorb file is, but this interpreter won't run neither gblorb nor blb games, and zblorb games show no pictures.
edit: aaah, I got what you mean. I haven't thought to run fizmo all by itself till now. :)

---

