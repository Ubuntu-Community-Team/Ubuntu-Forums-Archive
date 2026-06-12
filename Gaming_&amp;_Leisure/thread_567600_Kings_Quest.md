---
title: "Kings Quest"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by Johnny3 on 2007-10-04
I am new to Ubuntu and have been trying to install Kings Quest from this page.
[http://sourceforge.net/project/showfiles.php?group_id=61344&package_id=130221&release_id=536215](http://sourceforge.net/project/showfiles.php?group_id=61344&package_id=130221&release_id=536215)

I am down loading this one  	kq-linuxbin-20070831.tar.gz   Mirror   	2967933  	90  	i386   
I can extract it but have tried all kind of ways to install it. Has anyone install this Kinds Quest. How was it done. I use 7.04 32 bit.
Thanks Johnny3
Gainesville Fl

---

### Post by FranMichaels on 2007-10-04
> **Johnny3 said:**
> I am new to Ubuntu and have been trying to install Kings Quest from this page.
[http://sourceforge.net/project/showfiles.php?group_id=61344&package_id=130221&release_id=536215](http://sourceforge.net/project/showfiles.php?group_id=61344&package_id=130221&release_id=536215)

I am down loading this one  	kq-linuxbin-20070831.tar.gz   Mirror   	2967933  	90  	i386   
I can extract it but have tried all kind of ways to install it. Has anyone install this Kinds Quest. How was it done. I use 7.04 32 bit.
Thanks Johnny3
Gainesville Fl

Hi, sorry to say, KQ, isn't short for King's Quest in this case. This game is a console style RPG, similar to the older Final Fantasy games.

The good news is you can run King's Quest under Ubuntu, using Scummvm for the original King's Quest, and DOSBox can run that or the VGA remake. Anyway, the other good news is that these games are once again on sale, and run through DOSBox.

[http://www.scummvm.org/](http://www.scummvm.org/)
[http://dosbox.sourceforge.net/](http://dosbox.sourceforge.net/)

I don't want to provide a link like an advertisement.

So just google for King's Quest vivendi, and you'll find a box set with some of these great old adventure games.

:KS

---

### Post by Ecthelion on 2007-10-31
To answer to question:

To install that kq, you need to check if

[quote="README"]This game requires the following libraries (not included):

Allegro Game Library 4.2
Dumb Sound Engine 0.9
The libaldmb1 Runtime library
Lua 5.0[/quote]

you have these libraries (if not, first install them)

And then you should go to a terminal and type

[quote="README"]To install, type "./install.sh". You probably need to be root.[/quote]

so: ```
sudo sh ./install.sh
``` after you cd to the correct dir of course :-)

All in all this is probably quite complicated for a newbie.
Th easy way is not to download it from sourceforge, but to install the version you can find in the ubuntu repository.


To do this 
-go to the menu Applications > Add/remove
-search for qk
-check the checkbox and execute changes.
Give in you password and everything will be installed automatically for you.

Quite easier isn't it :-)

---

### Post by EDaggett on 2007-11-02
hello Fran

I'm a new member and need help with installing Kings Quest the Collection.

I bought it from a person I don't know.

I'm running Windows XP Pro and have a Pentium D Processor
with a 160 Gig Harddrive and 1 Gig memory.

Please advise.

---

### Post by FranMichaels on 2007-11-03
> **EDaggett said:**
> hello Fran

I'm a new member and need help with installing Kings Quest the Collection.

I bought it from a person I don't know.

I'm running Windows XP Pro and have a Pentium D Processor
with a 160 Gig Harddrive and 1 Gig memory.

Please advise.

Hello. 

This is a Linux forum :) Specifically [Ubuntu Linux.]("http://www.ubuntu.com/")

But okay, since you are a fan of adventure games.

As I linked above:
[http://dosbox.sourceforge.net/](http://dosbox.sourceforge.net/)
If I'm not mistaken, that's what the collection series is using...

DOSBox can handle those games, basically read the readme. For most, just copying the game directory then opening the exe/bat "Open With" dosbox will do the trick. I don't recall if under Windows it has the same option, it should though.

If you need further help, it would be more appropriate in the official [DOSBox forums]("http://vogons.zetafleet.com/index.php?c=7"). You may even find a how-to there specifically for the collection series :)

Good luck.

---

### Post by Sleepallnight on 2008-05-24
> **Ecthelion said:**
> To answer to question:

To install that kq, you need to check if



you have these libraries (if not, first install them)

And then you should go to a terminal and type



so: ```
sudo sh ./install.sh
``` after you cd to the correct dir of course :-)

All in all this is probably quite complicated for a newbie.
Th easy way is not to download it from sourceforge, but to install the version you can find in the ubuntu repository.


 
- Oh yeah, at last a solution! I've been trying to install the new KQ since this morning until i got to this thread. thanks for your solution, it works well... 
- Another thing, as far as my concern installing from the ubuntu repository doesn't give you the latest version of the game yet, on the menu page when you first open the KQ game you'd be shown names of contributors and the (c) year of maintenance, the older one covers 2002-2006 and the newer one from today's sourceforge displays 2002-2007. I might be wrong, coz the website claims the latest update to be on february 2008 but thats just my conclusion after a couple of times of un & reinstalls.

---

### Post by hipsterical on 2009-03-16
kq is loads of ****. it sucks ***. there is no way coming out of the game play. crashes Xorg. has terrible 80's graphics and it is boring, boring, boring, boring and ugly, ugly, ugly. endless intros. it just ended a kde session and i lost data. i wish the programmer responsible for that pile of feces to get run over by a heavy truck . i am going to uninstall it right now... done. some one has the email of that incredible sucker? im gonna goatse him .

---

### Post by hikaricore on 2009-03-16
> **hipsterical said:**
> kq is loads of ****. it sucks ***. there is no way coming out of the game play. crashes Xorg. has terrible 80's graphics and it is boring, boring, boring, boring and ugly, ugly, ugly. endless intros. it just ended a kde session and i lost data. i wish the programmer responsible for that pile of feces to get run over by a heavy truck . i am going to uninstall it right now... done. some one has the email of that incredible sucker? im gonna goatse him .

thread closed you've been warned

---

