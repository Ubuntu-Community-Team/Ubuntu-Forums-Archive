---
title: "Calling all MTG players"
date: 2007-12-04
forum: Gaming &amp; Leisure
---

### Post by Psychoslim on 2007-12-04
Hello fellow Magic the gathering players.  I have been doing some google searching for a Unix/Ubuntu M:tg game that was current up to the newest set(free to play that is) I got this idea on a deck and would like some insite.  Thanx for your time. :)

---

### Post by JurB on 2007-12-04
check out sourceforge, there are some java MTG games that work on linux. Dunno if they are current...
I know you can run that old MTG game in wine.

---

### Post by Beren Camlost on 2007-12-04
Indeed, a quick search at sourceforge shows quite a lot of related projects, just look [here]("http://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=magic+the+gathering").

An interesting one I found so far is [Magic Collection Manager]("http://sourceforge.net/projects/magiccollection/"). It offers a collection manager and an online virtual duel battleground and is currently in beta. Will take a while to look through them all and test them though. 

Still have my most used decks boxed at my bedtable, and thousands of cards stored away, as much as I stopped collecting them around 5th Edition :D Hopefully more are willing to test some of these projects. A fully functioning client with capability of importing cards lists and online play would be sweet, and definately something that should be in the repositories :)

Edit:

[Apprentice 2.0]("http://sourceforge.net/projects/apprentice2/") - The open source continuation of Apprentice 1.0, and emulator used to play card games over the internet, and most commonly assosiated withMTG.
[Firemox]("http://sourceforge.net/projects/firemox/") - Play Magic: The Gathering over LAN, internet or against another player. Been in developement since 2003 and seems to have a very active community.

---

### Post by Psychoslim on 2007-12-04
Isn't there anything up to date?

I think that there maybe many ways to abuse [Cairn Wanderer]("http://ww2.wizards.com/Gatherer/CardDetails.aspx?name=cairn%20wanderer").

I have this idea for a rebel deck :guitar: anything with a converted mana cost of 3 or less to be put into play.

:lolflag:

---

### Post by sethvath on 2007-12-04
Good timing, I have the same MTG itch too. If anyone wants to play legacy (anything prior to stormhold) I'm game. 

I have no idea what abilities there are in the newer sets. Still have a blue/white counter, reb/black sligh and multicolored control deck somewhere.

---

### Post by Psychoslim on 2007-12-04
sadly for the cairn wanderer it can not have shadow :(

---

### Post by sethvath on 2007-12-04
5 mana for a 4/4 creature that spawns all abilities of dead creatures and you're still complaining? 

The newer creatures are grossly overpowered, there's a green+red 8/8 trampler with 5 casting cost. 1R: regenerate 1G: regenerate. Cant remember the name offhand.

---

### Post by Psychoslim on 2007-12-04
do you know what set its from?

---

### Post by sethvath on 2007-12-04
No.. only remember the image and that its a gold card. Could search the magic cards database on wizards.com

---

### Post by wounded on 2007-12-05
The Firemox archive seems to not work for linux? I get errors and can't decompress it. I've downloaded it four times on multiple mirrors :[ Is it just me?

---

### Post by sethvath on 2007-12-05
It works. Did you download the jar? Select your home directory and it will decompress it there. Do not specify /usr/local/bin unless you're running the jar with sudo as there will no doubt be a permissions error. 

If you have java 5 it will work, with java 6 I've some trouble getting it to use the 32bit java on a amd64 system.

---

### Post by joku_muko on 2007-12-06
Found this. No MP. Page in Italian, but program is multilingual.

[http://www.magmamagicmachine.it/](http://www.magmamagicmachine.it/)

Forgot to mention its for windows. Will have to try it with WINE.

---

### Post by wounded on 2007-12-06
> **sethvath said:**
> It works. Did you download the jar? Select your home directory and it will decompress it there. Do not specify /usr/local/bin unless you're running the jar with sudo as there will no doubt be a permissions error. 

If you have java 5 it will work, with java 6 I've some trouble getting it to use the 32bit java on a amd64 system.

No, I was downloading "firemox-0.95.52.0-bin.tar.gz" because that is the default download that comes up. That would not decompress. When I downloaded the JAR the install program ran fine and made a "Magic - Project" folder but the only relevant thing in there to run is a "run.sh" that just spits out an error (I've gotten two different errors from it across two seperate installations). Link me to what I need to download, because I am obviously too dim to find it myself.

---

### Post by kamahl on 2007-12-06
> **sethvath said:**
> 5 mana for a 4/4 creature that spawns all abilities of dead creatures and you're still complaining?

Almost all.  Personally, I'd like it to have banding, and if my opponent has it, islandhome. :P

---

### Post by sethvath on 2007-12-06
> **wounded said:**
> No, I was downloading "firemox-0.95.52.0-bin.tar.gz" because that is the default download that comes up. That would not decompress. When I downloaded the JAR the install program ran fine and made a "Magic - Project" folder but the only relevant thing in there to run is a "run.sh" that just spits out an error (I've gotten two different errors from it across two seperate installations). Link me to what I need to download, because I am obviously too dim to find it myself.
If you installed the jar that is fine. In the magic project folder, run starter.jar

I have trouble getting it to run with java 6, if you have java 5 try it. It might just be an issue because I'm using amd64.

---

### Post by sethvath on 2007-12-06
> **kamahl said:**
> Almost all.  Personally, I'd like it to have banding, and if my opponent has it, islandhome. :P
Banding is such an old school ability but I do like it. Island walk island home, whats the difference again?

---

### Post by TheInfamousTom on 2007-12-07
Islandwalk - Create is unblockable if defending player controls an Island.

Islandhome - Creature cannot attack unless the defending player controls an Island. If at any time you do not control an Island, sacrifice the creature.

So, Islandwalk doesn't require you to have islands and has no attack restrictions - just the unblockable bonus if the defender has an island. (Like every other walk)  Islandhome requires you to have islands, and can't attack unless the defending player has at least one island. (But it can still block even if they have no islands.)

The same rules apply to other basic land types:  (Mountainwalk, forestwalk, etc..)

---

### Post by h0ser81 on 2008-01-21
I too have been trying to get this thing to work and I can't. Every archive I download will not uncompress and the java installer works but then I can't launch the actual program.

---

### Post by yowshi on 2008-01-27
i cant get any of these programmes to work either.

firemox gives me this error when i use the starter.jar Exception in thread "main" java.lang.NoClassDefFoundError: gnu/classpath/tools/JavapMain

and the exe tells me i dont have java 1.5

---

### Post by xpan on 2008-03-13
Hi,

how can I learn to play MTG? 

How can I start to understand the rules and playing strategies?

---

