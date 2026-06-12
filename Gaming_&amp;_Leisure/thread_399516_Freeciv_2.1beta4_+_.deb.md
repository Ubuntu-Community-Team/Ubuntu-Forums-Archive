---
title: "Freeciv 2.1beta4 + .deb"
date: 2007-04-02
forum: Gaming &amp; Leisure
---

### Post by charlieg on 2007-04-02
I haven't yet mentioned it on [Free Gamer]("http://freegamer.blogspot.com/") but [Freeciv 2.1beta4]("http://www.freeciv.org/") was out this weekend.

Freeciv 2.1 has far better graphics than 2.0, a themed UI (Gtk or SDL alternative) and lots of gameplay balance tweaks.  There's a world of difference between 2.0 and 2.1!

YMMV with this release and the .deb I just created.  I'm using Feisty Fawn and used checkinstall to create the .deb package.  I do not offer any kind of support nor guarrantee it won't hose your system.  Use at your own risk.

However it should be mostly harmless. :-)

Get it from here:
[http://www.filecrocodile.com/?d=F28566042](http://www.filecrocodile.com/?d=F28566042) (gtk version, 9megs)
[http://www.filecrocodile.com/?d=D95441752](http://www.filecrocodile.com/?d=D95441752) (sdl version, 11.5megs)

Note: you can only install one or the other, not both at the same time.

To start the game try 'civclient' from a terminal.  Happy civilization building!

---

### Post by charlieg on 2007-04-02
Uploaded.  Get it whilst it's hot. :popcorn: 

Oh and visit [Free Gamer]("http://freegamer.blogspot.com/") whilst you are at it. 8)

---

### Post by charlieg on 2007-04-02
Um, sorry to spam, forgot to mention the above is the sdl version.  I'm gonna compile the gtk version now, then sort out a better named sdl version after that.  Yap yap yap.

[edit] Done [/edit]

---

### Post by Josey on 2007-04-02
Nice work.  The gtk version works perfectly as far as I can tell.

---

### Post by charlieg on 2007-04-03
I'm surprised this isn't more popular.

Freeciv 2.1 has far better graphics and much more balanced gameplay.  And the SDL version has a sexy UI (altho sexy is not necessarily more functional).

---

### Post by graabein on 2007-04-05
I love civilization. Looking forward to trying this version of freeciv but filecrocodile is slower than hell... No other means of sharing the files?

---

### Post by darkteckno on 2007-04-07
How do you start the game?

---

### Post by Spleen on 2007-04-07
First post - woohoo...

Anyways, to charlieg, thanks for compiling this. I only started using Ubuntu a couple of months ago, and there is no way I could have compiled this for myself. Worked like a charm on Edgy. Oh, it was the SDL version I decided to use... (randomly)

Bit off topic, but I browsed your site, lots of good info there. Care to recommend any good Jeff Minter  type clones, maybe a Gridrunner clone for linux. Something fast ;)

Thanks again.

---

### Post by charlieg on 2007-04-11
> **darkteckno said:**
> How do you start the game?
Try 'civclient' in a terminal.

---

### Post by teddybairs1 on 2007-04-11
SDL seems to work just as well as the win32 version under wine. Anyone know how to save a game though? Can't seem to find the menu for it.

---

### Post by Spleen on 2007-04-11
From the readme...

" The game may be saved the game at any time using the 'save' server
command, like so:

  save mygame.sav

You can restore a saved game by using the '-f' server option, eg:

  civserver -f oursave2001.sav

or, if the save-file was created by a server that compressed it:

  civserver -f oursave2001.sav.gz

Now the players can rejoin the game:

  civclient -n Alexander

Notice how the player-name is specified with the -n option. It's vital
that the player uses the same name as they had when the game was running,
if they're to be allowed in.

The game may then be restarted with the 'start' command as usual. "

Hope that helps... :)

---

### Post by teddybairs1 on 2007-04-11
It does, thanks, but you'ld think that with all the pretty additions to the sdl gui they could have thrown in a graphical save/load menu/button that would make it so we don't have to use the cli.:)

---

### Post by charlieg on 2007-04-16
It's still beta... I'm sure they did not omit these things on purpose. ;)

---

### Post by graabein on 2007-04-16
I played the gtk version on holiday but forgot to bring the deb back to my place... Anyone sharing it? Filecrocodile does not respond.




Never mind. I finally got a response from Filecrocodile.

---

### Post by MaximB on 2007-04-17
what is the difference between the gtk version and SDL version ?

---

### Post by teddybairs1 on 2007-04-17
the GTK version relies on the GTK libraries and the SDL relies on the SDL libraries. Functionally, the SDL version has more eyecandy than the GTK version, but generally the GTK version has been more stable and playable. Also the SDL version has sacrificed some ease of use for eyecandy, hence the aforementioned lack of a graphical save/reload. This is my understanding of the differences between them.

---

### Post by Josey on 2007-04-17
[SIZE="4"]Mirror for SDL version here[/SIZE]

[http://www.wikiupload.com/download_page.php?id=128568](http://www.wikiupload.com/download_page.php?id=128568)

I didn't know which host to use so just grabbed one quick.
Click on download file on the right by the google ads.

---

### Post by teddybairs1 on 2007-04-17
charlieg really did a great job with the deb packages. They both install and run with no complications or problems. Anyone know how to convince the powers that be to add these packages to the Ubuntu repositories? They haven't had a real freeciv update in a long time, and these packages deserve to be there.

I installed the GTK package today. I liked the eye-candy from the sdl package, but the GTK is just so much more functional and playable.

---

### Post by Spleen on 2007-04-17
I agree, I've tried out both versions and the GTK version was much more usable.

---

### Post by charlieg on 2007-04-18
> **teddybairs1 said:**
> charlieg really did a great job with the deb packages. They both install and run with no complications or problems. Anyone know how to convince the powers that be to add these packages to the Ubuntu repositories? They haven't had a real freeciv update in a long time, and these packages deserve to be there.

I installed the GTK package today. I liked the eye-candy from the sdl package, but the GTK is just so much more functional and playable.

There's no way these will get into the repos.  To start with they were made with checkinstall, which does not introduce dependency resolution, so that flat rules them out anyway.  Apart from that, they are versions of a beta game so not suitable for the repos.  And to compound things I adhered to no standards whatsoever, I just made educated guesses at things like version names etc.

---

### Post by teddybairs1 on 2007-04-18
As far as them being versions of a Beta game, have you checked out half of the software in the repositories? A large portion of it is version 0.9 or below. Boson is a good example. It is currently 0.13 and has far more bugs than Freeciv 2.1 Beta4. As for the rest, you obviously did well at the guesswork you did, and I imagine it wouldn't be that hard to run back through it and deal with the dependency resolution.

At any rate, it would just be a shame if the only Ubuntu users who knew about these debs were the ones who read this thread. Maybe they won't make it into the repositories, but it would be nice.[-o<

---

### Post by Perfect Storm on 2007-04-18
0.XX version is not the same as beta version in the linux world. Therefore you'll see alot 0.XX in the repo as well.

---

### Post by teddybairs1 on 2007-04-18
I stand corrected. I always knew that what Linux coders called a beta Microsoft called a release version, but you've got to admit, giving something a sub 1.0 version number does tend to make one consider it in the Beta category at best. 

I still think that the freeciv 2.1 beta4 is more stable than some of the stuff I've seen in the repos. Not all of it obviously, but there are a few programs that crash far too easily to be considered stable. fair enough?

---

### Post by MaximB on 2007-04-18
the gtk version crashed only once when I did "load game" , but after that it worked fine
8/10 in stability
great job !

---

### Post by charlieg on 2007-04-19
> **teddybairs1 said:**
> I stand corrected. I always knew that what Linux coders called a beta Microsoft called a release version, but you've got to admit, giving something a sub 1.0 version number does tend to make one consider it in the Beta category at best. 

I still think that the freeciv 2.1 beta4 is more stable than some of the stuff I've seen in the repos. Not all of it obviously, but there are a few programs that crash far too easily to be considered stable. fair enough?

The point is that FreeCiv _does_ have a stable version in 2.0.x so it can't be just replaced without extra thought.  It's not like any of the other Boson versions have less bugs.

---

### Post by teddybairs1 on 2007-04-19
Alright, you win. I just really liked the 2.1 beta which you compiled (didn't know you would argue with me over what was essentially a complement) and thought everyone should get the chance without having to run through the compiler. Goodness knows I couldn't make heads or tales out of their instructions. Most I've ever compiled is kbfx silk and that's because it included a script that I didn't have to work too hard on, and someone else posted a howto here on the forum somewhere.

---

### Post by charlieg on 2007-04-19
That's why I provided .debs - so people can play without compiling it.

I'm not arguing with you, per se, just explaining why it can't go into the official repos.

---

### Post by n8wood on 2007-04-19
Can someone post the .debs again, the links are no longer working.

---

### Post by engla on 2007-04-19
2.1 beta 4 is really great. I'm playing it now these days, although I found a bug myself that made my game crash (deterministically so I couldn't go on), but I filed the bug, and two days later I could update to svn (development code) that didn't crash anymore.

So play the game, file bugs (good bugs. Attach savegames if they help to reproduce), and help the freeciv devs.

Looking forward to this. The SDL client has possibilites.. the playfield and directly visible UI is great, however I still prefer the gtk client for city dialogs, start new game dialogs etc.. all those are easier to use.

---

### Post by charlieg on 2007-04-20
> **n8wood said:**
> Can someone post the .debs again, the links are no longer working.

The links work for me.  Try again.

---

### Post by charlieg on 2007-04-20
Yeah I found a few bugs in the game.  Specifically doing anything with diplomats seemed to crash the game for me.  Also I managed twice when saving/loading games to get it into a state where my nation was AI controlled.

---

### Post by psadams on 2007-04-24
I downloaded the GTK version of this & installed it. When I try to run the game from the terminal by typing "civclient" I get the following error message:

civclient: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

Any ideas on the causes of this?

I'm running Ubuntu 7.04 with all updates installed.

---

### Post by teddybairs1 on 2007-04-24
If it's looking for anything "sdl" related as a dependency, you may have downloaded and installed the sdl version of the game instead. I don't think the gtk version would use libsdl_mixer for anything.

the sdl libraries are not installed by default into Ubuntu that I know of. Pull up synaptic and do a search for "libsdl" (sans quotes). Install everything that is a libsdl package.

In general if a program asks for a specific dependency to run it (even after installing it without problems), the easiest thing to do is to search all the repos for it through synaptic/adept and then install it. That usually clears things up, at least for me.

Because this package wasn't set up by the "Master of the Universe (Repository)" it probably didn't do the instant download and install of any dependencies it might have actually needed like it would have if it was done from the repos using synaptic/adept.

---

### Post by psadams on 2007-04-25
> **teddybairs1 said:**
> If it's looking for anything "sdl" related as a dependency, you may have downloaded and installed the sdl version of the game instead. I don't think the gtk version would use libsdl_mixer for anything.

the sdl libraries are not installed by default into Ubuntu that I know of. Pull up synaptic and do a search for "libsdl" (sans quotes). Install everything that is a libsdl package.

In general if a program asks for a specific dependency to run it (even after installing it without problems), the easiest thing to do is to search all the repos for it through synaptic/adept and then install it. That usually clears things up, at least for me.

Because this package wasn't set up by the "Master of the Universe (Repository)" it probably didn't do the instant download and install of any dependencies it might have actually needed like it would have if it was done from the repos using synaptic/adept.
Thanks for the advice. That fixed the problem. It is now loading ok.

I definately installed the GTK version & it still needed those dependencies. Very strange.

---

### Post by charlieg on 2007-04-25
Not strange - Gtk is just a graphics thing.  Freeciv uses SDL for sound.  The SDL UI is simply a replacement for the Gtk UI.

---

### Post by teddybairs1 on 2007-04-25
Didn't know that. Learn something new every time I visit the forums.

---

### Post by Vaalek on 2007-05-22
Good day,

Maybe somebody will have suggestions on solving my problem. I start the game, the window with choices (Start New Game, Connect..., etc.) loads, but when I press any of the buttons the window just freezes. On pressing Start New Game it freezes immediately, on pressing other buttons it loads the next screen and immediately freezes there.

I'm trying to run the game on Xubuntu, repository version and myself compiled beta4 act similar. Running from terminal shows nothing special except of telling me the game will continue with disabled sounds - do not think the problem is there.

Is there any error log the game produces? Would appreciate any advise.

---

### Post by graabein on 2007-05-26
I have another problem. I installed the beta 2.1 GTK client and it works just fine. But now I'm in Xfce and I can't figure out where the startup file is? I want to play the game but all I get on the menu is the old and busted Freeciv 2.0x!

---

### Post by teddybairs1 on 2007-05-26
Hey, the executable should be in /usr/local/bin/civclient

Why not just uninstall the 2.0.x?

---

### Post by graabein on 2007-05-30
Thanks. That was the right executable. 

How do I select which version to remove? Can I see it with apt or Synaptic?

---

### Post by teddybairs1 on 2007-05-30
Generally it's the package names which should clue you in. Freeciv 2.1 and Freeciv 2.0.8 should be labeled as such. look for the version number. Also, you only have one package to deal with with 2.1, whereas you should have two or three to deal with with 2.0.8. Open up Synaptic and search for" freeciv" (sans quotes). This should give you a list of every package which has anything to do with freeciv. leave the one marked freeciv 2.1 alone and mark for removal the ones having freeciv 2.0.8 in their package names. The version number should be displayed as well, so this should clue you in. If it works, 2.1 shouldn't be touched, while 2.0.8 should be completely removed.

---

### Post by Phalanx747 on 2007-06-25
> **Vaalek said:**
> Good day,

Maybe somebody will have suggestions on solving my problem. I start the game, the window with choices (Start New Game, Connect..., etc.) loads, but when I press any of the buttons the window just freezes. On pressing Start New Game it freezes immediately, on pressing other buttons it loads the next screen and immediately freezes there.

I'm trying to run the game on Xubuntu, repository version and myself compiled beta4 act similar. Running from terminal shows nothing special except of telling me the game will continue with disabled sounds - do not think the problem is there.

Is there any error log the game produces? Would appreciate any advise.

I have the exact same problem, only under Gnome. No errors reported either, it just freezes. I've found, though, that if you let it run long enough it will unfreeze and just remain at the main menu. I would like to find a solution as well :-)

---

### Post by engla on 2007-06-27
> **Phalanx747 said:**
> I have the exact same problem, only under Gnome. No errors reported either, it just freezes. I've found, though, that if you let it run long enough it will unfreeze and just remain at the main menu. I would like to find a solution as well :-)

It sounds like a problem with starting the civserver. If you start it separately (civserver in a terminal), does it report any errors?

Regardless, it shouldn't freeze even if the server can't start.. then it should report the error.

---

### Post by Phalanx747 on 2007-06-30
> **engla said:**
> It sounds like a problem with starting the civserver. If you start it separately (civserver in a terminal), does it report any errors?

Regardless, it shouldn't freeze even if the server can't start.. then it should report the error.

Yup, this works! By starting civserver separately and having civclient "Join Game" I am able to play. It looks much better now than it used to! I should say, though, that when selecting "Join Game" you must use 127.0.0.1 rather than "localhost". The latter simply returns an error.

---

### Post by AegisTalons on 2007-07-07
Hey,
I cannot download the files on the first page from File Crocodile. I have been trying to connect to it for a while and nothing. I have tried to compile FreeCiv on my own, but I'm having problems because I do not have all the needed development packages installed. I do not want to install 80+ Megs of development packages to play a game that is half that. Please help. Thanks.

---

### Post by charlieg on 2007-07-08
Josey posted a mirror for the SDL version here:
[http://www.wikiupload.com/download_page.php?id=128568](http://www.wikiupload.com/download_page.php?id=128568)

Sadly the rather **RUBBISH** new "feature" for the Ubuntu forums makes finding such things difficult for new readers.

**GET RID OF THIS RIDICULOUS THREADING.  THE FORUMS ARE NOT A MAILING LIST.**

---

### Post by AegisTalons on 2007-07-08
The links on FileCrocodile are working again. Thanks. I already tried Josey's mirror, but I was not downloading the file correctly from that site. It kept downloading a single text file instead of a deb package. I had to install another package afterward, but it looks like it works now. Thanks

---

### Post by Df_Yz on 2007-10-27
Can you post .deb's for amd64?

p.s. Links in first post don't work :(

---

### Post by TidusBlade on 2007-10-27
Thats because this thread is ancient :p

---

### Post by fakt00r on 2007-11-01
Is there a chance to get the freeciv 2.1 with an update in ubuntu? :)

---

### Post by meborc on 2007-11-08
> **fakt00r said:**
> Is there a chance to get the freeciv 2.1 with an update in ubuntu? :)

there is a deb in getdeb.net for gutsy at least... i don't know if there is one for feisty

---

### Post by ricardisimo on 2008-03-07
Does anyone have experience with [this version]("http://www.getdeb.net/release.php?id=2076") at GetDeb? I'm on Feisty, but the deb is for 7.10... am I going to have dependency problems with libc6 or some other component? Thanks in advance.

---

### Post by ricardisimo on 2008-03-07
I just answered my own question. Yup. version 2.1.3 is NOT for Feisty.

---

