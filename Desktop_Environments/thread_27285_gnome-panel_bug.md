---
title: "gnome-panel bug ?"
date: 2005-04-15
forum: Desktop Environments
---

### Post by sakka on 2005-04-15
hi all..

    I am slightly disappointed in gnome as of late ( not even taking into account the nasty user wars which is so utterly stupid I can't even believe it ) and I'll explain:

    I installed ubuntu new release at suggestion of over zelaous linux friend << ( so far he's correct but that may change as my perception and use dictate ) and decided to: 

MainMenu > internet > gftp > 'add to menu' : ( cause I'm a file queen )

BOOOOOM > can't find icon ..so I go:
-----------
gftp ( that has no icon remember) > right click: properties > browse for icon ( that nautilus 'clearly' shows as there and named accordingly and btw which is 'already' shown as the appropriate 'gftp' icon before I even start browsing for it   ) and BAM again; Details: icon not found <<<

so to reiterate...do things like this just fall through the cracks for poor unsuspecting mothers and hair dressers like myself to come and find and faint over or is this just one of those 'shtuff happens baby' that we must just learn to live with  using open source software , or should this linux-wannabe-artist consider kde instead ???

seriously..I love linux..I think  ubuntu is clearly ahead of its time in some respects but  gosh stuff like this really make me want to go packing my apron in fear of what else 'broken'  lays around the corner ( kitchen is hot enough as it is and if my cake falls i'm strangling someone ) .

cheers
sakka
AKA: extra-ordinaire artist and housewife and  huge on the fence distro user ::
-----

---

### Post by Bob D. on 2005-04-15
OK, I'm a bit confused here about what you are trying to do, so please bear with me.

Are you trying to add the gFTP launcher to the panel? This line "MainMenu > internet > gftp > 'add to menu' : ( cause I'm a file queen )" makes it hard, for me, to understand what you wish to do.

Point me in the right direction and I'm sure we can figure out what is going on.

Bob

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]    I am slightly disappointed in gnome as of late ( not even taking into account the nasty user wars which is so utterly stupid I can't even believe it ) and I'll explain:[/quote]

If you think the GNOME vs. KDE arguments are bad, wait till you walk into a vim vs. emacs argument (these are text editors, used mainly by programmers).

[QUOTE=sakka]    I installed ubuntu new release at suggestion of over zelaous linux friend << ( so far he's correct but that may change as my perception and use dictate ) and decided to: 

MainMenu > internet > gftp > 'add to menu' : ( cause I'm a file queen )

BOOOOOM > can't find icon ..so I go:[/QUOTE]

Question: what exactly is this "main menu" you're talking about? Are you talking about the Applications menu? I've read that the menu editor for GNOME isn't quite ready for general use yet. Also, where is the gftp icon you're looking for located, according to the program?

---

### Post by sakka on 2005-04-15
Are you trying to add the gFTP launcher to the panel? This line "MainMenu > internet > gftp > 'add to menu' : ( cause I'm a file queen )" makes it hard, for me, to understand what you wish to do.

Point me in the right direction and I'm sure we can figure out what is going on.

Bob[/QUOTE]
--------
okay pulling my hair out of my eyes::

'add to menu' should have been 'add to panel' ;-) < sorry OOPS

the rest is right I believe.

bye
sakka

---

### Post by sakka on 2005-04-15
[QUOTE=Stormy Eyes]If you think the GNOME vs. KDE arguments are bad, wait till you walk into a vim vs. emacs argument (these are text editors, used mainly by programmers).



Question: what exactly is this "main menu" you're talking about? Are you talking about the Applications menu? I've read that the menu editor for GNOME isn't quite ready for general use yet. Also, where is the gftp icon you're looking for located, according to the program?[/QUOTE]
-----
okay now your scaring me but i'm rough so Ill bear it..text wars huh I can NOT wait ! ( bring it on honey ; Ill fight ya over using gedit ANYDAY > spatula ready !!!)

main menu is the..ahm...hmm..footprint ??

I downloaded gftp from synaptic after enabling the 'easy' to use universe option...ubuntu makes this so easy even a HOUSEWIFE/artiste like myself ( with cake in oven and on the phone with 10 people at the same time) can't mess up!lol

kudos to  ubuntu for thinking of us poor dumb housewives (haha)....

seriously...a big thanks for making linux easy to use and so awesome in spite of that...

bye
sakka

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]okay pulling my hair out of my eyes::

'add to menu' should have been 'add to panel' ;-) < sorry OOPS

the rest is right I believe.

bye
sakka[/QUOTE]

If you're using the GNOME that came with Hoary, you should have two add to panel options. One takes a launcher from the Applications menu and puts it on your panel. The other lets you create a custom launcher. First, open a terminal and do **killall gnome-panel** to reset it, if you've already run **sudo apt-get install gftp** to install gFTP. Then, do add to panel and choose the option to add a launcher from the menu.

Let us know if this works for you.

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]okay now your scaring me but i'm rough so Ill bear it..text wars huh I can NOT wait ! ( bring it on honey ; Ill fight ya over using gedit ANYDAY > spatula ready !!!)[/QUOTE]

Hey, lady, I'm not going to fight you over what text editor to use. If you're comfortable with Gedit, more power to you. But if you give me static for using vim, I'll sic my cat on you. :)

BTW, the main menu is the one with the little foot in the upper left corner of your screen.

---

### Post by sakka on 2005-04-15
[QUOTE=Stormy Eyes]If you're using the GNOME that came with Hoary, you should have two add to panel options. One takes a launcher from the Applications menu and puts it on your panel. The other lets you create a custom launcher. First, open a terminal and do **killall gnome-panel** to reset it, if you've already run **sudo apt-get install gftp** to install gFTP. Then, do add to panel and choose the option to add a launcher from the menu.

Let us know if this works for you.[/QUOTE]
---------

I had already done the second option you suggested when I made my post..

for some reason even though the 'icon' clearly shows up in 'browse for icon' under; gnomemenu > internet > gftp :properties:: 'icon' in lower left of the window dialogue <<..it wont actually show up ON the gnome panel ...

is this just a gnome-panel bug ?

hope I  made this clear...
bye
sakka
btw:: you are all safe..cake did not fall...although I must warn my spatula was ready for total war..LOL

---

### Post by sakka on 2005-04-15
[QUOTE=Stormy Eyes]Hey, lady, I'm not going to fight you over what text editor to use. If you're comfortable with Gedit, more power to you. But if you give me static for using vim, I'll sic my cat on you. :)

BTW, the main menu is the one with the little foot in the upper left corner of your screen.[/QUOTE]
------
you guys are fun..

glad to be here ;-)

cat and two dogs looking back at ya ;-)heh

bye
sakka

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]---------

I had already done the second option you suggested when I made my post..

for some reason even though the 'icon' clearly shows up in 'browse for icon' under; gnomemenu > internet > gftp :properties:: 'icon' in lower left of the window dialogue <<..it wont actually show up ON the gnome panel ...

is this just a gnome-panel bug ?

hope I  made this clear...[/QUOTE]

Just hit ALT+F2 to get a "run program" dialog. Type "killall gnome-panel" in the dialog, hit enter, and wait for the panel to reset. Does the icon show up?

---

### Post by sakka on 2005-04-15
[QUOTE=Stormy Eyes]Just hit ALT+F2 to get a "run program" dialog. Type "killall gnome-panel" in the dialog, hit enter, and wait for the panel to reset. Does the icon show up?[/QUOTE]
----------
yes it did and thanx indeed!..what is the cause of this behavior..is it gnome-panel badness or synaptic or weird combo thereof?

thx/cu
sakka

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]----------
yes it did and thanx indeed!..what is the cause of this behavior..is it gnome-panel badness or synaptic or weird combo thereof?[/QUOTE]

It's just gnome-panel being stupid; it needs a good kick in the ass every so often. Basically, if you install or remove programs, or add launchers to the panel, just do **killall gnome-panel** to make the panel reset and reflect the changes you've made to the system.

---

### Post by neighborlee on 2005-04-15
[QUOTE=Stormy Eyes]It's just gnome-panel being stupid; it needs a good kick in the ass every so often. Basically, if you install or remove programs, or add launchers to the panel, just do **killall gnome-panel** to make the panel reset and reflect the changes you've made to the system.[/QUOTE]
--------
hmm...stupid as in not being updated right or stupid as in a bug that has not been fixed meaning I should submit a bug file ?

thank you
sakka

---

### Post by sakka on 2005-04-15
[QUOTE=Stormy Eyes]It's just gnome-panel being stupid; it needs a good kick in the ass every so often. Basically, if you install or remove programs, or add launchers to the panel, just do **killall gnome-panel** to make the panel reset and reflect the changes you've made to the system.[/QUOTE]
--------
stupid as in bug or just something that has not been addressed by gnome developers ?

either way should I file a bug I wonder ?

thanks everyone
sakka

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=sakka]either way should I file a bug I wonder ?[/QUOTE]

Go ahead and file a bug. I'd file one too if I was in your place, but I just don't care enough about it since I have a work-around I can use.

---

