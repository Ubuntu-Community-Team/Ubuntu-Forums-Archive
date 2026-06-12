---
title: "Play Starcraft natively on Linux!"
date: 2007-05-01
forum: Gaming &amp; Leisure
---

### Post by disturbedite on 2007-05-01
*My Disclamier:  I am not affiliated with the project in any way and just thought I'd make this post to let anyone interested know about it since no one else had yet.*

I am very pleased to announce the release of version 0.1 of Stargus!  You are now able to play Starcraft natively in Linux!  Eventually (assuming development stays active) it will supersede the need to use Wine to play Starcraft.
[I]
"Stargus is a Starcraft Mod that allows you to play Starcraft with the [Stratagus]("http://www.stratagus.org/") engine, as opposed to play it with the original Starcraft one. So unless you have a legal copy of Starcraft, Stargus will be pretty useless to you, since it doesn't come with any graphics or sounds itself. [/I]  * So why play Starcraft with the [Stratagus]("http://www.stratagus.org/") engine instead of the original Starcraft one? There are numerous reasons. It allows you to play Starcraft under Linux and other operating systems not supported by the original Starcraft engine. Also the Stratagus engine allows you to tweak numerous parameters so you can play around with different unit strength and such. *
  * Since Stargus uses a different engine, the game will not be an exact replica of the original Starcraft. If you want the original unchanged Starcraft experience, you will still have to run the original game."*  

**Don't misunderstand this though, this is only version 0.1 so it is still very incomplete and prone to issues.  Although I have ran it on Kubuntu Gutsy so far without issue.**

To clarify, here is what is complete and what is not:
    *  All of the Terran units have been added although not all of the features work yet
    * Sounds and music work
    * In-game menus are mostly finished

    * Protoss and Zerg have not been added yet
    * Campaigns do not work
    * The Computer AI is very simple
    * Videos do not work
    * Tileset flags are not working so it's possible to walk over all terrain

** Get it here!:  [http://stargus.sourceforge.net/](http://stargus.sourceforge.net/)**

Requirements:
Original Starcraft CD, Stratagus (I'd recommend compiling from source since the latest version in the Ubuntu Repos is outdated), and Stargus.
[COLOR=Red]Read the aforementioned page for installation instructions.[/COLOR]

[I]DISCLAIMER:
Stargus is not an official Blizzard product, it's a Starcraft modification, by Starcraft fans for Starcraft fans. You need a copy of the original Starcraft version to make use of Stargus. Starcraft is a registered  trademark of [Blizzard Entertainment]("http://www.blizzard.com/").[/I]

---

### Post by po0f on 2007-05-01
I will *definitely* be keeping an eye on this project's progress.  Thanks for the heads-up.  :)

---

### Post by MilosDusan on 2007-05-01
Oooh awesome.. Hope it'll also allow support for Brood Wars ;)

---

### Post by The Noble on 2007-05-01
Hm, it's not installing for me. I downloaded stratagus from the repos (not that old) and I have the stargus folder. Attempting a "make" only gives me this error:

```

b@b:~/Desktop/stargus-0.1$ make
rm -f startool.o mpq.o
g++    -c -o startool.o startool.cpp
startool.cpp:55:17: error: png.h: No such file or directory
startool.cpp: In function &#8216;int SavePNG(const char*, unsigned char*, int, int, unsigned char*, int)&#8217;:
startool.cpp:2662: error: &#8216;png_structp&#8217; was not declared in this scope
startool.cpp:2662: error: expected `;' before &#8216;png_ptr&#8217;
startool.cpp:2663: error: &#8216;png_infop&#8217; was not declared in this scope
startool.cpp:2663: error: expected `;' before &#8216;info_ptr&#8217;
startool.cpp:2673: error: &#8216;png_ptr&#8217; was not declared in this scope
startool.cpp:2673: error: &#8216;PNG_LIBPNG_VER_STRING&#8217; was not declared in this scope
startool.cpp:2673: error: &#8216;png_create_write_struct&#8217; was not declared in this scope
startool.cpp:2678: error: &#8216;info_ptr&#8217; was not declared in this scope
startool.cpp:2678: error: &#8216;png_create_info_struct&#8217; was not declared in this scope
startool.cpp:2680: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:2685: error: &#8216;setjmp&#8217; was not declared in this scope
startool.cpp:2687: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:2691: error: &#8216;png_init_io&#8217; was not declared in this scope
startool.cpp:2694: error: &#8216;Z_BEST_COMPRESSION&#8217; was not declared in this scope
startool.cpp:2694: error: &#8216;png_set_compression_level&#8217; was not declared in this scope
startool.cpp:2700: error: &#8216;PNG_COLOR_TYPE_PALETTE&#8217; was not declared in this scope
startool.cpp:2702: error: &#8216;PNG_INFO_PLTE&#8217; was not declared in this scope
startool.cpp:2703: error: &#8216;png_colorp&#8217; was not declared in this scope
startool.cpp:2703: error: expected `;' before &#8216;pal&#8217;
startool.cpp:2707: error: &#8216;png_byte&#8217; was not declared in this scope
startool.cpp:2707: error: expected `;' before &#8216;trans&#8217;
startool.cpp:2709: error: &#8216;trans&#8217; was not declared in this scope
startool.cpp:2711: error: &#8216;png_set_tRNS&#8217; was not declared in this scope
startool.cpp:2715: error: &#8216;png_write_info&#8217; was not declared in this scope
startool.cpp:2722: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:2731: error: &#8216;png_write_image&#8217; was not declared in this scope
startool.cpp:2732: error: &#8216;png_write_end&#8217; was not declared in this scope
startool.cpp:2734: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp: In function &#8216;int ConvertWav(char*, char*, int)&#8217;:
startool.cpp:3875: error: &#8216;gzFile&#8217; was not declared in this scope
startool.cpp:3875: error: expected `;' before &#8216;gf&#8217;
startool.cpp:3881: error: &#8216;gf&#8217; was not declared in this scope
startool.cpp:3881: error: &#8216;gzopen&#8217; was not declared in this scope
startool.cpp:3887: error: &#8216;gzwrite&#8217; was not declared in this scope
startool.cpp:3893: error: &#8216;gzclose&#8217; was not declared in this scope
startool.cpp: In function &#8216;int SavePanel(int, int)&#8217;:
startool.cpp:3981: error: &#8216;png_structp&#8217; was not declared in this scope
startool.cpp:3981: error: expected `;' before &#8216;png_ptr&#8217;
startool.cpp:3982: error: &#8216;png_infop&#8217; was not declared in this scope
startool.cpp:3982: error: expected `;' before &#8216;info_ptr&#8217;
startool.cpp:3997: error: &#8216;png_ptr&#8217; was not declared in this scope
startool.cpp:3997: error: &#8216;PNG_LIBPNG_VER_STRING&#8217; was not declared in this scope
startool.cpp:3997: error: &#8216;png_create_write_struct&#8217; was not declared in this scope
startool.cpp:4002: error: &#8216;info_ptr&#8217; was not declared in this scope
startool.cpp:4002: error: &#8216;png_create_info_struct&#8217; was not declared in this scope
startool.cpp:4004: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:4009: error: &#8216;setjmp&#8217; was not declared in this scope
startool.cpp:4011: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:4015: error: &#8216;png_init_io&#8217; was not declared in this scope
startool.cpp:4018: error: &#8216;Z_BEST_COMPRESSION&#8217; was not declared in this scope
startool.cpp:4018: error: &#8216;png_set_compression_level&#8217; was not declared in this scope
startool.cpp:4024: error: &#8216;PNG_COLOR_TYPE_RGB_ALPHA&#8217; was not declared in this scope
startool.cpp:4030: error: &#8216;png_write_info&#8217; was not declared in this scope
startool.cpp:4037: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
startool.cpp:4047: error: &#8216;png_write_image&#8217; was not declared in this scope
startool.cpp:4048: error: &#8216;png_write_end&#8217; was not declared in this scope
startool.cpp:4050: error: &#8216;png_destroy_write_struct&#8217; was not declared in this scope
make: *** [startool.o] Error 1
b@b:~/Desktop/stargus-0.1$ 

```

I have some homework to do, so this is not a tradegy yet, but if any kind sould could help in an hour or two it would be greatly appreciated.  Thanks for pointing this out disturbedite.

---

### Post by po0f on 2007-05-01
The Noble,

Did you not notice the first error?  Install libpng-dev and you should be good to go.

---

### Post by The Noble on 2007-05-01
Ah, thanks! I had to install the latest libpng-dev in the repos (currently 1.2 I think) and its is installing now. I totally missed where it said what package i was missing.

---

### Post by Entity` on 2007-05-01
dude there is no way that i am going to let this slip from my eyes.  if it reaches 1.0 or somewhere close, ill be eternally grateful for your work.  for now ill give it a whirl, and if it works with Brood war, im gonna be runnin hamachi on my pc all the time and using ubuntu.

your the greatest!!!   *cries in utter joy*=D>

---

### Post by po0f on 2007-05-01
I am so excited, this is like a Christmas present.  Only it's May and not Christmas.  There are no emoticons to express how I feel right now.

(Played it a little, it works.  WOO HOO!)

---

### Post by donkyhotay on 2007-05-01
Man, I love starcraft and I'm eager to see it come out for linux. The only bad thing I see about it when it's done is coordinating with others to play it. I hope someone sets up a master server somewhere so it'll be easier to find online games.

---

### Post by The Noble on 2007-05-01
Whoo! I got it to work after compiling stratagus by myself (took a while) and following the directions. There are a bunch of dependencies, all of which are in the repos. Looks nice too.

---

### Post by disturbedite on 2007-05-02
i'm really glad that ppl enjoy this.  i thought all you would.  i just thought i'd share the news.  (its actually been out for a little while).

just to remind everyone, i am not affiliated with the project at all, i just shared the news.

> **MilosDusan said:**
> Oooh awesome.. Hope it'll also allow support for Brood Wars ;)
well, wargus works with war2 OR war2 exp.  the catch is tho, that it only works with the dos cds, not bn edition.  (i believe the only reason it works with the dos cds is cuz no one has implemented support for the bn edition cd).  so i think stargus eventually (when it gets mature enough) will support sc and/or bw.  aamof i'm sure it will, since it wouldn't really be complete without all the stuff that bw introduced.

---

### Post by Entity` on 2007-05-02
Dude. I'm gonna tell you this once:
Run as fast as you can and don't look back.

Once Blizzard notices, they'll do one of two things: 
Either A):  they'll support you because many more people will buy the game and play it on linux
Or B):  tell you to stop and kill the project being the bastards they are.

Since this is only a mod and you are stating exactly what it is; they will probably just keep an eye on you and do nothing until they feel threatened for some obscure reason.  Many companies who make games that offer no support for mods choose B just to be slimy bastards whom everyone hates but patronizes them anyway because their games are actually pretty good.

---

### Post by donkyhotay on 2007-05-02
Blizzard is pretty smart and so long as stargus doesn't violate copyright laws blizzard isn't going to do anything since it will only increase starcraft sales. They didn't do anything against wargus which is technically worse since it was conflicting with warcraft:Bnet edition so I doubt they will do anything to stargus which isn't going to conflict with anything and possibly increase starcraft sales.

---

### Post by disturbedite on 2007-05-02
first of all entity, please do your research first.  i know what you're talking about, but i don't think you know enough about the history of these types of projects.

1.  wargus is still being actively developed despite freecraft.  explain that.
2.  wargus/stargus REQUIRE THE ORIGINAL CD.
3.  war2 is no longer supported by blizzard so that makes wargus' development "safer".
4.  blizzard's support of starcraft looks as if it will be dead after this next patch.

this is something to be happy about for now, so don't be a party pooper (i would have preferred a different term, but i know the forum rules ;)).

---

### Post by teddybairs1 on 2007-05-04
Hate to ask this, but why even bother? Both Starcraft and Broodwar run fine under wine.

---

### Post by nythacker on 2007-05-04
> **teddybairs1 said:**
> Hate to ask this, but why even bother? Both Starcraft and Broodwar run fine under wine.

Do you experience [COLOR="Blue"]slowness or choppiness[/COLOR] upon entering the in-game briefing menu in Starcraft using Wine? Do you have a fix for that?

Thanks!

---

### Post by Entity` on 2007-05-04
First of all, im not trying to be a party pooper, because Blizzard has shut down multiple efforts to remake the game for various efforts, including modding it for use with linux.  Second, I want you to continue what your doing in every way, because that would give me one more reason to abandon windows alltogether.  And third, I have never really used wine anyway, so this program would be highly useful in future endevors.  And last, wine doesn't play nice with battle.net anyway.

---

### Post by teddybairs1 on 2007-05-04
No, the game gets smoother and smoother with each successive version of WINE. Blizzard games are the ones I have the best luck with under WINE. Warcraft 2 works perfectly. I've never used the battle.net capabilities, but everything else seems to work just as it does under Windows.

---

### Post by disturbedite on 2007-05-04
> **teddybairs1 said:**
> Hate to ask this, but why even bother? Both Starcraft and Broodwar run fine under wine.

*** WHAT?!***  are you serious?  its NATIVE.  that means it has the potential to better and superior in every way to running it with wine.  sc does not run fine for everyone with wine.  (one minor example is that very annoying menu selection bug in campaign mode, you can't select which race you want to play as!).  it ran fine for me, but ever since the alsa driver "stuff" hit the fan (about 0.9.30-31) the blizzard games i play (d2+lod & sc) run at ~1-10 fps.  (like i said before, it doesn't affect *everyone* apparently, but it does affect a very large amount of users afaik).  we have to wait for the alsa driver to be rewritten.  (its a soc project).

asking why to run something natively vs running something with wine is like asking why should one buy a real rolex watch when you can buy a fake one on half of the new york street corners....

btw, you run war2 with wine? you should try wargus, its waaaaay better, i run it instead of using wine. give it a try if you want.

don't take this as an attack on you, but a rebuttal to your question.

> **Entity` said:**
> First of all, im not trying to be a party pooper, because Blizzard has shut down multiple efforts to remake the game for various efforts, including modding it for use with linux.  Second, I want you to continue what your doing in every way, because that would give me one more reason to abandon windows alltogether.  And third, I have never really used wine anyway, so this program would be highly useful in future endevors.  And last, wine doesn't play nice with battle.net anyway.

no offense taken.  i didn't mean any offense by my previous comment towards you, it just seemed a little bit overly negative in nature to me.  no harm no foul.  hope everyone will find it useful at some point, which i'm sure everyone will, assuming development continues.  (i like it already!)

---

### Post by teddybairs1 on 2007-05-04
I've got the battle.net edition. Wargus won't work with it. Never had a problem with it in WINE.

---

### Post by po0f on 2007-05-04
teddybairs1,

Did you bother checking the [homepage](http://wargus.sourceforge.net/) for Wargus?  They've explicitly stated it does not work with W2BNE.

---

### Post by disturbedite on 2007-05-05
@po0f
that is what he said.  i think you misread his post...

> **teddybairs1 said:**
> I've got the battle.net edition. Wargus won't work with it. Never had a problem with it in WINE.

ah, well that makes sense then, sorta.  you do know that wargus is online play capable right?

---

### Post by teddybairs1 on 2007-05-05
Thanks, yeah that is what I meant. I've known about wargus for a while, but all I could find was the battle.net edition so I never really tried it because I knew of wargus's problems with the .net edition. I'm not really into online gaming, I just enjoyed figuring out the campaigns.

po0f - your last post was a little rude. I know you probably didn't mean it that way, but it was. As a matter of fact, I looked at wargus' home page a couple of years ago when I was searching around to see what happened to the freecraft project (an unforgiveable sin by Blizzard if you ask me, it is an excellent Warcraft 2 parody).

I understand passionate opinions about favorite games and projects, but at the end of the day, it's still just 1s and 0s run through a processor, and not something to be rude about.

---

### Post by disturbedite on 2007-05-05
> **teddybairs1 said:**
> I'm not really into online gaming, I just enjoyed figuring out the campaigns.

same here!  i like playing online games, but i pretty much exclusively stick to single player for some reason...

> **teddybairs1 said:**
>  an unforgiveable sin by Blizzard if you ask me, it is an excellent Warcraft 2 parody.

i agree.  blizzard can be real a-holes.  thank the developers for wargus!  :guitar:

---

### Post by Ferrat on 2007-05-06
> **disturbedite said:**
> 
i agree.  blizzard can be real a-holes.  thank the developers for wargus!  :guitar:

True that Blizzard shut it down, but they could only do so more or less because of the name, there are many RTS games out there that remind you of StarCraft and Warcraft that was FAR from first I might add, the problem with Freecraft is the name and the fact that due to this Blizzard took an extra look in to the game engine of Freecraft and saw some of their own code which they could prove. 

And sure it's sad that Blizzard shut them down but Blizzard is a company that makes money and using their code is bad for business and any company would do the same, now Blizzard really aren't bad guys, they are good at what they do, they deliver what they say (even if it often takes longer then they have hope for) unlike other game companies Blizzard goes for quality instead of the quick buck. 
Blizzard has also show an intress in the Linux Community and even tried doing a Native Linux version for World of Warcraft, but they saw too many problems with the fact that Linux standards are somewhat lose and lacking and making it work for everyone would be extremly hard, time consuming and costly for the small community that is the Linux users, never the less they have looked in to it and hopefully they will again when linux is more the same over the board and not 1000 diffirent versions, because if blizzard (that has the cash and pull) goes in to the market serving games that play native on Mac, Win and Linux others will aswell.

---

### Post by Entity` on 2007-05-06
Right you are about Blizzard looking in and attempting a move with linux.  Quite a few new games today have linux support too.  And since linux is growing larger and larger with each passing year, game devs are thinking:  hey, this free, notably secure, open source operating system could very well be tomorrows future, so we got to start learning the ropes if we are to enter into this future prepared.  True Blizzard isn't nice, but you have to consider that the project it shut down was using Blizzard's code without permission.  The person who started this thread is just making a mod that would allow multi platform support.  Who knows, if blizzard likes it, they might adopt the mod as officially supported.  They may (they would be stupid if they don't) tinker with it to make it compatible with WoW and other games.  This may seem contradictory to what I said about running as fast as you can and not looking back, but this is just a best-case scenario.  I don't explain the worst-case scenario because it would not be conducive to this thread.  And everyone should know what the worst-case scenario anyway.

---

### Post by disturbedite on 2007-05-07
i wasn't aware that freecraft *actually contained blizzard code*.  but according to the wikipedia entry for stratagus/freecraft that *ISN'T* mentioned exactly:[LIST]
[*]On June [2003]("http://en.wikipedia.org/wiki/2003"), a [cease and desist letter]("http://en.wikipedia.org/wiki/Cease_and_desist_letter") was received from [Blizzard Entertainment]("http://en.wikipedia.org/wiki/Blizzard_Entertainment"), who thought the name *Freecraft* could cause confusion with the names *[StarCraft]("http://en.wikipedia.org/wiki/StarCraft")* and *Warcraft*, and that some of the ideas within the engine were too similar to *Warcraft II*. The project halted on [June 20]("http://en.wikipedia.org/wiki/June_20"), [2003]("http://en.wikipedia.org/wiki/2003").[/LIST]> **Entity` said:**
> The person who started this thread is just making a mod that would allow multi platform support.

i asked you guys to read my thread carefully, cuz i've mentioned *twice* that _i am not affiliated with the projec_t, i just made the thread to let all of you know about the project.  (make it three times ;)).

---

### Post by Entity` on 2007-05-08
> **disturbedite said:**
> i wasn't aware that freecraft *actually contained blizzard code*.  but according to the wikipedia entry for stratagus/freecraft DOESN'T mention that exactly:[LIST]
[*]On June [2003]("http://en.wikipedia.org/wiki/2003"), a [cease and desist letter]("http://en.wikipedia.org/wiki/Cease_and_desist_letter") was received from [Blizzard Entertainment]("http://en.wikipedia.org/wiki/Blizzard_Entertainment"), who thought the name *Freecraft* could cause confusion with the names *[StarCraft]("http://en.wikipedia.org/wiki/StarCraft")* and *Warcraft*, and that some of the ideas within the engine were too similar to *Warcraft II*. The project halted on [June 20]("http://en.wikipedia.org/wiki/June_20"), [2003]("http://en.wikipedia.org/wiki/2003").[/LIST]

Quote:
Originally Posted by Entity`  
The person who started this thread is just making a mod that would allow multi platform support. 

i asked you guys to read my thread carefully, cuz i've mentioned *twice* that _i am not affiliated with the projec_t, i just made the thread to let all of you know about the project.  (make it three times ;)).

I did read this thread carefully.  I did not say in any way that you were affiliated with blizzard.  I mearly stated what you were doing, and mods don't usually affiliate a person with the company in question.  So it is you who should read carefully now.  Still, when can we expect an update?

---

### Post by disturbedite on 2007-05-08
> **Entity` said:**
> I did read this thread carefully.  I did not say in any way that you were affiliated with blizzard.  I mearly stated what you were doing, and mods don't usually affiliate a person with the company in question.  So it is you who should read carefully now.  Still, when can we expect an update?

NO it is you that doesn't understand what i've said three times now.  i didn't make the mod.  i'm not associated with the stratagus project that is developing it.  i only made this post to let ppl know about the project.

so of course, i can't tell about the next version since i'm not associated with the project...

---

### Post by teddybairs1 on 2007-05-08
In other words Disturbedite is a project fan, not a project developer. S/He wants everyone to know about his/her favorite project as opposed to actually contributing to the project. Correct?

---

### Post by po0f on 2007-05-08
**disturbedite is not affiliated with either Stargus or Blizzard.**  Ok?  :)

[EDIT]

Stupid grammar...

---

### Post by disturbedite on 2007-05-08
> **teddybairs1 said:**
> In other words Disturbedite is a project fan, not a project developer. S/He wants everyone to know about his/her favorite project as opposed to actually contributing to the project. Correct?

yes, that is correct, cuz i am not a developer. 
(i will give you the benefit of the doubt and assume you weren't being a smartass about the last part of that comment).  lol

---

### Post by teddybairs1 on 2007-05-09
Which part? I wasn't trying to be a smart alec at all, just trying to clarify (as you were kind enough to do for me).

---

### Post by Frem on 2007-05-09
Question: If the StarCraft disk is required for Stargus (presumably because the resources are extracted from it), why is Wargus not compatible with the Warcraft II BNE?

Elaborating, wc2 BNE stores the game data in the same format as StarCraft, MPQ. If the MPQ files for StarCraft can be read, why hasn't Wargus been updated to allow the wc2 BNE disks to be used?

---

### Post by teddybairs1 on 2007-05-09
Developers resting on their laurels probably. Or else they're living in an ivory tower that hasn't gone past DOS into the 32-bit world.:lolflag:

---

### Post by disturbedite on 2007-05-09
> **teddybairs1 said:**
> Which part? I wasn't trying to be a smart alec at all, just trying to clarify (as you were kind enough to do for me).
no prob.  i was just referring to this part of the comment:
He wants everyone to know about his/her favorite project as opposed to actually contributing to the project.  ;)
i didn't know if you were being partly sarcastic or not, but as i said, i'd give you the benefit of the doubt.  but even if you were, it wouldn't matter...

> **Frem said:**
> Question: If the StarCraft disk is required for Stargus (presumably because the resources are extracted from it), why is Wargus not compatible with the Warcraft II BNE?

if you had read the rest of thread you would have seen i already mentioned why.  but its all good...
the reason why is cuz the developers have never bothered to implement support.  the developers are the same ppl that develop the core gaming engine; stratagus, some of them work on bos wars too i believe, stargus, & wargus.  so they have a lot on their plate.  i'm sure that if someone outside the project implemented it they'd be happy to include support for war2 bne.

plus, as teddybairs sorta said, the dos version didn't necessarily store the data the same way as the bne...

---

### Post by teddybairs1 on 2007-05-09
That is true, it doesn't. They store the data files under completely separate folders and file names. I did try playing with it once to point Wargus to a different directory on the disk, but it was a no-go.

---

### Post by disturbedite on 2007-05-09
i would have guessed that'd be highly unlikely to work if you had asked.  i believe you'd have to rewrite the paths that are searched.  stratagus (and hence wargus/stargus/boswars) is written in lua.

---

### Post by Frem on 2007-05-10
> **disturbedite said:**
> if you had read the rest of thread you would have seen i already mentioned why.  but its all good...
I have read the rest of the thread. The previous reason given was so vague that I assumed there was a deeper story behind it.

> **disturbedite said:**
> the reason why is cuz the developers have never bothered to implement support.
Wow, ya think?

> **disturbedite said:**
> plus, as teddybairs sorta said, the dos version didn't necessarily store the data the same way as the bne...
It doesn't matter, because Wargus never actually directly uses the original files, iirc. They had a converter program that rips apart data on the DOS disk and converts it to a new format.
MPQ support? It's just another converter program. If it works for Stargus, adding BNE support for Wargus would be utterly trivial, simply be a matter of changing the paths the program uses. For someone as familiar with the game as these guys, I'd say it would be the work of an hour, tops. Yeah, the stuff is stored under different file names. That's not a huge deal either, as I'm pretty sure that the structure would closely mirror that of StarCraft. Just a thought...

edit: Least I come off as a *complete* jerk, it might be worth mentioning that I have started work on modifying the conversion program for WarCraft II BNE. ;-)

---

### Post by disturbedite on 2007-05-10
[quote=Frem]I have read the rest of the thread. The previous reason given was so vague that I assumed there was a deeper story behind it.[/quote]
yeah, sorry about being vague, but thats the only reason given in the documentation or anywhere else i can find.

[quote=Frem]They had a converter program that rips apart data on the DOS disk and converts it to a new format.[/quote]
i don't think its exactly a converter, although i could be wrong, but i do know that it extracts the data, so its more like a decompressor/decoder for that/those particular format(s).

[quote=Frem] MPQ support? It's just another converter program. If it works for Stargus, adding BNE support for Wargus would be utterly trivial[/quote]
no doubt.  that was the first thought that occured to me when i found out about stargus.

[quote=Frem] edit: Least I come off as a *complete* jerk, it might be worth mentioning that I have started work on modifying the conversion program for WarCraft II BNE. ;-)[/quote]

lets try to keep it civil.  sorry if i've come off a bit testy on this thread, it just gets annoying some times when it seems like ppl don't read the entire thread so you have to repeat yourself.  but who cares, they're just words, a little typing never hurt anyone.  (aside from carpo-tunnel  ;))

but i am very glad to hear you're working on that.  of course we will find out whether it is simply a matter of rewriting paths or not.  (theoretically of course thats all that should be required).  (i'm sure you remember, but something to keep in mind is that the bne also includes the expansion).  i'm sure if it works that the developers would be happy to include a patch that introduces the support to the source tree.  good luck!

---

### Post by Entity` on 2007-05-11
Ooooooooooooooooooooooooooooooooooooooooohhhhhhhhhhhhhhhhhhhhhhhh.  I understand now.  Sorry my bad, we are correct now.

---

### Post by disturbedite on 2007-05-11
its all good.  no harm no foul.

---

### Post by n0.obAtroN on 2007-09-08
Hello, I am one of the devlopers of Stargus (n0.obAtroN). I am very pleased to say that the project is still active, and that we are making a release very soon. Stargus 0.2 will have many new and exciting features, so please show use your support and tell us what you think. My email is [email]wicked.goodlife@gmail.com[/email] Suggestions are most appreciated!

Now for the good stuff:

+ All of the Terran units have been added although not all of the features work yet
+  All of the Zerg units have been added although not all of the features work yet
+  Some of the Protoss units have been added
+  Sounds and music work
+  In-game menus are mostly finished
+  More complex Computer AI (its pretty hard)
+ Tilesets flags have been added although not all of the flags work yet (you cant walk over all terrain anymore)

- Campaigns do not work 
- Videos do not work
- Zerg larva + creep have not been added
- Most of Protoss units have not been added
- Protoss Shields have not been added
- Spells do not work
- In-game console needs some work (unit portraits, etc)

Visit [http://stargus.sourceforge.net/about.shtml]("http://stargus.sourceforge.net/about.shtml")

And[ http://stargus.sourceforge.net/sgscreenshots.html]("http://stargus.sourceforge.net/sgscreenshots.html")

---

### Post by cmat on 2007-09-08
thats good to read :)

---

### Post by Ferrat on 2007-09-09
Nice, keep up the good work, would be so great with a native engine

---

### Post by n0.obAtroN on 2007-09-10
I have opened a thread dedicated Stargus. Check it out at [http://ubuntuforums.org/showthread.php?t=547989&highlight=stargus]("http://ubuntuforums.org/showthread.php?t=547989&highlight=stargus")

---

### Post by n0.obAtroN on 2007-09-25
Hello Stargus fans! We are in need of a coder to hac...MODify the Stratagus Engine to better suport our needs. If you know C++ well and would like to help out contact me at [email]wicked.goodlife@gmail.com[/email]

ANY help is appreciated!!!

gl hf, n0.obAtroN

---

### Post by tym2die on 2009-04-17
how can i play my legal starcraft online with xubuntu?, i wine hq will not install battlenet it says wrong version plz help i cant live without sc

---

### Post by Jpardue on 2009-04-17
Thanks alot for the info, I definitely will be following this!

---

### Post by wsonar on 2009-04-17
Going to have to check this out that used to be one of my favorite games

---

