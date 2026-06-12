---
title: "Ultima IV DOSbox/dbgl problems"
date: 2009-08-03
forum: Gaming &amp; Leisure
---

### Post by Nixie Pixel on 2009-08-03
Hi all, I am trying to get Ultima IV working in DOSBox. I'm using dbgl as my DOSBox front-end, and am currently using the "late 80's" template. The game runs when I use ultima.com as the launcher, but the sound keeps having problems (the music plays fine, then is distorted, then plays fine...etc.). 

I am not familiar enough with DOSBox to know how to fix the problem. Are there any DOSBox experts out there able to assist?

Oh, yes I do know about XU4, but the port has some bugs so I would rather play the original, which it requires. I don't know what the benefit is to play a beta port with bugs?

Thanks!

---

### Post by Grishka on 2009-08-03
you'll probably have to adjust cpu cycles. this may take some experimenting with ctrl+F12 and ctrl+F11, until you get it right.

---

### Post by rCXer on 2009-08-03
Not an expert but I had a similar problem with a different game.  One thing that helped was reducing the sound mixer's rate.  I'm not familiar with dbgl so here's how you can do this without it.  Basically you have to create a configuration file (dbgl might do this for you) and edit it.

* Run DOSBox
* Type "config -writeconf dosbox.conf" into the prompt. This should create a "/home/username/dosbox.conf" file
* Open it and scroll down to the line that says...
```

rate=22050

```
and change it to...
```

rate=11025

```
... or something lower like 8000.

---

### Post by Nixie Pixel on 2009-08-04
> **rCXer said:**
> Not an expert but I had a similar problem with a different game.  One thing that helped was reducing the sound mixer's rate.
Great, this worked for me, thank you!

Now I have a new problem - I can't move the cursor. Input is not being received by the game. Any idea why nothing I press does anything at all in the game?

Thanks!

---

### Post by rCXer on 2009-08-04
That's another problem I had.  It's a bug in DOSBox 0.72. There are 2 ways to fix this.

1. The easy way: Set usescancodes to false in your dosbox.conf

```

usescancodes=false

```

2. The hard way: Update to the next version of DOSBox.  DOSBox 0.73 fixes the problem but it's not in Ubuntu's repositories yet.  You have to build/download a copy using instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1171794)

---

### Post by Grishka on 2009-08-04
> **rCXer said:**
> That's another problem I had.  It's a bug in DOSBox 0.72. There are 2 ways to fix this.

1. The easy way: Set usescancodes to false in your dosbox.conf

```

usescancodes=false

```

this can also be set in DBGL. just tick off the 'use scancodes' option in profile's I/O tab.

> 2. The hard way: Update to the next version of DOSBox.  DOSBox 0.73 fixes the problem but it's not in Ubuntu's repositories yet.  You have to build/download a copy using instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1171794)

this is not hard at all, 0.73 can be installed easily from many sources now. get it from [getdeb](http://www.getdeb.net/app/Dosbox), use [playdeb](http://www.playdeb.net), or grab a package [from karmic](http://packages.ubuntu.com/karmic/dosbox). or use the newest [DBGL](http://members.quicknet.nl/blankendaalr/dbgl/) version, it comes with 0.73 as well.

---

### Post by Nixie Pixel on 2009-08-07
I have DOSBox 0.73, and the keyboard input doesn't work, with or without "use scancodes" checked.

I am not sure where to go from here...

Thanks again!

---

### Post by Grishka on 2009-08-07
ooh, nasty. do you have the same problem with any other DOS games?

---

### Post by BoyOfDestiny on 2009-08-07
Hmm... Does launching dosbox straight from Applications -> Games, greet you with a Z:\ prompt, and does input work?

If so, I'd say it's something odd with the front-end... 

If you'd like, try right clicking on your ultima4 (whatever it is, .exe, .com or .bat) and choose Open With... dosbox. It will launch it and handle the mounting (assuming you didn't add anything to your ~/.dosbox/dosbox-0.73.conf autoexec section.)

If it's still a problem, look for a setup.exe or install.exe in that ultima directory (I don't have the game for this platform...) and make sure input devices are configured properly.

---

### Post by Nixie Pixel on 2009-08-07
I haven't tried any other DOS games yet under linux, this is my first one - I ran DOSBox + DFend Reloaded on Windows in the past.

I ran it directly with DOSBox and I still had the same input problem.

The setup executable only allows me to choose sound, there are no input options.

The funny thing is that the first time I press a key (to skip the intro) it works, but anything afterward does nothing.

---

### Post by Nixie Pixel on 2009-08-07
Ok, I just ran Battletech: The Crescent Hawk's Inception without a problem, so the input issue is Ultima-IV specific it seems.

---

### Post by Crunchy the Headcrab on 2009-08-07
> **Nixie Pixel said:**
> Ok, I just ran Battletech: The Crescent Hawk's Inception without a problem, so the input issue is Ultima-IV specific it seems.

That sucks.  I'm thinking of buying the Ultima Collection.  It costs $30-150 depending on the source because EA screwed Origin and so these games are ultra rare.  I wish they'd rerelease them, but EA's so damn big now that I doubt it'll ever happen.

Love the Ultima games, so I'll probably still take the plunge eventually if it's possible to at least run 6-8 in dosbox.

---

### Post by anaconda on 2009-08-07
> **Crunchy the Headcrab said:**
> That sucks.  I'm thinking of buying the Ultima Collection.  It costs $30-150 depending on the source because EA screwed Origin and so these games are ultra rare.  I wish they'd rerelease them, but EA's so damn big now that I doubt it'll ever happen.

Love the Ultima games, so I'll probably still take the plunge eventually if it's possible to at least run 6-8 in dosbox.

I think Ultima IV is actually free nowdays. At least it can be downloaded from several places, which all claim that downloading it IS legal.

However. I have actually bought a cd with ultima 1-6. The CD wasn't pirated, BUT I got no instruction book with it.. 
Which is especially annoying with ultima6, because U6 asks a "security" question, which you can answer correctly only with the help of the book..

And it REALLY wasn't a pirated copy.  It was one CD in a 6 CD set that cost about 10&#8364;, Bought from a well respected shop. 

Just wanted to mention that, so that if you DO buy the collection, remember to check that you also get the manual with it.
(actually you can find the manuals from the net too...)

PS. I have Ultima 4 and 5 working well in dosbox. (havent tried the other ones in dosbox yet.)

---

### Post by Grishka on 2009-08-07
this is very odd, the cursors work for me as well, I can move the aspiring Avatar with arrow keys just fine. maybe something's wrong with your copy?

---

### Post by BoyOfDestiny on 2009-08-07
Alright, since it was a legal download. What's happens if you run avatar.exe directly? Does the input work then?

---

### Post by Nixie Pixel on 2009-08-10
> **BoyOfDestiny said:**
> Alright, since it was a legal download. What's happens if you run avatar.exe directly? Does the input work then?

When I run avatar.exe directly it says "No party formed!"

And yes, the source code has been released, hence how "XU4" was created legally.

---

### Post by Nixie Pixel on 2009-08-10
Oh, and I can't do anything at the "no party formed" message. So I'm sort of stuck :(

---

### Post by Grishka on 2009-08-10
you DID try pressing 'I' at the main menu, didn't you?

---

### Post by Nixie Pixel on 2009-08-11
> **Grishka said:**
> you DID try pressing 'I' at the main menu, didn't you?
Uhh....
:redface:

I guess I didn't...since I couldn't move the cursor and select Options or anything else, and nothing seemed to work (other than "I" apparently), I thought the input was bad.

So...sorry about that, "I" worked.

:(

---

### Post by TheKid965 on 2010-07-03
> **Nixie Pixel said:**
> 
And yes, the source code has been released, hence how "XU4" was created legally.

Yes, this is an old thread and I apologize for the necromancy, but I just noticed this while doing a search for XU4 and how to install it in Ubuntu.  I felt I had to clarify something that was never corrected, lest someone get the wrong impression about the status of *Ultima IV*.

First off, the actual source code for the game is *NOT* available, and probably never will be.  But that's not necessarily the fault of Origin or even EA; as with many vintage games, the source is probably lost to history (and would be for the Apple II at any rate).

Second, in 1999 Origin/EA allowed a PC gaming magazine (the name of which escapes me right now) to publish the complete version of *Ultima IV* on their cover CD-ROM, as a marketing gimmick for the then-new *Ultima IX*.  I'm a bit fuzzy on the details, but not long thereafter Origin gave permission for certain specific websites to mirror the game, and eventually allowed the XU4 project to do so as well.  That is how the game became, for all practical purposes, freeware (as opposed to Free Software or public domain).

There are many projects available to enhance or update the all of the old *Ultima* games* to work on modern hardware and/or operating systems.  These are, generally speaking, legal to distribute; however, all of them require an original copy of the game(s) in question to run.  And thus far, *Ultima IV* is the only original game to be legally available as a no-cost download.  There have been attempts by fans over the years to get EA to allow the distribution of the other games as legal abandonware, but all such requests have (perhaps unsurprisingly) fallen upon deaf ears.

Hopefully that clears up the legality of the *Ultima* issue, if there's any question.

[size=1]** - Well, all of them except *IX*.  But that game is both A) relatively modern and B) not exactly the most beloved game in the series to put it mildly.  I believe it works well under Wine, but haven't checked lately to make sure.*[/size]

---

