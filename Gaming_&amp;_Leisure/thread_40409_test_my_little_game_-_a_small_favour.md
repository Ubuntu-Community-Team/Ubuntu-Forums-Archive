---
title: "test my little game - a small favour"
date: 2005-06-09
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-06-09
hey everyone.  last year i sunk some time into programming a little python game called openFantasy.  basically it is an attempt to create a little RPG that mirrors the functionality of the old NES dragon warrior and final fantasy games.  i am using the language python.

you can snag it here: [http://cs.georgefox.edu/~jdodson/files/openFantasy_0.1.0.tar.bz2](http://cs.georgefox.edu/~jdodson/files/openFantasy_0.1.0.tar.bz2) - 92k 

anyways, any ubuntu version "should" run the game with no troubles.  just un bzip2 the file, un tar it and in the openFantasy directory type:

python openFantasy.py

and everything should work fine.  anyways, let me know what you think.  you should only be able to talk to people, have a few cutscenes go by, and trade items to have things happen, like doors opening, etc.  you should also be able to push trigger objects to make things happen as well, like reveal a hidden character or open a gate or something.  you should be able to trade items to get out of the first village and enter a larger world that is shockingly devoid of any real substance.

the level files are .csv files made with open office calc to make level construction a snap.  just load the .sxc file, make your changes, pray they are legal(i.e. i have pretty strict bounds checking, as in if you deveate from my format, the game will die) and everything will be fine(i think:) ).  

so test it out and let me know what you think.  i plan to implement a WAY better story, sofar the one i included is lame, it is just for testing the engine.  and i plan to implement a turn based fighting system, a save feature and then finish the game.

thanks.

p.s. dont laugh at the graphics, i am not a uber-artist.  ok i am not a very good artist either:)

---

### Post by The Na Kun on 2005-06-09
Alright, I'm downloading now.  I'm going to have to switch over to ubuntu and pray that there isn't some dumbass "you need [this] program to play, so I'm going to make you download it, in which you need to download 400 more programs and waste your life."  No internet on ubuntu sucks..  So time to test, reporting back soon...

---

### Post by bored2k on 2005-06-09
Ok Zorgoth is the most annoying character ever LOL . This game reminds me of a software you probably know called RPG Maker.

Dude you are the funniest person ever LOL. What's with the Santa Claus wannabe magicians (ho ho ho)? This is so funny... Bridgman rocks !

---

### Post by bored2k on 2005-06-09
[QUOTE=The Na Kun]Alright, I'm downloading now.  I'm going to have to switch over to ubuntu and pray that there isn't some dumbass "you need [this] program to play, so I'm going to make you download it, in which you need to download 400 more programs and waste your life."  No internet on ubuntu sucks..  So time to test, reporting back soon...[/QUOTE]
 Just download python from python.org dude.

---

### Post by bored2k on 2005-06-09
Ok the game worked, but I noticed this:
>  python openFantasy.py
Fontconfig error: "local.conf", line 4: mismatched tag


---

### Post by jdodson on 2005-06-09
[QUOTE=bored2k]Ok the game worked, but I noticed this:[/QUOTE]

what did you do to get that?

---

### Post by bored2k on 2005-06-09
[QUOTE=jdodson]what did you do to get that?[/QUOTE]
 Nothing, I just loaded the game up. I reloaded it and got the same thing again. Without even touching the game, just by firing it up.

---

### Post by jdodson on 2005-06-09
[QUOTE=The Na Kun]Alright, I'm downloading now.  I'm going to have to switch over to ubuntu and pray that there isn't some dumbass "you need [this] program to play, so I'm going to make you download it, in which you need to download 400 more programs and waste your life."  No internet on ubuntu sucks..  So time to test, reporting back soon...[/QUOTE]

ha, right, no offense, i wasnt thinking about the windows users.

to play this game in windows you need to download python:

[http://www.python.org/ftp/python/2.4.1/python-2.4.1.msi](http://www.python.org/ftp/python/2.4.1/python-2.4.1.msi)

get the gtk runtime enviornment for windows:

[http://prdownloads.sourceforge.net/gimp-win/gtk%2B-2.6.7-setup-1.zip?download](http://prdownloads.sourceforge.net/gimp-win/gtk%2B-2.6.7-setup-1.zip?download)

the pygtk library:

[http://www.pcpm.ucl.ac.be/~gustin/win32_ports/binaries/pygtk-2.6.2-1.win32-py2.4.exe](http://www.pcpm.ucl.ac.be/~gustin/win32_ports/binaries/pygtk-2.6.2-1.win32-py2.4.exe)

that should be everything to get it to run.

---

### Post by jdodson on 2005-06-09
[QUOTE=bored2k]Nothing, I just loaded the game up. I reloaded it and got the same thing again. Without even touching the game, just by firing it up.[/QUOTE]

looks like it is a font error, i will check it out a bit, if the game plays it might not be a big deal.  sounds like its not game threatening, thanks for the report.

---

### Post by The Na Kun on 2005-06-09
Amasing.. It's like the first thing that works!!

So yeah, interesting game you got there.  I wish it was longer, though.  Still, cool.

---

### Post by DirtDawg on 2005-06-09
What a cool thing to ask people to do! My finals are tommorow, but after that I'm all over some play testing.

---

### Post by DirtDawg on 2005-06-09
or is it "test playing"?

---

### Post by jdodson on 2005-06-09
[QUOTE=The Na Kun]Amasing.. It's like the first thing that works!!

So yeah, interesting game you got there.  I wish it was longer, though.  Still, cool.[/QUOTE]

it will be longer when i get more to it, i was thinking about building up a small game where you traded around items to beat the game.  i might do that this weekend if i have some time.  

i was thinking about implementing a fighting system.  do people think multi-characters like final fantasy 2 for SNES would be cool, or just the simple dragon warrior one character fight system?  i was thinking multi-char, but wanted some feedback on that.

---

### Post by bored2k on 2005-06-09
[QUOTE=jdodson]it will be longer when i get more to it, i was thinking about building up a small game where you traded around items to beat the game.  i might do that this weekend if i have some time.  

i was thinking about implementing a fighting system.  do people think multi-characters like final fantasy 2 for SNES would be cool, or just the simple dragon warrior one character fight system?  i was thinking multi-char, but wanted some feedback on that.[/QUOTE]
 Depends on how complex the fighting system will be. I would personally prefer a robust one character fight system over a "Final Fight" generic type punch kick fire between 3 characters.

---

### Post by jdodson on 2005-06-09
[QUOTE=bored2k]Depends on how complex the fighting system will be. I would personally prefer a robust one character fight system over a "Final Fight" generic type punch kick fire between 3 characters.[/QUOTE]

well i plan to do a final fantasy 2 type, magic, sword, etc attack system.  not really sure how it will all work yet.  play final fantasy 2, something like that:)

---

### Post by bored2k on 2005-06-09
[QUOTE=jdodson]well i plan to do a final fantasy 2 type, magic, sword, etc attack system.  not really sure how it will all work yet.  play final fantasy 2, something like that:)[/QUOTE]
 I remember FF-2 . It's my *numero 3*prefered FF game (after X and IX). That's great.

... You had to mention FF2 :/. Now I'll want to change my character class at will every 20 minutes :/ .

---

### Post by ubuntu_demon on 2005-06-09
funny game :)

---

### Post by christooss on 2005-06-09
sorry to ask how can I start this game?

---

### Post by Leif on 2005-06-09
Is it just me, or are a number of the areas not done yet ? When I try to get into the 'village' surrounded by a lake, and some other places, all i get is an empty map, and on the console "IndexError: list index out of range". Other than that, very nice. Couple of spelling errors, and it might also be nice to have the dialog autoscroll.

---

### Post by christooss on 2005-06-09
Nice game but...

How can I end this game. I have came in to bridgemans village and gave rabbit a letter and he gave me something blue. Now what?

Game's got a lot of potentials

---

### Post by skoal on 2005-06-09
This game is great.  I give you a **** happypenguin rating (out of 5).  Not bad at all.  However, I have a few requests if you want to make it to a 5. Can you turn this into an OpenGL First Person Shooter and drop some weapons along the way, like a rocket launcher maybe. I met some fairy in the woods and he started some beef with me about waking him from his precious little nap. He told me to go jack him some stupid flute which I gathered was some sort of lost family heirloom.  I just wanted to stick my Rocket Launcher in his face and say, "Eat this!".  I dunno, maybe I've been playing too much Doom3 lately.  Great game though...

\\//_

---

### Post by jdodson on 2005-06-09
[QUOTE=Leif]Is it just me, or are a number of the areas not done yet ? When I try to get into the 'village' surrounded by a lake, and some other places, all i get is an empty map, and on the console "IndexError: list index out of range". Other than that, very nice. Couple of spelling errors, and it might also be nice to have the dialog autoscroll.[/QUOTE]


yeah it is an early beta.  i plan to finish a quest system so the game can be beaten.  and then implement a fighting based system, etc.

and yes, its not quite finished yet.

---

### Post by jdodson on 2005-06-09
[QUOTE=skoal]This game is great.  I give you a **** happypenguin rating (out of 5).  Not bad at all.  However, I have a few requests if you want to make it to a 5. Can you turn this into an OpenGL First Person Shooter and drop some weapons along the way, like a rocket launcher maybe. I met some fairy in the woods and he started some beef with me about waking him from his precious little nap. He told me to go jack him some stupid flute which I gathered was some sort of lost family heirloom.  I just wanted to stick my Rocket Launcher in his face and say, "Eat this!".  I dunno, maybe I've been playing too much Doom3 lately.  Great game though...

\\//_[/QUOTE]

HA!  perhaps i will add those features in a later dot release.

---

### Post by christooss on 2005-06-09
so can I end quest or not?

---

### Post by jdodson on 2005-06-09
[QUOTE=christooss]so can I end quest or not?[/QUOTE]

end quest as in "cant go any further" then yes.  

end quest as "there is a formal ending to the game" then no.

---

### Post by jdodson on 2006-03-15
I have started extending OpenFantasy if anyone is interested.  The new code tree is here:

[http://jdodson.org/~jdodson/files/openFantasy/](http://jdodson.org/~jdodson/files/openFantasy/)

The project site is here:

[http://jdodson.org/index.php/openfantasy/](http://jdodson.org/index.php/openfantasy/)

Sofar, no new features, but I am massively cleaning up the code(it really needs it).

If anyone is interested in getting in on the action via testing, coding or whatever, drop me a line at my website jdodson.org.

Rock it till you die.

---

