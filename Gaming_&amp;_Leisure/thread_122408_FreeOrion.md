---
title: "FreeOrion"
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by Garyu on 2006-01-27
Hey, I found this thread in Ubuntu backports forum. 

[http://ubuntuforums.org/showthread.php?t=40327](http://ubuntuforums.org/showthread.php?t=40327)

Maybe it could be moved here? In any case, any ideas on how to get FreeOrion to work? I want to try this version, since IMHO the Master of Orion II is one of the best computer games ever created.

---

### Post by polpak on 2006-01-27
Well the error you're getting from running it under wine means you're missing the visual C++ runtime library. I'm not sure how you installed wine, but I'd definately recommend using the winetools program to install the base system and the visual C++ libs. 

Course I'd definately recommend using a non-windows version and just compile it yourself.. (instructions here: [http://www.freeorion.org/index.php/Compile](http://www.freeorion.org/index.php/Compile))

---

### Post by Garyu on 2006-01-28
[QUOTE=polpak]Well the error you're getting from running it under wine means you're missing the visual C++ runtime library. I'm not sure how you installed wine, but I'd definately recommend using the winetools program to install the base system and the visual C++ libs. [/QUOTE]

Compiling when there are dependencies outside of the ubuntu repositories is nothing I will venture into at the moment. I'm still learning basic stuff. (trying to avoid the "noob"-word since it is bad language - I wouldn't use "nigger" either btw:-#)

I installed Wine by adding their repository to synaptic (binaries, not source) and just checking the box. I wish more companies made it that easy to install stuff. :D

---

### Post by KhaaL on 2006-10-25
I know it's a old thread - but I'd like to know if it's possible to run FreeOrion natively in ubuntu? Or wine'd...


(@Garyu: Pluggar du också på umu? kul att se att jag inte är den enda som andv. ubuntu där ;))

---

### Post by Garyu on 2006-10-25
> **KhaaL said:**
> I know it's a old thread - but I'd like to know if it's possible to run FreeOrion natively in ubuntu? Or wine'd...


(@Garyu: Pluggar du också på umu? kul att se att jag inte är den enda som andv. ubuntu där ;))

Nope, SLU, jag läser till jägmästare. :cool:
Annars finns det nog en hel del Ubuntuanvändare i Umeå. En av dom som jobbar på Ålidhems Datorhörna använder Kubuntu. I Robertsfors finns en relativt aktiv grupp som jag hört talas om. Sen har jag väl tvingat ett par av mina bekanta att använda Ubuntu ("annars hjälper jag er aldrig mer när ni får problem med datorn" är en bra övertalningsmetod har jag märkt).

As you can see from this page:
[http://www.freeorion.org/index.php/Compile](http://www.freeorion.org/index.php/Compile)
FreeOrion has some dependencies that aren't in the ubuntu repositories. Quite a shame, since this game seems promising enough. It is probably possible to compile the game, if you solve the dependencies first. I don't know enough about programming to venture into this, but I would rejoice if anyone would take the time to make a .deb or a howto on this...

---

### Post by Sukarn on 2006-10-26
Uh, mind talking in english or using the PM system instead?

---

### Post by StickyStyle on 2006-10-26
Never mind me, need to fully understand the post first.

---

### Post by andnobodyslept on 2006-12-14
This game looks great, unfortunately it is still not ready for ubuntu (or is ubuntu not ready for this game), either way there is a guy at debian who has put a little under half a year in on making a deb package. 
[http://freeorion.org/forum/viewtopic.php?t=1490&sid=ac0dc0da9dab7adc0bc7308611b0f786]("http://freeorion.org/forum/viewtopic.php?t=1490&sid=ac0dc0da9dab7adc0bc7308611b0f786")
I would give him a buzz and see what I can do to help out, unfortunately I don't have to skills. 
I would also love to know if anyone has gotten this game up and running under edgy and just hasn't posted in the forums, because I would love to know how, mainly since the how to on the freeorion site is a little old.

here's to hope

---

### Post by andnobodyslept on 2006-12-16
Ok, so I got the game compiled, and running, and it is showing it's alpha stage qualities, basically there is an error that occurs whenever you do a certain thing (opening/closing the fleet window), but it can be compiled on edgy. My advice, go through the dependencies one by one using aptitude not apt-get, since some of the dependencies need to downgrade some other packages and aptitude will do this for you. Also as I said before, go one by one, since doing them all at once won't get you too far. Also get FMOD, I just stuck it in my home folder and used the advice they gave on the compile page. Finally read the debian guy's story, there is some good adivice in there and the Ubuntu one is from 5.04 and not all that useful. 
As I said before the game looks beautiful, and there is no doubt in my mind in a year or so they will have a great beta version that will be very playable. In the meantime, if you like MOO2 and have some free time, try installing the game, this project looks good.

---

### Post by Garyu on 2006-12-17
Nice. So you actually got it running? That's great. But if it's as you say very alpha... I think I might wait a while before installing it. I'm not very fond of crashes, even though I absolutely love this game... =)

Thumbs up! Hope the beta version isn't too far away. :D

---

### Post by andnobodyslept on 2006-12-17
Ya, getting the game running took some time, and the artwork that has gone into it looks great. Unfortunatly it is very alpha, and the forums aren't that active. I would lend a hand but I know nothing about programing (plan to learn some over the next year or so) so I really can't lend a hand. I say if you know C++ and are interested go over and give them a hand, the main programmers seem like they are motivated, just a little overwhelmed. I'm going to keep an eye on it and wait or the 0.4 release, though I don't know when that is.

---

### Post by Spalatum on 2007-07-03
How did you manage to set it up. I read the wiki but I did not understand it all 100%. Can someone please try to guide me how to get this going?

---

### Post by mikedep333 on 2008-01-22
New Release:
[http://www.freeorion.org/index.php/Main_Page](http://www.freeorion.org/index.php/Main_Page)

> FreeOrion 0.3.1-RC7 has been released. This release has some initial test shipdesign functionality, initial fleet supply route display code, many new tech, special and building icons, and various UI improvements and bug fixes. ... Linux users need to compile from source.

---

### Post by Achetar on 2008-03-20
3.8 is out now. All dependencies can be met (besides GiGi) through apt-get. Unfortunately, I am still having errors (building on Hardy) if I get it built, I will post a guide.

---

### Post by Perfect Storm on 2008-03-20
GiGi comes with FreeOrion (if they havn't changed it) - SVN

---

### Post by Perfect Storm on 2008-03-20
Just tested today FreeOrion 64-bit guide to make sure it still works.
[http://gaming.gwos.org/doku.php/guides:64bit:freeorion](http://gaming.gwos.org/doku.php/guides:64bit:freeorion)

This is tested on Ubuntu 7.10 64-bit Gnome with Nvidia card.

---

### Post by Achetar on 2008-03-21
It doesnt work for me. Hmm. Oh wait, right I run i386. but I downloaded the 386 version of the ogre package. Errors out on freeorion compile (cant find GG?) Anyway, I am going to start a thread for htis.

---

### Post by Nullack on 2008-06-30
The guide is 404, can anyone help please? Im on 64bit

---

### Post by Cappy on 2008-07-01
> **Nullack said:**
> The guide is 404, can anyone help please? Im on 64bit

[http://64.233.169.104/search?q=cache:0xYZ6c7XhcsJ:gaming.gwos.org/doku.php/guides:64bit:freeorion+guides:64bit:freeorion&hl=en&ct=clnk&cd=3&gl=us&client=opera](http://64.233.169.104/search?q=cache:0xYZ6c7XhcsJ:gaming.gwos.org/doku.php/guides:64bit:freeorion+guides:64bit:freeorion&hl=en&ct=clnk&cd=3&gl=us&client=opera)

---

### Post by rtom on 2009-03-04
It seems a bit old topic but I just came over and found that you don't need to compile the game from source, just download [http://freeorion.psitronic.de/download/latest.tar.gz](http://freeorion.psitronic.de/download/latest.tar.gz) and unpack. I placed it into /usr/local/games, started with the freeorion binary, runs smooth.

Tested on 8.10.;)

---

### Post by theShaggy on 2009-03-12
This game appears to both slow my computer to a crawl (while the game runs fine) and shut down my internet.

Any ideas why?  I'm playing single-player, which I don't think needs the internet (at least according to the FAQ on Freeorion.org), but it still happens.

---

### Post by nloewen on 2009-03-15
I have it running but when I'm in the game I'll click on something and the game will randomly crash. I had to disable compiz in order to get it to display anything. Hope to be running smooth soon.

---

### Post by rtom on 2009-04-10
theShaggy and enloewen: did you try to start the game in terminal and look for error messages?

---

### Post by glotz on 2009-04-10
> **Garyu said:**
> Master of Orion II is one of the best computer games ever created.
Agreed. Keeping an eye on this project.

---

### Post by nloewen on 2009-04-11
> **rtom said:**
> theShaggy and nloewen: did you try to start the game in terminal and look for error messages?

no. I removed the game because there's no AI and it gets boring playing by yourself so I can't check. That would probably be useful though.

---

