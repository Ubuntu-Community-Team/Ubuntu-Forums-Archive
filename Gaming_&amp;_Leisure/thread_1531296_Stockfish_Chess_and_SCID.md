---
title: "Stockfish Chess and SCID"
date: 2010-07-14
forum: Gaming &amp; Leisure
---

### Post by docetrago on 2010-07-14
Hi, folks.

I've downloaded and installed Stockfish 1.8.0-4 chess engine from 

[http://packages.debian.org/sid/i386/stockfish/download](http://packages.debian.org/sid/i386/stockfish/download)

I would like to know how to establish an UCI interface to Stockfish on SCID 4.2.1.

I wanna play serious games against Stockfish, but when I click ( on SCID ) the main menu Play > Serious Game, SCID opens the Game Configuration dialog box, but it isn't enabled because when I click on the Configure UCI engine button an error message appears : "No UCI engine defined."

So, how do I define the UCI engine ?
How do I run Stockfish under SCID ?

Any helping is welcome.

Thank you very much !

---

### Post by sas3 on 2010-07-22
Try configuring the UCI engine from the menu: Tools->Analysis Engine (Ctrl+Shift+A). You may not find your engine listed there, so hit "New" in the dialog box. I chose the following params and it worked for me:

Name: Stockfish 1.6 (I use 1.6 from the ubunutu repositories)
Command: stockfish
Directory: /home/Sas3/.scid (hit the ~/.scid button, it will fill this for you)
ELO: 3100 (perhaps you could tweak this too; it should be higher for 1.8 ).
UCI: select the checkbox.
I did try the "Configure UCI Engine" button from here, but most of it there is greek and latin for me. ;)

---

### Post by docetrago on 2010-07-23
> **sas3 said:**
> Try configuring the UCI engine from the menu: Tools->Analysis Engine (Ctrl+Shift+A). You may not find your engine listed there, so hit "New" in the dialog box. I chose the following params and it worked for me:

Name: Stockfish 1.6 (I use 1.6 from the ubunutu repositories)
Command: stockfish
Directory: /home/Sas3/.scid (hit the ~/.scid button, it will fill this for you)
ELO: 3100 (perhaps you could tweak this too; it should be higher for 1.8 ).
UCI: select the checkbox.
I did try the "Configure UCI Engine" button from here, but most of it there is greek and latin for me. ;)

Dear Mr. Sastry

I'm very thankful for your clear answer !

Now I can play serious games against Stockfish on SCID.

The only remark I'll leave here is that the parameter "Command", in my settings, refers to the location of the Stockfish program. It is :

Command : /usr/games/stockfish

And now we're done !

Cheers from Brazil.

---

