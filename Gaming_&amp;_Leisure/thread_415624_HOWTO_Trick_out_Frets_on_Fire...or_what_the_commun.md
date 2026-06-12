---
title: "HOWTO: Trick out Frets on Fire...or what the community was up to while you slept"
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by buttons on 2007-04-20
**[SIZE="3"]So you like Frets on Fire now, eh?[/SIZE]**

So do I, in fact it's taking damn near all my free time!  The vanilla [FretsOnFire-1.2.451]("http://fretsonfire.sourceforge.net/") installation is a very good game.  However, it is also quite broken and rather dull-looking.

**[SIZE="2"]Broken? How?[/SIZE]**

It doesn't have multiplayer!  Or the ability to play the other guitar parts.  Or to make the background image static, which is both less annoying and lets you do nifty things like make big concert halls for your backgrounds.

And the big one...

For anyone who has played a guitar (or the fantastic Guitar Hero), you understand the concept of the "Hammer On" and the "Pull Off" (HOPO).

A refresher:
Playing a note and then hammering your finger onto the string will play a different note, allowing you to play notes in rapid succession without strumming.  Similarly, playing a note and releasing your finger will change to another note.  This functionality inherent in string instruments is built into Guitar Hero and available to you via the incredible **[RF-Mod]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4423")**, written by Rogue_F of the [fretsonfire.net forum]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi") community.

*** NOTE**: The "HOPO" functionality built into FoF 1.2.451, which was introduced in 1.2.438, is merely a "tapping" implementation.  Rather than true HOPO functionality, the developers introduced a feature that simply lets you tap the note to play it rather than strumming as long as the end of the note is close to the next note.  This is just wrong and in songs like Sweet Child of Mine results in basically three strums for the entire intro.  It's certainly easier, but lacks realism and the challenge that made Guitar Hero so great in the first place.

**[SIZE="2"]OK, you've convinced me.  How on earth do you install this RF-Mod business?[/SIZE]**

Glad you asked!  Since RF-Mod changes so much of the basic functionality in FoF, it has to be compiled from source.  Fortunately for you, Syberdave of the of the [fretsonfire.net forum]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi") community has compiled both 32-bit and 64-bit RF-Mod implementations for you.  Note that as of the time of this writing, RF-Mod is NOT compatible with 1.2.451.  It is compiled against 1.1.324, but don't worry, RF-Mod fixes most of the memory leaks that plagued earlier versions for you as well.

Get them from [Syberdave's site]("http://syberdave.net/archive/"), or from [Rogue_F's official archive]("http://208.184.121.23:8080/FretsOnFire/") (win32 available as well).  This would be a good time to mention some of the other things RF-Mod does (from the [forum page]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4423")):

> Two huge items in this version...

HOPO (that work well and are selectable on or off, or even per song)
Multiplayer Head to head (Thanks Pudding), and Multiplayer Party mode.

Other things include:
A sexy scrolling high score list
Snazzy all in one RFmod settings menu
Highly useful relocatable song directory
Space saving no duplicate song.ogg and guitar.ogg
...And so much more (in the README.txt)

Just unzip the archive wherever you want FoF installed, and run the binary.  It's identical to the vanilla installation, thanks to Syberdave's hard work rolling it up for us linux folk.

**[SIZE="2"]K, this is nice.  But...you said something about tricking out?  And dull-looking?  I want SHINY THINGS[/SIZE]**

Don't we all.  For this portion of the guide, I would like to take a moment to explain how a (traditional) mod works in FoF.

You put a folder in the data/mods folder, titled whatever you want to call your mod.  In it, place a file with the same name as its data/ equivalent, and it will be replaced when you turn the mod on by going to Settings->Game settings->Mod Settings, changing the folder name to On, and going to Apply New Settings at the bottom of the menu.

For instance...if you have a neck skin you like, you make a folder called New Neck in data/mods, put your new neck.svg in there, turn on the New Neck mod, and presto!  New neck whenever you play.

Sound like too much work?  Pre-existing mods are ready for download, created by the [modding community]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=11;st=0") at fretsonfire.net!

Here are some [completed mods]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=1613") (various)

Some [GH backgrounds]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4605") (dgrams2000)

Some [new necks]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=467") (TapsaKn)

And more!  A bit of searching and you can find all kinds of wonderful goodies in there, or of course create your own.  I highly recommend downloading a couple of them, and then mixing and matching different pieces to suit your liking.

**What about those stupid cassette tapes?  I have a lot of songs from Guitar Hero II that I ripped off the cd I own, which is fair use and thus not illegal.  They look like crap.**

Never fear!  ThatJon has created an [Automatic Cassette Labeller]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=2940") (sic) which, when run, automatically downloads any labels it knows about.  All it requires is python, which you've got.

**[SIZE="2"]Last question...what about that stupid pink fret?[/SIZE]**

Ahh.  You have acquired a PS2 (with adapter) or XBOX 360 guitar, and you've noticed that all of the colours match except for the last one.  What happened to the orange fret?  Well, pink separates Frets on Fire from Guitar Hero.  To be honest, pink is easier to see.  However, because I own a PS2 guitar, sometimes my tiny brain is jarred by the sight of a pink fret on the screen and an orange one under my pinky.  I'm funny like that.

Anyway, to change this permanently, you can fire up your favourite text editor and hit up ~/.fretsonfire/fretsonfire.ini (obviously won't be there until you've played the game and/or changed some settings).

Find the theme section, and change it thusly:

```
[theme]
base_color = #FFFF80
fret3_color = #0000FF
background_color = #330000
hopo_color = #000000
fret0_color = #00FF00
fret4_color = #FF6600
selected_color = #FFBF00
fret1_color = #FF0000
fret2_color = #FFFF00
```
The important spot here is fret4_color, which is now orange.

*** NOTE AGAIN**: I include changing the hopo_color there to black from its RF-Mod default of light blue.  In my opinion this makes it much easier to see which notes can be HOPOed.  If you like it the way it is, don't change it.

--------------------

I think that about wraps it up for this guide.  I'll update it with other stuff as I think of it, and in the meantime please be sure to ROCK OUT.  Thank you.

Oh, and screenies! Everyone loves those:

(this is my own theme which I've mixed and matched from the available ones on the fretsonfire.net forums.  Because I have no idea where most of the images came from and thus can't give credit where credit is due, I think it would be wrong of me to post the theme I'm using.  If you ask about a certain element, though, I could probably find the time to track it down.)

---

### Post by palermi on 2007-04-20
WOooow!!! :guitar:

---

### Post by hikaricore on 2007-04-20
yery nice!

---

### Post by hikaricore on 2007-04-22
[http://www.fretsonfire.net/](http://www.fretsonfire.net/) seems to be down at the moment >.<

Also I found some songs for FoF at: [http://frets.freenerd.org/?songs](http://frets.freenerd.org/?songs)
(many of these songs are fret patterns only and need you to supply the music for legal reasons I assume, others are posted with "artist permision" take it as you will)

---

### Post by Tinusje on 2007-04-22
Hey, its a very nice guide :D But i got one quesiton though.. i installed the mod and everything, but when i want to play a song i only get a red screen. Like it's still loading or something, but i can wait all day long and it's still the same red screen :confused: Does anybody knows what the problem can be?

---

### Post by buttons on 2007-04-22
> **Tinusje said:**
> Hey, its a very nice guide :D But i got one quesiton though.. i installed the mod and everything, but when i want to play a song i only get a red screen. Like it's still loading or something, but i can wait all day long and it's still the same red screen :confused: Does anybody knows what the problem can be?

Do you have direct rendering working for your graphics card?

---

### Post by Tinusje on 2007-04-22
Yeah i think so. But the strange thing is that i could play FoF perfectly before i installed the mod. I didn't change any of the settings so it's pretty weird :confused:

---

### Post by syberdave on 2007-04-22
> **Tinusje said:**
> Hey, its a very nice guide :D But i got one quesiton though.. i installed the mod and everything, but when i want to play a song i only get a red screen. Like it's still loading or something, but i can wait all day long and it's still the same red screen :confused: Does anybody knows what the problem can be?

When do you get a red screen? When you start it? When you press "Play Game"? When you've selected a song?

Are there any errors that you pressed "OK" to? Did you put any songs into the data/songs/ folder? (Rogue_F said that I should remove the built-in songs to make the package smaller.) Are there any errors when you run the script from the command line?


And what makes FoF more appealing is that you can find Guitar Hero songs for it.

---

### Post by Tinusje on 2007-04-22
There are no errors or anything. I just select a song, then I select the difficulty and after that my screen just stays red.

And yes, I do have songs in de song folder, but I could play any song i had before I installed de mod. 
I tried to change settings but I always get the same result.

---

### Post by buttons on 2007-04-22
> **Tinusje said:**
> There are no errors or anything. I just select a song, then I select the difficulty and after that my screen just stays red.

And yes, I do have songs in de song folder, but I could play any song i had before I installed de mod. 
I tried to change settings but I always get the same result.

How did you install the mod?  The available tar is a standalone installation, requiring none of the vanilla FoF.  It should be in a separate folder entirely.

I'm not trying to insult your intelligence or anything but the way you keep saying "before I installed the mod" makes me think maybe you copied it into the mods directory instead or untarred over the original directory.  Just a hunch.

---

### Post by Tinusje on 2007-04-22
8-) Hehe I just didn't know how to exactly say it :P But i got it to work now :D I just re-installed FoF and then I "installed" the mod :D Don't know why it didn't work but hey, it works perfectly now so that makes me a happy man 8-) 8-)

---

### Post by syberdave on 2007-04-22
Uhm, well, glad it works.

---

### Post by hikaricore on 2007-04-22
don't you love problems that fix themselves?  ^_^

---

### Post by buttons on 2007-04-23
> **hikaricore said:**
> [http://www.fretsonfire.net/](http://www.fretsonfire.net/) seems to be down at the moment >.<

Also I found some songs for FoF at: [http://frets.freenerd.org/?songs](http://frets.freenerd.org/?songs)
(many of these songs are fret patterns only and need you to supply the music for legal reasons I assume, others are posted with "artist permision" take it as you will)

The forum appears to be back up, thankfully.

---

### Post by syberdave on 2007-04-24
RFmod 3.5 is out. Binaries uploaded.
Make sure you add songs since mine doesn't come with them.
You can take the data/songs/ folder from the official binary package.

---

### Post by Pdennis on 2007-04-24
Thanks!  This is great... 

My only wish is fore additional songs to become more easily available

---

### Post by syberdave on 2007-04-24
You could get a bunch of user-submitted songs here:
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=5;st=0](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=SF;f=5;st=0)

I think that's as easily available as it could get. Stuff is posted on Rapidshare, etc because of copyright issues. I think that some people put GH/GH2 packs up there.

---

### Post by justin whitaker on 2007-04-24
This game is kicking my nether region. :) 

I did find songpacks...so now I have 3gb of songs...but I can't even get past Bang Bang. :(

:lolflag:

---

### Post by Nate53085 on 2007-06-08
I can't get the mirror for the automatic cassette downloader to work.  I click the request download link button and it replaces that link with simple text that says download link.  There is no actual link.

**EDIT**

NVM, found it.  Link is just a little to lost in the ads.

---

### Post by BERRYBLITZ on 2008-01-13
Ya i joined this forum just to say how the hell u put the damn RF mod on 
i follow instructions in read me and in doesnt work
i cant start the fkin game it shows a red line  on the screen with the music playing  need help with that if anyone could give me proper instructions on how to put the mod on then plz write

---

### Post by sk8dork on 2008-01-14
i suggest everyone wondering about this mod go to the latest official thread for it here:
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=15905](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=15905)

i don't know if it's cuz i wasn't logged in, but the first post of that thread says that there's only going to be one more version of the mod to come out in the future and then it's done, and it links to another thread for explanation of this, but the link is broken. judging by the replies in the thread, i am guessing the mod is so kickass that the author is now/going to be on the FoF dev team and it will be integrated into future versions of FoF, without the need for the mod. this is only speculation on my part since the link to the explanatory thread is broken.

that said, the mod is probably not working for you because you have a newer version of FoF and a way outdated version of the mod. the posting of the mod linked in this thread was last update in april of 07. the thread i linked to above has been updated in december 07.

edit: you'll definitely want to stick with the 1.2.451 release of FoF and the 4.14 release of RFMod for now, at least until the next version of FoF comes out (right now 1.2.512 is the latest and it's quite buggy, and there isn't a version of this mod built for it yet.)

[here is the wiki link for the mod]("http://fretsonfire.wikidot.com/rf-mod")
and [here is the link to a forum post at fretsonfire.net with the latest and previous releases]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=2;t=4217"), regularly updated

edit again: read [this thread]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=2;t=15953") to see how the future of Frets On Fire is a bright and glorious one. woohoo!

---

### Post by Boktai1000 on 2008-06-22
For people who want to set up Frets on Fire now, its recommended to grab the newest version from [http://fretsonfire.wikidot.com/rf-mod](http://fretsonfire.wikidot.com/rf-mod) which of right now is 4.15.  The author of RF-mod is now developing for Frets on Fire and soon the features of this mod will be implemented in the standard download, which will make this a lot more convenient, especially if you can just grab it off Synaptic.

---

