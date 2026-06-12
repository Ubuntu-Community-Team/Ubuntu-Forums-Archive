---
title: "Any good Tarot or Astrology programs in linux?"
date: 2008-12-10
forum: General Help
---

### Post by iheartubuntu on 2008-12-10
I cant seem to find any that just work. Astrolog is commmand line and not quite what im looking for... anything else out there more in depth? Something to do with Tarot would be nice as well. Thanks for any tips.

---

### Post by Baji on 2009-02-04
Why don't you have a look at [https://help.ubuntu.com/community/Astrology](https://help.ubuntu.com/community/Astrology)

---

### Post by iheartubuntu on 2009-02-05
> **Baji said:**
> Why don't you have a look at [https://help.ubuntu.com/community/Astrology](https://help.ubuntu.com/community/Astrology)

Great! Thank you very much. Just what I had been looking for too!

:KS

---

### Post by giltwist on 2009-09-01
I'm working on something to do tarot readings in pyGTK.  I was just doing it to teach myself Python, but how cool is it that there's nothing out there?  I've looked around and there's like nothing;  it sort of makes me more motivated to finish it.

---

### Post by marseille on 2009-09-24
giltwist, plz let us know when you complete the tarot program.  i have been waiting forever for someone to get motivated to program some tarot software that works well on ubuntu linux.  the closest i came to having a tarot program on ubuntu was a java program but java doesn't always work out too well for me on 64-bit.

thx so much, this was gr8 news!:)

> **giltwist said:**
> I'm working on something to do tarot readings in pyGTK.  I was just doing it to teach myself Python, but how cool is it that there's nothing out there?  I've looked around and there's like nothing;  it sort of makes me more motivated to finish it.

---

### Post by giltwist on 2009-10-04
Classes are a little heavy this semester so I haven't had much chance to work on it.  However, I plan on getting some work done over thanksgiving break.  I've already got most of the under-the-hood stuff done (Side note: python isn't nearly as convenient as javascript for parsing XML).  Making the GUI look nice is a bit more trouble.  I'm hoping for a beta version in December.

---

### Post by iheartubuntu on 2009-10-08
> **giltwist said:**
> Classes are a little heavy this semester so I haven't had much chance to work on it.  However, I plan on getting some work done over thanksgiving break.  I've already got most of the under-the-hood stuff done (Side note: python isn't nearly as convenient as javascript for parsing XML).  Making the GUI look nice is a bit more trouble.  I'm hoping for a beta version in December.

Sounds great! What are you doing for the card images? If you scrounge around the net, there are sites with the entire ryder-waite deck scanned in :)

---

### Post by giltwist on 2009-10-12
Well, for copyright reasons, I probably shouldn't use any published tarot images.  I'm also not sure if the standard suits and arcana are copyrighted or anything.  The first release of my program will be supplied with a deck of my own devising so as to be completely in the clear.  I'm not much of an artist, so I thought the first release would just be text in appropriately shaped frames.  

That being said:

1) If any talented artist out there is interested in making a set of images, send me a message over AIM. 

2) If a licensing guru could help me figure out whether or not the standard deck format is public domain and any issues with using, say, the Rider-Waite images, that'd be awesome.  Again, feel free to AIM me.

3) The decks are specified via XML, so it will be super easy to add in image specifications once I've got some.

4) While switching entirely to images would look nice, I'm worried about how that might make it difficult to produce new decks.  My ultimate vision for this program is sort of the layout you see on a Magic The Gathering card: a title at the top, a small picture and a description at a bottom.  The picture will be optional.

---

### Post by marseille on 2009-10-12
*Consider* [GNU] *_[CARDPICS]("http://www.nongnu.org/cardpics/")_* :P


> Cardpics is a set of free cards sets.

If you are programming a card game and are looking for free cards, Cardpics was made for you! Get a set of cards and include them in your project, as soon as your project is free. [http://www.nongnu.org/cardpics/](http://www.nongnu.org/cardpics/)

[. . . ]

Cardpics is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version. [http://www.nongnu.org/cardpics/license.en.html](http://www.nongnu.org/cardpics/license.en.html)



Cardpics leaves some room for interpretation.  It has:

* 56 poker cards [52; plus the page for each suit; and a joker]
 
* plus 21 *blank* major arcana cards anyone can paint on

* and a back.

a while ago, i reworked cardpics in gimp so i could read a _[32-deck cartomancer]("http://xanadu.110mb.com/wiki/index.php?n=Python.Cartomancy")_ style: Ace; 7 on up (see the GNU result -- or use it/rework it -- _[here]("http://www.divshare.com/download/launch/1521202-5e2")_).


PS:  one thing i noticed about tarot software on *nix,  is that folks who read a deck of regular cards and _[post-lenormand]("http://api.ning.com/files/dws1kb1*KdJbCzRTQ7y--ptTCd2TYoiw95fgJ-xl9c9T67mtnWwAqyzvXMG9rJu2CYxTldTUMWLnCM2bFnJ-GzwJnm1gwwPl/PropheticalEducationandPlayingCardsLenormandKarten.pdf")_ followers have been forgotten.  it would be absolutely HOTT if that changed in the future;)

as for now -- *in my opinion* -- the best bet for a *GUI-based* card divination program for *gnome* on ubuntu are two pieces of open source tarot software, with one being java based.  they are:

**SymSolon Astrology Software**
[http://sourceforge.net/projects/symsolon/](http://sourceforge.net/projects/symsolon/)

 -- symsolon is an astrology based karmic card program and i have to say it's getting pretty fabulous since it's first release. it even casts an astrology wheel outlining each period of life with an associated `_[symbolon]("http://www.aeclectic.net/tarot/cards/symbolon/")_' card.

**jTarot Personal Advisor**
[http://sourceforge.net/projects/jtarot/](http://sourceforge.net/projects/jtarot/)

 -- then there's good ole trusty cross-platform java-based jTarot, *now moved to sourceforge*.  it has a variety of tarot decks and reading types but compared to symsolon, it takes a lot more effort to install it in ubuntu since it needs java.

---

### Post by giltwist on 2009-10-12
@marseille

Thank you for the link to cardpics.  As far as playing card decks, I would happily include them in the base release.  I am not familiar with either of the systems that you mentioned; can you suggest to me a resource that lists the meanings for them?  
Also, I want to reiterate that my system allows people to generate their own decks and spreads using a simple XML layout.  So if anyone else has other deck requests, please wait until my first release.

With respect to the other software you mentioned, mine is written in python, making it very much at home on Ubuntu.

---

### Post by marseille on 2009-10-12
> As far as playing card decks, I would happily include them in the base release. ... suggest to me a resource that lists the meanings for them?  

*i think* this is slightly more of a challenge -- *on an ethical level*.  although there a few texts out of copyright and available for your project's use, it's common to run across some meanings considered anathema -- as you probably well know since tarot is subject to the same issue. but of the more positive modern-day cartomancers, i would say _[robert camp]("http://www.7thunders.com/index.php?test=1")_ has cornered the *copyrighted* publishing market. he works off a 52 card method but note that there is more 20th century lit on the 32 card subject, even if it's more obscure.

so as they say: ` don't throw out the babies with the bathwater' -- i still suggest taking a look at what the previous generations have to say and their methods in laying out the cards.  especially since there is a difference between reading a full 52 card deck vs. a 32 or 36.

**[COLOR="DarkOrchid"]here are a few works out-of-copyright for you to use:[/COLOR]**

**PRS FOLI**: _[Fortune telling by cards]("http://xanadu.110mb.com/wiki/index.php?n=E-book.FortuneTellingByCards")_ (1904)

**Charles Platt**: _[Card fortune telling]("http://www.archive.org/details/cardfortunetelli00plat")_; a lucid treatise dealing with all the popular and more abstruse methods (1865)

* also see platt's excerpt on _[Mlle Lenormand's Nines]("http://xanadu.110mb.com/wiki/index.php?n=E-book.MlleLenormandNines")_ (*not to be confused with post-Lenormand cards*)

**Sepharial**: A Manual of Occultism: Cartomancy and Various Methods (1927) _[Chapter III Cartomancy]("http://xanadu.110mb.com/wiki/index.php?n=E-book.Cartomancy-VariousMethods")_

**Henry J. Wehman**: Mother Shipton's gipsy fortune teller and dream book: with Napoleon's Oraculum (1890) -- _[Fortune-Telling by Cards]("http://www.docstoc.com/docs/document-preview.aspx?doc_id=719166&key=MWZhYjk3NzUt&pass=NDBmZS00Mjcz")_

**Mrs. John King Van Rensselaer**: [Prophetical, educational and playing cards]("http://www.archive.org/details/propheticaleduca00vanruoft") (1912) Chapter: _[Lenormand Karten]("http://api.ning.com/files/dws1kb1*KdJbCzRTQ7y--ptTCd2TYoiw95fgJ-xl9c9T67mtnWwAqyzvXMG9rJu2CYxTldTUMWLnCM2bFnJ-GzwJnm1gwwPl/PropheticalEducationandPlayingCardsLenormandKarten.pdf")_

> Also, I want to reiterate that my system allows people to generate their own decks and spreads using a simple XML layout.  So if anyone else has other deck requests, please wait until my first release.

:KS excellent! it would be sweet if it was possible for the user to change the number of cards they use, ie 78, 52, 32, 36; as well as the relative meanings.

> With respect to the other software you mentioned, mine is written in python, making it very much at home on Ubuntu.

:KS fabulous, i luv _[python]("http://xanadu.110mb.com/wiki/index.php?n=Python.Cartomancy")_ :guitar:

*     *     *

_[more on tarot/cartomancy...]("http://xanadu.110mb.com/wiki/index.php?n=E-book.Tarot")_

---

### Post by giltwist on 2009-10-12
> it would be sweet if it was possible for the user to change the number of cards they use, ie 78, 52, 32, 36; as well as the relative meanings.

Here, maybe it would help if you saw the XML files.  They are still very much works of progress, but you can get the basic gist of things.  You can make tarot-like decks using both major and minor arcana or decks like playing cards using only minor arcana.  The enumeration of the cards is totally up to the user as well.  Instead of the standard tarot setup, my deck goes 0-9 then child, woman, man, elder.   You could very easily do A-K of each standard suit and decide whether or not to include jokers as major arcana.  The way I have it set up, the suits don't even have to be the same size.

---

### Post by iheartubuntu on 2009-10-13
Wasnt the Rider-Waite deck made back in 1911? Isnt it out of copyright? Let me check wiki just for the heck of it...

[http://en.wikipedia.org/wiki/Rider-Waite_tarot_deck](http://en.wikipedia.org/wiki/Rider-Waite_tarot_deck)

> U.S. Games currently claims copyright on the cards, although the actual copyright may only be valid on certain colorized versions of the card. While others argue that it is in the public domain in the US because they were created prior to 1923, the US Games claim may be valid because the derived version of the cards was not in the public domain when US Games created their copyright.

I wonder if you could use that deck, but just make it black and white.

---

### Post by bela.mihalik on 2009-10-17
Do you know this collection of Tarot decks?

**JBOT3 - Tarot Giga-Torrent; 300+ Tarot Decks (for Orphalese or other)**
(2.2GB - I attached a torrent file)

I thing it is a good idea to make a software that can understand this package.

---

### Post by giltwist on 2009-10-19
I'm pretty sure that torrent would defy copyright law.  While early editions of Rider-Waite MIGHT be in public domain, pretty much everything else is too new to use without express permission.

G

---

### Post by Giblet5 on 2009-10-19
Am I the only person who sees the fuming gobs of irony in the whole idea of computer tarot?

As I understand it, the "power" of tarot - if you believe in such things - flows from the reader and not the deck, so using a computer for card selection eliminates all of the reasons for doing it in the first place.

It's like "Oooh! Let's use a purely logical system to aid us in spiritualism!"

Free! A program that meditates for the user: ```
sleep 300
```

---

### Post by giltwist on 2009-10-19
@Giblet

Three thoughts:

1) How is it different than someone who believes in luck letting a computer pseudorandomly generate a lottery ticket?

2) You are right, the power is generally thought to originate from the reader and not the carda (though this is not universally true).  However, that power is not in the selection of the cards but in their interpretation.  A monkey can pick cards off the top of a deck, but only a person can put it all together using intuition that allows deviation from the "standard" definition of a card.

3) Not everyone uses Tarot religiously all the time.  I, for example, like to occasionally use Tarot cards for RPG sessions of games like DnD.  I know there are like d100 tables out there for pregenerated interpretations, but it's a lot more fun to give players the cards and let them do the readings.  Some of the games I play are over the internet, so a script that could generate the text I could copy & paste into an email or whatever would be very useful.  In fact, I personally don't like using my real deck for this game-mastering purpose.  A computer script seems much more appropriate.

---

### Post by Giblet5 on 2009-10-19
> **giltwist said:**
> @Giblet

Three thoughts:

1) How is it different than someone who believes in luck letting a computer pseudorandomly generate a lottery ticket?

2) You are right, the power is generally thought to originate from the reader and not the carda (though this is not universally true).  However, that power is not in the selection of the cards but in their interpretation.  A monkey can pick cards off the top of a deck, but only a person can put it all together using intuition that allows deviation from the "standard" definition of a card.

3) Not everyone uses Tarot religiously all the time.  I, for example, like to occasionally use Tarot cards for RPG sessions of games like DnD.  I know there are like d100 tables out there for pregenerated interpretations, but it's a lot more fun to give players the cards and let them do the readings.  Some of the games I play are over the internet, so a script that could generate the text I could copy & paste into an email or whatever would be very useful.  In fact, I personally don't like using my real deck for this game-mastering purpose.  A computer script seems much more appropriate.

Thank you for the eloquent clarification.

Once a person subscribes to the concept of luck then computer tarot starts make a kind of contextual sense as well, and you explained it very well.

My sides still hurt though.

---

### Post by iheartubuntu on 2009-10-22
> **Giblet5 said:**
> Am I the only person who sees the fuming gobs of irony in the whole idea of computer tarot?

As I understand it, the "power" of tarot - if you believe in such things - flows from the reader and not the deck, so using a computer for card selection eliminates all of the reasons for doing it in the first place.

It's like "Oooh! Let's use a purely logical system to aid us in spiritualism!"

Free! A program that meditates for the user: ```
sleep 300
```

You do have a point. Its like trying to do a java applet of the Ouija board on a website. Just not quite the same.

---

### Post by JakeFrederix on 2010-05-29
The first deck of tarot cards using Rider Waite images was published in 1909. Intellectual property rights only protect for a maximum duration of 70 years after the death of the author (or longest living author in case of multiple authors).

The deck was drawn by **Pamela Colman Smith**, who died in 1951. The rights will have expired in 2021. (of course, if nobody possesses the rights, then the point is moot)

She has no living relatives, so unless she explicitly sold the rights to anyone, you're free to use the images.

This however is a special case, as she was in serious debts by the time of her death, and everything she owned was sold to the highest bidder to pay off the debts. 

It was however uncommon in those days to sell intellectual rights, and although the paintings and drawings of the deck were sold, the rights remained untouched.

In short, since nobody owns the rights to the deck (regardless of the fact that they are still active), you are free to use them.

Kind regards,
Jake

---

### Post by donnagarnet on 2010-07-02
If you're still looking, I found this.  No idea if it's any good.  I found another tarot program for Linux but it was for websites to lure in customers.

[http://www.top4download.com/visual-tarot-pro-lifetime-license/kqcxkigl.html](http://www.top4download.com/visual-tarot-pro-lifetime-license/kqcxkigl.html)

---

### Post by Nick_Jinn on 2010-07-02
I would love an I-ching program.

I-ching is binary, so a program for it should be relatively simple.

---

### Post by proggy on 2010-07-03
> **donnagarnet said:**
> If you're still looking, I found this.  No idea if it's any good.  I found another tarot program for Linux but it was for websites to lure in customers.

[http://www.top4download.com/visual-tarot-pro-lifetime-license/kqcxkigl.html](http://www.top4download.com/visual-tarot-pro-lifetime-license/kqcxkigl.html)
I don`t think you should suggest a program you haven`t tested or tried.
I says linux but when you download it`s` exec.

---

### Post by marseille on 2010-07-30
It's been a while... school was crazy these past few semesters.

anyway, i'm hoping something good is happening with the python tarot program. tonight i upgraded to lucid and installed openastro (which went much better than i expected -- good install, fairly stable, only blew a fuse when i tried to save my chart as a PDF) and now i'm motivated to read my cards :KS

ps... i'll follow up on the earlier part of the thread... i got sidetracked too:D



----

also checked out the ($100) tarot/lenormand (22 | 36 | 78 deck) program out...

>  Originally Posted by donnagarnet  View Post
If you're still looking, I found this. No idea if it's any good. I found another tarot program for Linux but it was for websites to lure in customers.

[http://www.top4download.com/visual-t.../kqcxkigl.html](http://www.top4download.com/visual-t.../kqcxkigl.html)

and found out it has to run under [wine]("http://visualtarot.com/en/downloads/")... or toss it in the virtualbox or something i guess


--- 

iching is good too... i like the pyching python program in the repositories but my most fav oss iching piece of code is an obscure unix command line generator written a while back by _[aubrey jones]("http://web.archive.org/web/20060823080651/http://astro.temple.edu/~netzaper/iching/")_. i don't know if she ever released a newer version of her work but here is the last one i could track down is: _[iching-0.8.1.tar.gz]("http://web.archive.org/web/20040826225225/http://astro.temple.edu/~netzaper/iching/source/iching-0.8.1.tar.gz")_  ... take a look at a screenshot of it at my _[album]("http://ubuntuforums.org/album.php?albumid=268&pictureid=847")_.

---

### Post by wog on 2011-01-08
I'm looking for a Astrology program with a GUI, and I'm maybe about one step away from rank beginner. 

All the links at this site ([https://help.ubuntu.com/community/Astrology](https://help.ubuntu.com/community/Astrology)) seem outdated, providing no applications for the current version (Natty Narwhal) I'm using. 

This is particularly interesting because OpenAstro.org seems the most up-to-date option yet it seems dependent on python-gnome2-desktop, and so is uninstallable. Astrolog, the other option in the list simply isn't in the repositories at all, and so is not recognized. 

I found this other page ([http://www.linuxlinks.com/article/20100326204646824/Astrology.html](http://www.linuxlinks.com/article/20100326204646824/Astrology.html)) containing a few other options, but also with problems. In particular, Skylendar, pymorinus, oroboros, SymSolon pretty much all require either installing from source (a tarball) or else python (which I don't really understand).

From that list, only Maitreya has deb files, and therefore installs. I'm trying to habituate myself to it now, but it would be nice if there were other options to choose from.

---

### Post by marseille on 2011-01-09
If you're trying to practice Western geocentric, would you consider running a Windows app under Wine-HQ? I'm still running Lucid so I have no idea what's going on with newly released Ubuntu OS' but here is another option:

If openastro isn't working out, try ZET LITE freeware. [http://zaytsev.com/downloads.html](http://zaytsev.com/downloads.html)

Even though it lacks certain copy/paste and printing functions, it's a pretty nifty and comprehensive freeware. I have always seen it run stably under Wine in Ubuntu and (unlike Windows Astrolog) haven't had any font/legibility issues.


O T H E R:

(JYOTISH) 

[http://jyotishtools.com/linux.php](http://jyotishtools.com/linux.php)

---

### Post by thofke on 2011-07-13
> **marseille said:**
> It's been a while... school was crazy these past few semesters.

anyway, i'm hoping something good is happening with the python tarot program. tonight i upgraded to lucid and installed openastro (which went much better than i expected -- good install, fairly stable, only blew a fuse when i tried to save my chart as a PDF) and now i'm motivated to read my cards :KS

Any news on your python tarot program?

---

