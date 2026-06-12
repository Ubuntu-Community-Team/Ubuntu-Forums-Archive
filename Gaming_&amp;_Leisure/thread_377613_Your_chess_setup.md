---
title: "Your chess setup?"
date: 2007-03-06
forum: Gaming &amp; Leisure
---

### Post by Somenoob on 2007-03-06
I use Glchess(from Gnome games) for the GUI 
And GNUchess for the engine

What about you?

---

### Post by teaker1s on 2007-03-06
3dchess:popcorn:

---

### Post by UbuWu on 2007-03-06
[Pychess]("http://pychess.googlepages.com/home") :guitar:

---

### Post by Somenoob on 2007-03-06
> **UbuWu said:**
> [Pychess]("http://pychess.googlepages.com/home") :guitar:

I tried it, I encountered a dependecy problem. The error message didin't state what it was.

---

### Post by DoktorSeven on 2007-03-06
Eboard+GNUchess (or occasionally Crafty)

---

### Post by Dr. Cox on 2007-03-20
just manually installed eboard as the version coming in the repos has some flaws in the menu display.
got my hands on the crafty sourcecode... any idea how to compile it and after that, make eboard recognize it?

thanks for the help.

---

### Post by DoktorSeven on 2007-03-20
Crafty is in the Multiverse repos if you don't want to compile it; FTP site with the code seems slow or down so I can't check, but if you want to compile it I"m sure it's the standard extract, **./configure, make, sudo make install** installation procedure (you'll need to apt-get install build-essential).

---

### Post by hikaricore on 2007-03-20
I use GLchess as well, but I'm still looking for a quake port that will allow me to run [Quess]("http://www.atomicgamer.com/newsFeed.php?id=36125"). :(

---

### Post by mig10k on 2007-04-01
> **DoktorSeven said:**
> Crafty is in the Multiverse repos if you don't want to compile it; FTP site with the code seems slow or down so I can't check, but if you want to compile it I"m sure it's the standard extract, **./configure, make, sudo make install** installation procedure (you'll need to apt-get install build-essential).

i can't find crafty in multiverse (ubuntu 6.10).

---

### Post by buntu_hugenewbie11 on 2007-04-05
I can't seem to get pychess to run at all. I start the program and it never finishes loading any ideas?
I tried the fruity engine and it never seems to work. Same with hoichess.
Recently I tried brutalchess but the engine is easy to beat making it dull.
Does anyone know how to link up to the yahoo chess servers from fiesty terminal or kde? 
What other engines are decent?

---

### Post by kno712 on 2007-04-07
I'm afraid that, in my honest opinion, the best chess programs are for the Win$ platform; you can use wine and arena ([www.playwitharena.com);](www.playwitharena.com);) it is free, you can use UCI or winboard engines and you can download a good opening book as well; I use babaschess as well ([www.babaschess.net);](www.babaschess.net);) it is very good for playing chess in FICS. This last one I have installed in linux and it rus fine son far.

pychess will be a good program but still is a early development stage; I've heard about csboard, but I haven't tried it myself.

---

### Post by buntu_hugenewbie11 on 2007-04-08
With 3dchess I get the following error:
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings

Anyone know what I need to get and install?
I'm using fiesty.

---

### Post by jmelton on 2007-04-09
Rybka is by far the best chess engine in the world.  I haven't tried running it in Linux yet, but it should run fine under most chess GUIs (any that are UCI) that run in Linux.

---

### Post by buntu_hugenewbie11 on 2007-04-09
You need wine for Rybka though is it worth it?

---

### Post by DoktorSeven on 2007-04-09
> **buntu_hugenewbie11 said:**
> With 3dchess I get the following error:
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings

Anyone know what I need to get and install?
I'm using fiesty.

Not sure if the packages are the same as in Debian but you need something like python-opengl and python-gtkglext1.  Search using synaptic, you should be able to find packages with these or similar names.

---

### Post by buntu_hugenewbie11 on 2007-04-09
Yeah I tried those: the GLgext package doesn't seem to exist.
Could it be something with my nvidia card?

---

### Post by DoktorSeven on 2007-04-09
Well, you will likely need a working 3d environment but if the game actually tells you that you need those two things, then it wasn't able to find them and you do need to install them.

Did you try enabling universe/multiverse repos (search for info)?  Maybe it's in there.  

Also, see this: [https://answers.launchpad.net/ubuntu/+ticket/4469](https://answers.launchpad.net/ubuntu/+ticket/4469) ; are you running 64 bit?  Might be out of luck according to that.

---

### Post by buntu_hugenewbie11 on 2007-04-09
Thanks- I am running a 64bit --> guess that makes sense. Hope they get it going soon. :-(

---

### Post by nabla on 2007-04-22
In Ubuntu just eboard for FICS, Crafty as engine but I don't use it much. I keep a windows partition for chessbase, fritz, etc.

---

### Post by Grigorius on 2007-06-25
> **kno712 said:**
> I'm afraid that, in my honest opinion, the best chess programs are for the Win$ platform; you can use wine and arena ([www.playwitharena.com);](www.playwitharena.com);) it is free, you can use UCI or winboard engines and you can download a good opening book as well; I use babaschess as well ([www.babaschess.net);](www.babaschess.net);) it is very good for playing chess in FICS. This last one I have installed in linux and it rus fine son far.

pychess will be a good program but still is a early development stage; I've heard about csboard, but I haven't tried it myself.

I agree the best chess interface is the Fritz interface and I think basically all the ChessBase software is a step or two above the competition. In windows (xp) I use Fritz 10 (the interface + engine, I also have Rybka and Hiarcs ...) 

I also tried to experiment a bit with FICS and the software available for linux ... SCID for the database, I use Crafty, GNUchess and Fruit in combination with Gnomechess - witch comes with Ubuntu, I use Toga2 in combination with Arena - and this works well with wine, and to play on the internet I tried Jing but I didn't like it I didn't like X-board either so I settled with Varese (Varese is only meant to work with the FICS server: [http://varese.home.att.net/](http://varese.home.att.net/) ) ... however I still boot win to play chess because there is no good substitute for Chessbase + I have many training DVD-s that won't play in linux (I was able to install Chessbasereader but it hangs when I try to open a DVD ... and as far as I'm aware there is no solution - I heard that Chessbase or to be more precise Fritz 8 works and this might be a good try but I already own Fritz 10 so ... for me it is better to go to win to play chess ... in fact the thing the bothers me most is that there is no software for linux that has a multitasking ability (when talking about chess) and I wasn't able to find a way to analyse my games using linux software ... the only way I know how to do that is to look move by move with an engine running ... but that takes too much time that I don't have ... there is no analysis option like there is in fritz ...

 P.S. If there is any programmer or something like that that knows if something is being developed I would love to know about it (something like playchess I mean) or even in general (for chess) ...

---

### Post by Golyadkin on 2007-06-25
GNUChess

---

### Post by Contrast on 2007-06-25
I use pouetChess when I'm playing by myself and/or when I have a friend over. Then I have Knights for online multiplayer.

---

### Post by efmunu on 2007-06-30
Pychess. Especially version 0.7 in the svn looks very promising (FICS support).

---

### Post by Myrizio on 2007-07-23
Dear Grigorius, i'm trying to get a copy of the Varese interface but its site is permanently down.
If you still have a copy of it, could you be so kind to let me retrieve somewhere? I found it in no place. Thanks!
Ah, btw, i need it because i would like to compare it to the chess interface that i am writing my friend Paolo:
[http://tagua.ath.cx/trac/](http://tagua.ath.cx/trac/)

---

### Post by Grigorius on 2007-07-30
I do have it it is 4.9MB big ... I culd send it to you I just made a .rar file ... so if you'll leave me an email ... or some other way to send the file to you I will ...

---

### Post by Myrizio on 2007-07-30
I'd be very happy if you could do so!
just send it to the address giorgio.monge [AT] gmail.com
Thanks a lot!

---

### Post by olejorgen on 2007-08-07
I'm also a little dissapointed over the chess offering in linux.

I think **eboard** is good though.

---

### Post by hikaricore on 2007-08-07
> **olejorgen said:**
> I'm also a little dissapointed over the chess offering in linux.

I think **eboard** is good though.

There are some really good chess titles, I doubt you've tried them all.

What exactly disappoints you?

---

### Post by olejorgen on 2007-08-07
gnome-chess: I really like the default theme, and overall feel.
- Can't undo
- No network play (I understand this might be out of scope)
- 3D view *really* crappy
- Few options (no suprise here ^^) eg. autosave all games
- Conflicts with gnuchess (wtf?) [I think this is a bug]
- Sometimes the pieces move *very* slowly

brutalchess: Pretty
- No engine support
- Crappy built-in AI
- Can't save
- Can't zoom (minor)
- No network
- No undo (?)
- General lack of options / features

pouetChess: Pretty
- General lack of options / features (Similar to brutalchess)

pyChess: Similar to gnome-chess, some nice features as hint mode
- No undo
- No network
- Few options (eg. theme / autosave)

xboard:
- gtk1 (or somthing) -> ugly
- Cant resize window? (Haven't used it much because of this. I can't see the whole board)

eboard: 
- Can't play two player on same machine (only with 2 clients running)
- Impossible to undo during 2 player game
- Could be more stable (but I guess I can't complain)

Don't get me wrong, there are plenty of good titles, it just seems all are missing something. As linux is a kinda geeky OS, I'd expect something even better.

Disclaimer: I haven't tried all of the above titles extensively

PS: And don't give me this "oh, why do you want to undo in a chess game, you're no allowed to do that!" 

Reponse: You can make a mistake, and don't want to start all over because the current game is interesting. Besides, I think a computer game should allow you to do everything a normal board game can do

---

### Post by hikaricore on 2007-08-07
I'm actually quite amazed at the effort you've put into finding the perfect chess game.
Sorry to say I underestimated you.  >.<

I've been very happy myself with Dreamchess: [http://www.dreamchess.org/screenshots.html](http://www.dreamchess.org/screenshots.html)
Which I believe is in the repos.

I doubt it has all the features you want but it sure is pretty.  ^_^

---

### Post by olejorgen on 2007-08-07
Well, it's really not that much. As I said, I've not done extremely extensive testing :)

I haven't tried dreamchess, but at least it seems like it has undo ^^

It's not in the repos, but will be in gutsy, I think

---

### Post by seanX on 2007-08-12
Thanks for the info on dreamchess.

I got it to install after doing:

    sudo apt-get install libsdl-image*
    ./configure
    make
    sudo make install

Then, I ran it with the:

    dreamchess

command from the terminal, or you could add it to your application launch
menu.  It's in /usr/local/bin by default.

Basically, this is the closest I've got so far to the pre-loaded Windows Vista 
Chess game, which is good by most measures.  Dream chess has 
the retract/undo feature that most of you have been looking for.

I don't know if it has sound though.  I can't hear anything.
Thanks.

---

### Post by Fingolfin on 2007-09-19
> **olejorgen said:**
> 
xboard:
- gtk1 (or somthing) -> ugly
- Cant resize window? (Haven't used it much because of this. I can't see the whole board)


Xboard has the most configurable setup than any other GUI for chess engines.
It is a command line driven program with myriad options, type
%man xboard
in the console and check out the -boardSize (or -size) switch.

---

### Post by nonewmsgs on 2007-09-19
a lot of fics-ers in the house :)
i personally like jin.  it is my favorite native chess proggy.  babas under wine is something ugly even after the smiley disabling bug thing.  the only things lacking in jin are 1: chat tabbed window, and 2: move history even if you weren't observing.  
i <3 the skull pieces too.  it's the first non-staunton set i liked.


im ahorse from fics

---

### Post by nonewmsgs on 2007-09-19
> **seanX said:**
> Thanks for the info on dreamchess.

I got it to install after doing:

    sudo apt-get install libsdl-image*
    ./configure
    make
    sudo make install

Then, I ran it with the:

    dreamchess

command from the terminal, or you could add it to your application launch
menu.  It's in /usr/local/bin by default.

Basically, this is the closest I've got so far to the pre-loaded Windows Vista 
Chess game, which is good by most measures.  Dream chess has 
the retract/undo feature that most of you have been looking for.

I don't know if it has sound though.  I can't hear anything.
Thanks.

i did the apt-get but the ./ doesnt work.  what directory do i have to cd first??

---

### Post by andrew.46 on 2007-09-19
Hi,

> **buntu_hugenewbie11 said:**
> With 3dchess I get the following error:
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings

Anyone know what I need to get and install?
I'm using fiesty.

I don't run this program but try searching the cache with something similar to this:

```
 apt-cache search opengl | grep python && apt-cache search gtkglext

```

There was nothing for:

```
apt-cache search gtkglext | grep python
```

but plenty without. Have a play with the search and you will eventually stumble across the right files :-)

             Andrew

---

### Post by nonewmsgs on 2007-09-20
the one thing i have to wonder about that really annoys me is when it shows all available moves.  it's in gnuchess and 3d.  :|

---

### Post by cinematography on 2007-10-12
```
sudo apt-get install eboard eboard-extras-pack1 crafty crafty-books-medtosmall gnuchess gnuchess-book
```

eboard is a great, simple, to the point chess board. It doesn't seem as buggy or clumsy as pychess and xboard seem on my system. And crafty is a brilliant engine. I can barely beat that thing.

---

### Post by nab on 2007-10-13
Hi,

I wanted to use glchess + fruit.

But I can't get glchess to see the fruit engine (from universe)

How do I activate the AI?

TIA,
Niko

---

### Post by cinematography on 2007-10-15
> **nab said:**
> Hi,

I wanted to use glchess + fruit.

But I can't get glchess to see the fruit engine (from universe)

How do I activate the AI?

TIA,
Niko
I'm having the same problem. 

*correction on pychess* 
Its actually a lot better than I originally thought. Its still a little buggy on my computer, but its very clean and straight forward.

*update*
Arena, a Windows gui, runs wonderfully with wine, and can easily install and use the fruit engine.

---

### Post by nab on 2007-10-20
just a short update:

switched from glchess to knights and it works :-)

Well I know it's KDE, so my system got really bloated ;-(

have a nice weekend,
Niko

Edit: Upgrades this weekend to Gutsy and ... glchess works with fruit :-)

---

### Post by Lobais on 2007-11-06
Did you check out the latest beta of PyChess 0.8?
It has now got FICS and Undo functionalities.

---

### Post by gh23l on 2007-11-18
I haven't seen anyone mention Jose-Chess. I guess it's the best chess-gui for linux. It can be found at: [http://jose-chess.sourceforge.net/](http://jose-chess.sourceforge.net/)

To give you an impression, how beutiful it can look if you've downloaded the additional textures as well. here's a screenshot: [[IMG]http://img123.imageshack.us/img123/2679/bildschirmfotojs1.th.png[/IMG]](http://img123.imageshack.us/my.php?image=bildschirmfotojs1.png)

---

### Post by mivo on 2008-01-26
I usually play with the already mentioned Pychess, and recently bought a copy of [Shredder 11 for Linux]("http://www.shredderchess.com/linux.html"). It isn't free, but you can freely set the ELO value of the computer opponent (starting at 850), which none of the free alternatives offer, and there is a coaching mode. There is a 30-days trial version available, too, and Shredder works fine in Ubuntu (the install script didn't work, however). A graphically nifty, and free, chess game is [DreamChess]("http://www.getdeb.net/app/DreamChess"), which looks certainly better than the 3D chess interface that comes with Ubuntu.  :) All three are actively maintained.

---

### Post by Lobais on 2008-01-26
> **mivo said:**
> I usually play with the already mentioned Pychess, and recently bought a copy of [Shredder 11 for Linux]("http://www.shredderchess.com/linux.html"). It isn't free, but you can freely set the ELO value of the computer opponent (starting at 850), which none of the free alternatives offer, and there is a coaching mode.
Coaching mode sounds cool, but does it work? I just downloaded the demo, and the coatch only talked to me if I directly was loosing a piece.
Is it better in the registred version?

---

### Post by Joor on 2008-02-12
I just installed pychess with the add program thing. But it was only veriosn 0.6. 
0.8 was released so I press download and then it goes into install mode in the "terminal" but after it was done I can no longer play chess  why ?

---

### Post by mivo on 2008-02-13
> **Joor said:**
> 0.8 was released so I press download and then it goes into install mode in the "terminal" but after it was done I can no longer play chess  why ?

Did you download the .deb file from Pychess' home page? If so, it doesn't seem to work so well with Ubuntu. You can find a working .deb of the (almost) latest  version at GetDeb.net: [http://www.getdeb.net/app/PyChess]("http://www.getdeb.net/app/PyChess")

---

### Post by Joor on 2008-02-13
Got the 0.8 beta3 installed now :)
cant get the beta4 to work tho ..

---

### Post by drobvice on 2008-02-17
There is a .deb packaged for Hardy [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fp%2Fpychess%2Fpychess_0.8~beta4-1_all.deb&md5sum=8b88d043b37647349a55ca9f3001ea57&arch=all&type=main").  It works on Gutsy.

---

### Post by mivo on 2008-02-19
> **drobvice said:**
> There is a .deb packaged for Hardy [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fp%2Fpychess%2Fpychess_0.8~beta4-1_all.deb&md5sum=8b88d043b37647349a55ca9f3001ea57&arch=all&type=main").  It works on Gutsy.

It doesn't work for me and behaves like the Debian file on the Pychess home page:

```

Traceback (most recent call last):
  File "/usr/games/pychess", line 41, in <module>
    pychess.Main.run(sys.argv[1:])
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 468, in run
    PyChess(args)
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 400, in __init__
    self.initGlade()
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 433, in initGlade
    window["menubar1"].drag_dest_set(flags, dnd_list, gtk.gdk.ACTION_COPY)
TypeError: list items should be of form (string,int,int)

```

---

### Post by drobvice on 2008-02-19
Hmm.  I'm on a fresh Gutsy install with all updates.  Interesting it doesn't work.  To be honest I wasn't sure if it would install but it works fine for me.  Sorry that doesn't help.

---

### Post by Lobais on 2008-02-27
> **mivo said:**
> It doesn't work for me and behaves like the Debian file on the Pychess home page:

```

Traceback (most recent call last):
  File "/usr/games/pychess", line 41, in <module>
    pychess.Main.run(sys.argv[1:])
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 468, in run
    PyChess(args)
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 400, in __init__
    self.initGlade()
  File "/usr/lib/python2.5/site-packages/pychess/Main.py", line 433, in initGlade
    window["menubar1"].drag_dest_set(flags, dnd_list, gtk.gdk.ACTION_COPY)
TypeError: list items should be of form (string,int,int)

```

This bug has been fixed in the 0.8 final version.

---

### Post by skyttan on 2008-03-22
I dualboot with Windows XP only because of my chess programs: Chess Assistant 9.0, ChessBase 9, Fritz 11, training CDs from ChessBase and other Convecta Ltd. software. In my Ubuntu 7.04 I have PyChess and Crafty (only engine strong enought) alongside BlitzIn trough Wine installed when I want to play some games. I tried Knights but it does the same as other mentioned. 
   Linux open-source/free chess-apps are, and will always be, way behind Windows commercial software for serious chess players like me because of many reasons.

This is why:
 **1)** it needs a huge effort by the constantly working devolopers to bring an uppdated chess program, i.e.
    - an chessbase, searchable by players, posions, themes and so on with all the newest games played up-to-date (game providing service like [http://www.chesscenter.com/twic/twic.html]("http://www.chesscenter.com/twic/twic.html") but done more automaticly by the software) 
    - an opening book, with all the new lines and eventually how to respond to them, found out with engine (online book: [http://chessok.com/?page_id=98]("http://chessok.com/?page_id=98"))
 **2)** a strong engine capable of analysing every damn thing, however and whenever you want, posision or whole game with annotions
 **3)** apps to play on the internet (ICC and PlayChess), using all of its feutures like studying games afterwards, autosaving them and so on
 **4)** and eventually most of all, an easy-to-use GUI (the program itself) to give you full control over all the feutures, makeing them work nicely together

And as I tested this Linux apps, all this mess of finding, getting, installing and finally tweaking them to get them work is just to much mess to go throught for chess players. My only hope today is combining online services with [Deep Shredder 11 Linux]("http://www.shredderchess.com/chess-program/deep-shredder-11-linux.html"), of wich I am not hopeful for, 'couse I did not even get the [demo]("http://www.shredderchess.com/chess-download/free-demo-download/download-shredder-classic-3-linux.html") working (btw thankful for help on this point).

I apoligise for my spelling, I know it is not very good but hopefully you will understand what I am trying to say.

Your sincerely,
skyttan

---

### Post by Lobais on 2008-03-28
You are right that there is really a lack of a decent Linux chess client (which I guess is also why so many people are trying to create one). If you have good ideas, you should certainly try and tell the devs about it. Perhaps you can even help help things out.

---

### Post by PC_load_letter on 2008-04-03
The real question is why doesn't a company like ChessBase have a Linux version of Fritz? I'd still buy it, it doesn't have to be free :D

---

### Post by PC_load_letter on 2008-04-03
...for the Chess experts here, how good is this one:
[http://www.shredderchess.com/linux.html](http://www.shredderchess.com/linux.html)

---

### Post by PC_load_letter on 2008-04-03
> **PC_load_letter said:**
> The real question is why doesn't a company like ChessBase have a Linux version of Fritz? I'd still buy it, it doesn't have to be free :D

Found the answer at their official website: 
[B]=============================================
No, sorry. There's an economic reason for this: it takes a pile of time and effort (i.e. money) to develop software for a particular OS and if it's not going to sell enough copies to cover the development costs, it's not going to get made. And I'm not just talking through my hat here; we had years of requests for a Mac version of ChessBase and, after one was released, the sales were (shall we say) somewhat less than mediocre and loads of money got lost on that particular venture.

I'm in no way busting on Linux here, but it's nowhere near as popular as Windows. If the day comes when the split between them gets closer to 50/50, I'm sure that a Linux version will be seriously considered. -- SL 
===============================================[/B]

50/50?!! So it might be a while before we see Tux playing Fritz.

---

### Post by geneven on 2008-05-15
For 1-minute (on FICS), Jin is the only thing I've found workable. I can't try Varese since it has disappeared. Xboard just doesn't have the features it needs, for really fast chess -- the clock needs to be very visible, etc. I've watched Knights over the years, and it has always seemed woefully inadequate to me.

Of course, Windows and Blitzen seemed essential to me on ICC, but I haven't been there for quite awhile.

---

### Post by skyttan on 2008-06-08
> **PC_load_letter said:**
> ...for the Chess experts here, how good is this one:
[http://www.shredderchess.com/linux.html](http://www.shredderchess.com/linux.html)

I tried the demo, but I couldn't get it up. Even asked my brother, he couldn't either get it up working. I did not buy the program because of this.

But I didn't mention in my last post how I study chess in Ubuntu. I use internet-based solutions for that. Here are some links:
**Opening bases**
 - [http://www.shredderchess.com/online-chess/online-databases/opening-database.html](http://www.shredderchess.com/online-chess/online-databases/opening-database.html)
 - [http://chessok.com/?page_id=98](http://chessok.com/?page_id=98)
**Games database**
 - [http://chesslive.de/](http://chesslive.de/)
 - [http://www.chessgames.com/](http://www.chessgames.com/)
**Play on the internet (through browser)**
 - [http://www.instantchess.com/](http://www.instantchess.com/)
 - [http://gameknot.com/](http://gameknot.com/)
**Chess Puzzles**
 - [http://homepage.ntlworld.com/adam.bozon/ChessPuzzles.htm](http://homepage.ntlworld.com/adam.bozon/ChessPuzzles.htm)

..and at last, for you who wants to improve your game:
 - [http://chesstempo.com/](http://chesstempo.com/)

If you know about more of this on-line things, please let us know!

---

### Post by mivo on 2008-06-08
As for Shredder: I didn't try the demo, but I did buy the software. The included installation script really didn't work for me in Ubuntu. But provided that Java is installed, it is not necessary. You can just launch it with a simple command:

java -jar LinShredder.jar

Just make a desktop launcher and/or add it to the appropriate menu. This may work with the demo as well.

---

### Post by linuxisfree on 2008-06-08
I've got pouetChess.

---

### Post by kkady32 on 2008-08-13
how start xboard with toga2 and fruit?

---

### Post by cristo-father on 2008-08-14
[http://www.getdeb.net/app/DreamChess](http://www.getdeb.net/app/DreamChess)

---

### Post by pwc on 2008-08-28
Alright you linux lovers no more crying about chess not being available for linux. I have what I consider an excellent setup with Ubuntu 8.04 both for playing and studying chess. I have databases, engines, clients for playing on internet, and software for playing and studying chess.
 Here's the programs I use: 

Databases: 

Scid - used for opening collected databases  and  studying games,
          also has built in engines useful for studying. It's free and 
          available with Synaptic. Has more features than I could 
          possibly list here.
Bookup - Unique software for studying openings and is not free
         however can be easily  setup in Ubuntu. I installed 
          VirtualBox with Synaptic and 
         loaded my old windows XP. Now with just one click I'm in XP and 
         using Bookup! I can open any of my linux chess programs on 
          desktop and work right along with Bookup. 

Chess clients for internet:

There are several, I use Eboard, think it's great. Use it on FICS.  Eboard is a little techy to set up but the "how tos" are available and just find them and  follow to a tee. You can also use it for playing games against various engines, I installed Crafty, GNU, and Sjeng and all beat me with 
ease since you can't set the level of play. Eboard available with Synaptic and of coarse free.

Chess playing software: 

  There are a few free linux programs available and I don't like any of them. I use Shredder for Linux which is a class act. You can set the levels and play or use it for study. It does cost but not much, I paid about $25 it think.

  I don't think I'm missing anything using linux as far as chess goes and it's mostly free. Could be totally free but a little money makes it nicer.

---

### Post by cardinals_fan on 2008-08-28
The Shredder web version is actually quite nice on the hard setting.

---

### Post by kkady32 on 2008-09-10
with fruit work now:)now i try to start with toga2

---

### Post by anjilslaire on 2008-09-11
+1 for dreamchess

---

### Post by ubuntp on 2008-09-11
pyChess. Also it maybe worthwile to recompile open source engines like Crafty with ICC for some speed [benefit]("http://macles.blogspot.com/2008/09/intel-cc-compiler-gcc-and-intel-atom.html").

---

### Post by Mr. Mullrway on 2008-09-11
I will have to try out GNUChess.  I have been using Yahoo Chess for awhile now but I am tired of spending half an hour just to find a game.  Not to mention you don't know if your playing against a human or a bot half the time.

---

### Post by japhyr on 2009-01-16
I've just started using scid, and it's good to have all my fics games in one place.  I would like to be able to play a position from one of my games out against the computer.  Is there any way to do that using scid, or to open a position from an scid game in another chess program?

---

### Post by InspiredIndividual on 2009-01-18
> **japhyr said:**
> I've just started using scid, and it's good to have all my fics games in one place.  I would like to be able to play a position from one of my games out against the computer.  Is there any way to do that using scid, or to open a position from an scid game in another chess program?

Both are possible. Importing a position in another chess program is quite easy. You can just export the current position in FEN notation by Edit > Copy Position. Another possibility is to export a PGN file using Tools > Export Current Game > Export Game to PGN file. You can also play a board position against any UCI engine by choosing Play > Serious Game. In the configuration window there's an option to play from the current position.

---

### Post by conscious on 2009-01-18
Rybka in Xboard (via Wine and polyglot).

---

### Post by japhyr on 2009-05-13
> You can also play a board position against any UCI engine by choosing Play > Serious Game. In the configuration window there's an option to play from the current position.

A belated thank you for this.  I had to leave chess for a while to finish graduate school, but I went back to it recently and reread this post.  It has been very helpful for practicing endgames.  However, I can only seem to play positions that start with white moving.  If it is black's move, the computer always seems to play black.  I don't see any way in SCID to specify what color I play, or any of the normal controls like "move now".  Am I missing something?  Are there controls like this in SCID?  If it makes any difference, I have it configured to use Fruit.

---

### Post by leipogs23 on 2009-05-13
I can't beleave i was able to find a thread here that talks about chess.haha! I used to be a chess adict, I just left it because of school. Anyone here also playing in chess.com?haha. Why not try fritz 3.5 using wine?? If I remember it correctly, its now a platinum rated. Used to prepare with it when I still use windows. Haven't tried it in ubuntu+wine though...

---

### Post by pwc on 2009-06-01
Here's an interesting link for you chess lovers, looks like a useful blog for linux users that play or study chess:

[http://www.linuxchess.org/](http://www.linuxchess.org/)

---

### Post by ArnoldGove on 2009-06-12
> **mivo said:**
> I usually play with the already mentioned Pychess, and recently bought a copy of [Shredder 11 for Linux]("http://www.shredderchess.com/linux.html"). It isn't free, but you can freely set the ELO value of the computer opponent (starting at 850), which none of the free alternatives offer, and there is a coaching mode. There is a 30-days trial version available, too, and Shredder works fine in Ubuntu (the install script didn't work, however). A graphically nifty, and free, chess game is [DreamChess]("http://www.getdeb.net/app/DreamChess"), which looks certainly better than the 3D chess interface that comes with Ubuntu.  :) All three are actively maintained.

I have Windows Deep Shredder. Any more comments on the Linux version? Does it come with a 64-bit Shredder engine (in case you have a 64-bit system) like the Windows version does?

---

### Post by powerfade1 on 2009-08-25
> **ArnoldGove said:**
> I have Windows Deep Shredder. Any more comments on the Linux version? Does it come with a 64-bit Shredder engine (in case you have a 64-bit system) like the Windows version does?
Here's a bump for a good question.  I'd like to know the answer, too!

---

### Post by Crunchy the Headcrab on 2009-08-25
Has anyone played battlechess?  It's freeware and runs in dosbox.  I haven't played it since I was a kid so my memory might be skewed but it's a fun game.  The chess pieces are animated and have battle animations when they conquer a square.

---

### Post by powerfade1 on 2009-08-25
> **pwc said:**
> Here's an interesting link for you chess lovers, looks like a useful blog for linux users that play or study chess:

[http://www.linuxchess.org/](http://www.linuxchess.org/)


Great link.  It should be very helpful, but will take a while for me to read!  :)

---

### Post by ricardisimo on 2009-11-18
The only engine I can get to output in scid is scidlet (in other words, the one that came with it). Can someone post the appropriate scid analysis engine settings for crafty, fruit, glaurung, gnuchess, hoichess and toga2, as well as any other engines that are readily available out there. Thanks.

---

### Post by robaljoo on 2009-11-18
i am using 3d chess its good

---

### Post by mivo on 2009-11-18
> **Crunchy the Headcrab said:**
> Has anyone played battlechess? It's freeware and runs in dosbox.

If this is the Battle Chess developed and released by Interplay between the late 80s and early 90s, it is not freeware. Interplay didn't release it as freeware and the copyright hasn't expired.

[IMG]http://upload.wikimedia.org/wikipedia/en/5/50/ST_Battle_Chess.png[/IMG]

---

### Post by ricardisimo on 2009-11-18
> **ricardisimo said:**
> The only engine I can get to output in scid is scidlet (in other words, the one that came with it). Can someone post the appropriate scid analysis engine settings for crafty, fruit, glaurung, gnuchess, hoichess and toga2, as well as any other engines that are readily available out there. Thanks.

Is anyone using scid getting analysis trees from any other engines other than scidlet and gnuchess? If so, how? Thanks.

---

### Post by ricardisimo on 2009-11-19
Let me rephrase that... is anyone using any linux app for analysis purposes? Or is everyone just playing 5-minute chess for practice?

---

### Post by hansteam on 2010-02-25
I run crafty for analysis, but I'm still looking for a good interface for it... I've tried xboard and eboard, but they just aren't as intuitive as babas...

---

### Post by houshdaran on 2010-04-30
I have got 4 questions:

1-How can I use Rybka in ubuntu?
2-Can I set a "postion" in ubuntu?I used glchess, but could not set a position with it, just a complete game..
se Rybka engine under ubuntu?I can download that for free, but don't know how to use it.
3-Can I find anything like or better than Mega database for free?

---

### Post by shcherbak on 2010-05-27
1) chess database
- scid 
- jose (java or wine)
2) analisis (many engines - Rybka included)
- Arena (wine)
3) game-play
- all above exp. jose
- jin eboard (for FICS)
- fritz (wine)
- shredder (ver for linux)
- chessgenius (wine)
- crafty (!!!)
...and more, but do not have time for testing

Amount of stuff for chess is huge, just setting things takes a bit
of time. Question is still on how to make scid more engine friendly?
Has anyone tried polyglot?

---

### Post by aklo on 2010-05-28
I'm looking for "GO" chess but everytime i download the game from the software center, it does not have an AI player. Can someone point me out in the right direction?

---

### Post by shcherbak on 2010-05-29
[http://senseis.xmp.net/?GoPlayingPrograms](http://senseis.xmp.net/?GoPlayingPrograms)

---

### Post by smartidiot on 2010-06-24
Scid and Stockfish together work great.  Stockfish is very close to Rybka and it is free.

I will have some blog posts on this on my blog [Attacking Chess]("http://attackingchess.blogspot.com")

Check it out and enjoy :)

I do almost all of my studying in Linux with Scid and Stockfish.  for Openings it is hard to beat Chess Position Trainer - running that in a VM.

---

### Post by spencercarran on 2010-06-28
PyChess has improved, but I still wonder what the deal is on some points. It defaults to having my strongest engine analyzing in the background—while I'm playing games on FICS! Obviously inappropriate. Eboard is sensible enough to DC you from FICS when you start an engine running.

Anyways, does anyone know of a good set-up for analyzing games? I basically want to feed a pgn to an engine and have it go through and annotate where any significant mistakes (ie changes in eval) occurred and what lines would have been better. I would rather not use Windows programs for this, even if they are flawless in WINE.

---

### Post by JuLx6 on 2010-07-20
Hi,

I've installed eBoard and Stockfish (with Polyglot) but I can't manage to have Stockfish show me any score or pondering, how can I enable that in the console ? Thanks !

---

### Post by Lobais on 2010-09-09
I do analysis with the utilities/blunders.py tool from PyChess. I can use any of my engines, just like PyChess.
It is not integrated in the app yet, so I think it is more a proof of concept. It works quite well though.
> ```
[thomas@ahle PyChess Head]$ PYTHONPATH=lib/ python utilities/blunders.py ~/mygame.pgn 
Selected file /home/thomas/mygame.pgn

The file contains the following games:
[0] Unknown vs. Unknown

Autoselecting game 0.

PyChess found the following analyzers on your system:
[0] PyChess 0.10beta3
[1] GNU Chess 5.07

What engine should be your analyzer? [n] 0

Enter how many seconds we should use for each move [n]: 10

PyChess 0.10beta3 will now analyze the game between Unknown and Unknown with 10 seconds per move.

.......Undoing
.....Undoing 6 -1075 Qd5
White blunder
Should have done: ['Nf3', 'Ne7', 'Bg4', 'h5', 'Bxh5+', 'Rxh5']
....Undoing 5 507 Bxc8
Black blunder
Should have done: ['Qxc8', 'Nf3', 'Nc6', 'O-O']
.....Undoing 5 0 e5
....Undoing 4 69 Bh3
.....Undoing 4 -15 dxe6
.....Undoing 3 0 fxe6
....Undoing 3 -264 e6
White blunder
Should have done: ['Bh3', 'Ne7', 'fxe6', 'dxe6']
....Undoing 2 279 gxf5
Black blunder
Should have done: ['Nc6', 'e4', 'Nf6', 'd4']
.....Undoing 2 0 f5
....Undoing 1 190 g4
Black blunder
Should have done: ['e6', 'e4', 'e5', 'Nc3']
.....Finish
[thomas@ahle PyChess Head]$ 

```
This means that the small pgn, I made for the example, had 5 blunders, at move 1... g4, at 2... Nc6, at 3. e6, at 5... Bxc8 and finally at 6. Qd5.

The whole game looked like this:
> ```
[thomas@ahle PyChess Head]$ cat ~/mygame.pgn 
[Event "Local Event"]
[Site "Local Site"]
[Round "1"]
[Date "2010.09.09"]
[White "Thomas Dybdahl Ahle"]
[Black "Guest"]
[Result "*"]

1. g4 f5 2. gxf5 e6 3. fxe6 dxe6 4. Bh3 e5 5. Bxc8 Qd5 6. Bf5 *
```

---

### Post by DangerOnTheRanger on 2010-09-09
Eboard with Sjeng, GNUChess, and Crafty, plus FICS connectivity.
I also use BabasChess under WINE for FICS.

I use XBoard for viewing PGN files.

---

### Post by japhyr on 2010-11-18
About a year and a half ago I used Jin to play on FICS, and really enjoyed it.  Now Jin seems to have a bug where it makes a sound every third move.  I can't play very well without sound because I can't tell quickly when my opponent has moved.  Is there a way to fix this?

I tried eboard, but that did not seem to work very well either.  Eboard kept showing my opponent's time running down when in reality my opponent had made a move, and my time had run out and then I got disconnected.  All while I was watching my opponent's clock tick away.

What clients are people using on FICS?

My handle is japhyryder, by the way, and I'd be happy to play anyone when I get this sorted out.

---

### Post by anlag on 2011-09-15
I  use Scid for database/analysis/training. Have multiple engines loaded but mostly use Stockfish, just installed Rybka as well though so will be giving that a go.

---

### Post by davesalyers on 2011-09-17
I primarily use PyChess with the following engines: Pychess 0.10beta3, Sjeng 11.2, Fruit 2.1, HoiChess 0.10.3, Phalanx XXII-pg, GNU Chess 5.07, Crafty 23.4. I like that Pychess automatically sets up and integrates most engines and that you can easily adjust the difficulty setting to match your skill level. (I'm a weaker player just coming back to Chess after many years.)

I also have Eboard and use that on occasion. I tried Xboard and while it is fully functional - I like something a bit more intuitive to use.

I also have a goal of learning Shogi and Xiangqi (Chinese chess). It is nice to see that Ubuntu has many of the classic games represented. (If it had more classic card games as well as dominoes I would be even happier - I live in a rural area with satellite internet so we lose signals during snow storms and such so installed games help to whittle away the time.)

BTW, to answer the previous query about FICS - PyChess is the 7th most used FICS interface - 874 users. Check out - [http://pychess.org/news/](http://pychess.org/news/)

---

