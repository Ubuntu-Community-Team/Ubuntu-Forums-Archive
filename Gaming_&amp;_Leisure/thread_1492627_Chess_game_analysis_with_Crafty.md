---
title: "Chess game analysis with Crafty"
date: 2010-05-24
forum: Gaming &amp; Leisure
---

### Post by OldAlgis on 2010-05-24
Hi there! I hope somebody can and will help me - I want to find out how to set up a chess engine, preferably Crafty to analyse chess games.  I would expect that there are mailing lists dedicated to Crafty or perhaps forums?

Any information would help.

---

### Post by kewlbns69 on 2010-06-11
I just finished a custom crafty setup complete with table bases and all the extra bells and whistles that make crafty a real serious opponent. Here's how i did it

1. Download and install Crafty ```
sudo apt-get install crafty
```2. Download multi part enormous.zip as well as start.pgn and startc.pgn from
  [ ftp://ftp.cis.uab.edu/pub/hyatt/pgn/]("ftp://ftp.cis.uab.edu/pub/hyatt/pgn/") and extract enormous.zip (all 3 files need to be in the same directory)

3. Open terminal cd /directory/of/pgn/files and crafty to run

4. Once crafty is running you should see White(1):
    From here type book create enormous.pgn 60
    Type books create start.pgn 60
    Type bookc create startc.pgn

5(Optional).  Now that you have the opening books created it's time to get the table bases. Go [ftp://ftp.cis.uab.edu/pub/hyatt/TB/](ftp://ftp.cis.uab.edu/pub/hyatt/TB/) and download everything in the 3-4-5 and tbs directory (this is about 7GB worth of files and isn't necesary unless you're looking to do some serious analysis or you like to torture yourself with brutal chess engine settings).

6a(eboard setup) 
 NOTE: if you wish to use eboard to play against crafty all book files must be located in ~/.eboard and all table base files must be located in ~/.eboard/craftylog
 
 1) Download and install eboard ```
apt-get install eboard
``` 2) Open eboard and start a new game Peer -> Play against Engine -> crafty
 3) After eboard creates an engine bookmark we want to modify this slightly
     Peer -> Engine Bookmarks -> Edit Engine Bookmarks (assuming you have one)
     under the "Directory" option type /home/user/.eboard/craftylog 
 4) Edit the command box to say crafty smpmt=2* hash=512M* hashp=128M* ponder=on learn=7 bookpath=/home/gimpdaddy1979/.eboard egtb=on tbpath=/home/user/.eboard/craftylog this will setup eboard to run crafty with extreme settings.
Good Luck! :)

*Note: smpmt=2 assumes a dual core system. The hash and hashp options control how much memory crafty should use for it's analysis. You can set these at just about anything, but if you exceed your systems available memory limits the highest possibles are set automatically by the engine. So feel free to experiment to find your systems limits the console output on eboard will tell you what values crafty actually used and you can later edit the command 

6b(scid setup)     
 1) ```
sudo apt-get install scid
``` 2) Open scid and open the analysys engine window....Tools -> Analysis Engine
 3) Cick new and enter the following...
Name: Crafty V.23.1(or whatever version you're using)
command: crafty
parameters: smpmt=2 hash=512M hashp=128M ponder=on learn=7 bookpath=/home/user/.eboard egtb=on tbpath=/home/user/.eboard/craftylog
Directory /home/user/.eboard
4) Uncheck UCI because crafty is a winboard engine and leaving this checked will cause errors.
5) Double click the new entry created for crafty to load the engine and you're done! Crafty will now analyze your games at it's full strength


P.S I hope this helps people who want to play some extreme chess on linux without having to buy some expensive comercial product. Also if anyone knows how to run crafty with those options through Xboard with ICS i'd be much appreciative for the help
-peace

---

### Post by OldAlgis on 2010-06-11
> **kewlbns69 said:**
> I just finished a custom crafty setup complete with table bases and all the extra bells and whistles that make crafty a real serious opponent. Here's how i did it

1. Download and install Crafty ```
sudo apt-get install crafty
```2. Download multi part enormous.zip as well as start.pgn and startc.pgn from
  [ ftp://ftp.cis.uab.edu/pub/hyatt/pgn/]("ftp://ftp.cis.uab.edu/pub/hyatt/pgn/") and extract enormous.zip (all 3 files need to be in the same directory)
(snipp...) 
-peace

Thank you for a detailed reply - greatly appreciated.  I will work through it and, no doubt, will be back with questions. 

Your contribution is a very valuable help!  Actually, I have installed Crafty and eboard (and Xboard, for that matter) from the ubuntu repos as deb packages.

What I have failed to do is to get Crafty to analyse my games.  I confess that I prefer to play chess with human oponents on FICS, the Free Internet Chess Server
[http://www.freechess.org](http://www.freechess.org). 
My aim is to get Crafty to analyse the games and show bad errors as  there are plenty of those, yet they are not so easy to spot.

I hope to learn from your experience and eventually get Crafty with eboard to do what I would like it to do.

Will be in touch and thank you again!

---

### Post by OldAlgis on 2010-06-12
> **kewlbns69 said:**
> 
(big snip...)
4. Once crafty is running you should see White(1):
    From here type book create enormous.pgn 60
    Type books create start.pgn 60
    Type bookc create startc.pgn
(another big snip...)


Downloaded enormous.zip and unzipped it. A large collection of games, nearly one and a half million...  (1 496 327 games!)

Created book.bin, books.bin, but failed to create bookc.bin.  Assumed that there was a typo in your instructions - in bookc the depth 60 was missing, so typed from crafty's prompt
```
 bookc create startc.pgn 60 
```
That did create the bookc.bin.

Started experimenting with the eboard. This enables to set time limits with increments ("Fisher times"), viz. 2 min at start, 12 sec increment per move. "eboard" is quite nice, but how to get it and crafty to analyse a game, downloaded from FICS in their pgn format?

Looks very interesting. Thanks again!

---

### Post by kewlbns69 on 2010-06-12
> **OldAlgis said:**
> "eboard" is quite nice, but how to get it and crafty to analyse a game, downloaded from FICS in their pgn format?


eboard is strictly a frontend to play against crafty and other xboard/winboard engines. There's a built in ICS client but that's it. I use scid for analysis it allows me to load a game from pgn start the crafty engine and it just goes. Nice simple output that doesn't confuse me all that much. once you get that setup you'll have a fairly sync'd system you can use eboard to play and scid to analyze and crafty "thinks" just as hard in both apps.

---

### Post by eec on 2010-12-06
how do we use the endtables downloaded from hyatt's webpage? what should i do?

---

### Post by kewlbns69 on 2011-02-15
> **eec said:**
> how do we use the endtables downloaded from hyatt's webpage? what should i do?

it's in the command you have to customize when u tell eboard to run crafty

"egtb=on" does it...u can check this in the console it will tell you it found tables or whatever i have to redo this on my machine so i'll post back w/ the output which should end up being roughly the same as your system as long as you have a dual core w/ 2Gb memory otherwise i think the numbers might be different since crafty adjusts if you set things too high

---

### Post by bogdarnet on 2011-05-24
Do any of these programs (eboard, scid, Xboard, pychess, etc.) allow you to give them a pgn file of games and automatically blundercheck or annotate using crafty or stockfish or another engine?  I can do this on my other machine (Windows-encumbered) with Fritz... just wondering if there's an existing solution on Ubuntu.  (Don't really care for wine... I haven't had much luck with it so far.)

---

### Post by bogdarnet on 2011-05-26
Okay, think I found an answer in SCID... Once the game and the engine are loaded, there's an annotation button at the bottom of the engine window.  Looks like it can be set to go through multiple games there as well.

---

### Post by croak2012 on 2011-09-30
6a(eboard setup) 
 NOTE: if you wish to use eboard to play against crafty all book files  must be located in ~/.eboard and all table base files must be located in  ~/.eboard/craftylog

Hi, 

I seem to get stuck at this stage because I'm a bit of a newbie to ubuntu and don't understand directory structure that well yet... anyway  my exe file is located in /usr/games and folder located in /usr/share/games/eboard.
I copied and pasted book files to the /usr/share/games/eboard directory so just wondering if it will still work if i use this directory instead? thanks in advance
Ian

---

### Post by donkyhotay on 2011-09-30
The "~" means your home folder so assuming your ubuntuforums username is the same as your computer username then 
~/.eboard 
is the same as 
/home/croak2012/.eboard
Be aware that a folder with a . in front of it (like the .eboard folder you are using) is considered a hidden folder and won't show up automatically in nautilus, you'll need to go into settings and "show hidden files" in order to see it. If it's telling you to put things in the a folder in your home directory then putting things in another folder (like the /usr/share/games/eboard you were trying) won't work.


//edit: as a general rule unless you *really* know what you're doing you shouldn't manually put files into any other folders besides your home folder. Thats what the package manager is for to take care of all that. Even though it's where "apps" are stored and seems like it would be the equivalent of messing around with the windows program files folder because of the way linux stores information there isn't really a difference between an "app" and the OS itself and messing around with other folders is more like messing around with the windows/system folder. Thats why lots of programs will tell you to save/store files (even plugin type things) into a folder in your home folder (like this did).

---

