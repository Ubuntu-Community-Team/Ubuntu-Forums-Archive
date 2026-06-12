---
title: "hor requiring root access"
date: 2005-06-08
forum: Gaming &amp; Leisure
---

### Post by skelooth on 2005-06-08
[http://patrickavella.com/hor.shtml](http://patrickavella.com/hor.shtml) -> 2d sh'mup
[http://patrickavella.com/ballbuster.shtml](http://patrickavella.com/ballbuster.shtml) -> clanlib breakout game

both games written by me, and both are pretty damn cool :)

---

### Post by The Na Kun on 2005-06-08
[QUOTE=skelooth][http://patrickavella.com/hor.shtml](http://patrickavella.com/hor.shtml) -> 2d sh'mup
[http://patrickavella.com/ballbuster.shtml](http://patrickavella.com/ballbuster.shtml) -> clanlib breakout game

both games written by me, and both are pretty damn cool :)[/QUOTE]
 Okay, sure..

Yeah, this is going to sound really stupid, but I'm new to linux.  Alright, so, the alien game thing is the first game I got to work perfect with ./configure, make, and sudo make install.  So, how do I run the program?

---

### Post by skelooth on 2005-06-08
just type hor into the command line :)

I just ran it on ubuntu for the first time myself, and the performance was horrible, hopefully you'll have better luck with your GPU (SDL never liked my hardware set up for some reason).

---

### Post by The Na Kun on 2005-06-08
[QUOTE=skelooth]just type hor into the command line :)

I just ran it on ubuntu for the first time myself, and the performance was horrible, hopefully you'll have better luck with your GPU (SDL never liked my hardware set up for some reason).[/QUOTE]
 That just does nothing.. I wish I wrote down what it said.. But I forgot.. So yeah, I typed hor and it just spit 2 lines at me..

---

### Post by skelooth on 2005-06-08
tell me what those two lines where :)

I'm not sure but you MIGHT need to be root to run it. HoR was the first game I wrote, and I originally wrote it on windows, a friend ported it to linux for me.

Also for midis to work you need to have /dev/sequencer ... I don't have one of those :) but I believe installing tiMIDIty would work for music.

If you want to run ballbuster, just so you know, the clanlib in the synaptic package manager is VERY out of date. I've been trying to bug the author to get someone to update the deb package :)

Edit:

Yes, you need to be root to run HoR

---

### Post by The Na Kun on 2005-06-08
Well, when I do sudo hor and just hor, it give me something like this:
Copyright ...
Segmentation fault

What on earth does that mean?

---

### Post by skelooth on 2005-06-08
[QUOTE=The Na Kun]Well, when I do sudo hor and just hor, it give me something like this:
Copyright ...
Segmentation fault

What on earth does that mean?[/QUOTE]
 it would help if you copy pasted the full error :)

A segmentation fault can literally be ANYTHING. That is SDL's generic way of saying "something went awry".

It could be an issue with the version of SDL installed, an SDL library not installed, or user rights to access full screen mode.

IIRC it should only need sdl and sdlmixer, though I'm not entirely sure.

Try switching into root before running it. IE
> su
> ******
> hor

---

### Post by The Na Kun on 2005-06-08
Here is a screen shot (err, wrote it to a disk..):
[[IMG]http://img256.echo.cx/img256/2381/screenshot6wm.th.png[/IMG]](http://img256.echo.cx/my.php?image=screenshot6wm.png)
su doesn't work, nothing does... Help?

---

### Post by jdodson on 2005-06-08
no offense really.  but a game should not require root access unless it is running some sort of multi-player faculties, and even then, you dont need to require it.

i think this game is fairly suspect(trojan anyone?), or it is coded poorly.

i would recommend to everyone to not play this game until more information surfaces.

---

### Post by skelooth on 2005-06-09
[QUOTE=jdodson]no offense really.  but a game should not require root access unless it is running some sort of multi-player faculties, and even then, you dont need to require it.

i think this game is fairly suspect(trojan anyone?), or it is coded poorly.

i would recommend to everyone to not play this game until more information surfaces.[/QUOTE]

Excuse me? HoR was my first game written two years ago. If you have some kind of beef with it needing root access for full screen, then go grab the source code and fix it your self. How dare you accuse me of putting a trojan in a video game that's had over 100,000 downloads.

It was originally written for WINDOWS.

---

### Post by skelooth on 2005-06-09
[QUOTE=The Na Kun]Here is a screen shot (err, wrote it to a disk..):
[[IMG]http://img256.echo.cx/img256/2381/screenshot6wm.th.png[/IMG]](http://img256.echo.cx/my.php?image=screenshot6wm.png)
su doesn't work, nothing does... Help?[/QUOTE]

If you're still not getting it to work it's probably not worth the trouble. It compiles and runs just fine for me. I would say make sure you have SDL installed correctly... otherwise, I don't know why it's not working :) But if the poor performance I got in it is similar on other hardware set ups, then it's really not worth the trouble. It's very playable in redhat based distros and runs great in windows... I'll have to ask my friend on ubuntu if it runs okay on his box. Sorry about that.

---

### Post by jdodson on 2005-06-09
[QUOTE=skelooth]Excuse me? HoR was my first game written two years ago. If you have some kind of beef with it needing root access for full screen, then go grab the source code and fix it your self. How dare you accuse me of putting a trojan in a video game that's had over 100,000 downloads.

It was originally written for WINDOWS.[/QUOTE]

i am just saying a game that requires root access to play is suspect.  i am not saying it actually is, i am saying it is worth mentioning.  being a mod, i do have security and our users in mind.

just because something has been downloaded 100,000 times does not mean its not tampered with or legit.  tons of malware and spyware is popular, not saying your program is either of those things, however, popularity does not mean "free from ill intent."

again, i am just saying its suspect.  i meant it as a warning, people can download and run whatever they want.  

and thats fine it was written for windows, however the fact remains the game should not require root access to run.

---

### Post by skelooth on 2005-06-09
well then you need to go talk to the authors of SDL, since that is beyond my control. Are you going to tell people not to download my other game because it requires a version of clanlib that's not in the repository? That is extremely rude to accuse me of trying to install trojans on people's computers. As a mod you do not need to SLANDER my software. It was my first game written 2 years ago, it has a couple of bugs on non windows system and the source code is a mess, I would appreciate it if you would not slander it.

It can be found on MANY many main stream gaming sites including megagames, gamehippo, tucows, happypenguin.org and more. If it had a trojan, or if it was suspect, I dont think they'd have reviewed and linked to it.

---

### Post by jdodson on 2005-06-09
[QUOTE=skelooth]well then you need to go talk to the authors of SDL, since that is beyond my control. Are you going to tell people not to download my other game because it requires a version of clanlib that's not in the repository? That is extremely rude to accuse me of trying to install trojans on people's computers. As a mod you do not need to SLANDER my software. It was my first game written 2 years ago, it has a couple of bugs on non windows system and the source code is a mess, I would appreciate it if you would not slander it.

It can be found on MANY many main stream gaming sites including megagames, gamehippo, tucows, happypenguin.org and more. If it had a trojan, or if it was suspect, I dont think they'd have reviewed and linked to it.[/QUOTE]


again, i dont know anything about your game.  however, i have tons of games that were written with those libraries that do not require root access to run.  

i am not saying your software IS malware, i am saying i would caution people in using it when the normal operation of a single player game requires root access.

---

### Post by skelooth on 2005-06-09
[QUOTE=jdodson]again, i dont know anything about your game.  however, i have tons of games that were written with those libraries that do not require root access to run.  

i am not saying your software IS malware, i am saying i would caution people in using it when the normal operation of a single player game requires root access.[/QUOTE]

Well, I don't know why it won't run unless you're root. Oh well. In 2 years, and after being reviewed on serveral high traffic websites, not only are you the only one to complain, but the only one to 'warn' people about my software. Rude. All I was doing was posting my games to help add to the community. You make me sorry I did.

---

### Post by jdodson on 2005-06-09
[QUOTE=skelooth]Well, I don't know why it won't run unless you're root. Oh well. In 2 years, and after being reviewed on serveral high traffic websites, not only are you the only one to complain, but the only one to 'warn' people about my software. Rude. All I was doing was posting my games to help add to the community. You make me sorry I did.[/QUOTE]

i dont know why it will only run as root either.  

it is normal to run in admin mode the entire time in a windows session, that is why windows security is lame.  normal user software (unless it is installing system files, or programs or changing something system wide) should not require root access(this is the unix security model, and it is a good model, however some linux distros devate from this, lindows for example.  MANY people feel that is a lame model.).  this is the model of unix security that has been around for many, many years.  if this is "rude" then so be it, i dont care.  my first duty is to the users of this forum, so when something is out of place i feel it my job to tell them.  

this is one of those instances.  

again, i meant no disrespect to your software.  it just raises a flag when a game requires root access to run.

---

### Post by skelooth on 2005-06-09
[QUOTE=jdodson]i dont know why it will only run as root either.  

it is normal to run in admin mode the entire time in a windows session, that is why windows security is lame.  normal user software (unless it is installing system files, or programs or changing something system wide) should not require root access(this is the unix security model, and it is a good model, however some linux distros devate from this, lindows for example.  MANY people feel that is a lame model.).  this is the model of unix security that has been around for many, many years.  if this is "rude" then so be it, i dont care.  my first duty is to the users of this forum, so when something is out of place i feel it my job to tell them.  

this is one of those instances.  

again, i meant no disrespect to your software.  it just raises a flag when a game requires root access to run.[/QUOTE]
 Fair enough. I just couldn't help but feel a little bit attacked by the way you worded your post. I understand where you're coming from.

Just to drill in. There is no trojans, spyware, adware, or any type of unwantedware in any of my programs.

---

### Post by The Na Kun on 2005-06-09
So, help on how to play the game would be nice...

---

### Post by senectus on 2005-06-09
[QUOTE=The Na Kun]So, help on how to play the game would be nice...[/QUOTE]
Make it executable (right click and properties or chmod +x filename) then double click it.
not too hard.

---

### Post by skoal on 2005-06-09
[QUOTE=skelooth]Oh well. In 2 years, and after being reviewed on serveral high traffic websites, not only are you the only one to complain, but the only one to 'warn' people about my software. Rude. All I was doing was posting my games to help add to the community. You make me sorry I did.[/QUOTE]

Nah, I doubt Mr. Dodson was the first one to point that out about needing to run root.  You should take his concern and advice as concern for this community, first and foremost.  The fact you find his WARNING to the community about the "necessity to run the game as root" as trivial or rude, raises more concerns and objections (at least in my mind) about your game.

Quite frankly, I find it questionable that anyone who knows how to program anything on Linux would have difficulty in understanding something so basic as root priveleges.  

\\//_

---

### Post by The Na Kun on 2005-06-09
Alright now, I don't really want to make a topic, so I'll just post this here.  As you might have seen, I spent over an hour downloading scourge, but I can't play it.  It goes till it says I need openGL.. Where do I download the driver?  I have an intel 82865G integrated graphics controller, so where do I download?  I think that their download was for like, just ww.  Please, I spent so much time downloading junk for that game, help would be nice...

---

### Post by skelooth on 2005-06-10
[QUOTE=skoal]Nah, I doubt Mr. Dodson was the first one to point that out about needing to run root.  You should take his concern and advice as concern for this community, first and foremost.  The fact you find his WARNING to the community about the "necessity to run the game as root" as trivial or rude, raises more concerns and objections (at least in my mind) about your game.

Quite frankly, I find it questionable that anyone who knows how to program anything on Linux would have difficulty in understanding something so basic as root priveleges.  

\\//_[/QUOTE]

Quite frankly, I find it questionable that anyone of even moderate intelligence would try to rekinder the flames of a dead arguement. It was my first game written TWO YEARS AGO FOR WINDOWS, and *I* am not the one who ported it to linux. Don't open your mouth and spew garbage when you a) have no place in the conversation, and b) are radiating your amazing ability to pick and choose what you read for the sole purpose of trolling.

It is a dead arguement, and has already been settled. I really don't care who you are, or how long you've been posting on this forum, you are a simpleton troll.

January 2004: [http://happypenguin.org/show?Heroes%20of%20Roswell%20%28HOR%29](http://happypenguin.org/show?Heroes%20of%20Roswell%20%28HOR%29)
not a single complaint


[http://www.google.com/search?hl=en&lr=&c2coff=1&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=heroes+of+roswell&btnG=Search](http://www.google.com/search?hl=en&lr=&c2coff=1&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=heroes+of+roswell&btnG=Search)
After 100,000 downloads and being listed on tons of sites, for something so 'suspect', you'd think someone would have said something earlier? Of all my friends who run linux, you'd think one of them would have said "Hey skel, that's not right" ? I'm not saying it's "okay" that it needs root privlages, i'm saying you're being a pompous moron by attacking me about it.

---

### Post by skoal on 2005-06-10
[QUOTE=skelooth]Quite frankly, I find it questionable that anyone of even moderate intelligence would try to rekinder the flames of a dead arguement.[/QUOTE]
Whoa! Remember to take deep breaths and exhale while typing.  Two people raise concern about you giving out *poor* advice to run a game as root, and yet you persist.  Why?

In reality, I think you give me too much credit.  "Moderate" intelligence actually sounds quite flattering.  I don't get too many replys like these.  In fact, I need more.  I got a fever for more flames, and the prescription is more cowbells.

\\//_

---

### Post by jdodson on 2005-06-10
skelooth,

i can tolerate you telling me to f off, even though you are violating the ubuntu code of conduct, something to which you agree to when you sign up for this forum.  however, if you continue to attack the people of this forum when qthey uestion your game, i will confer with other moderators to take action against you as a user of this forum.  

i understand you are upset.  i understand people questioning your work is not fun.  i write games, if someone had a beef with them it would in some way be a slap against me.  however, if you spend time in the unix world, it should be no surpsie that games should not require root access to run.  however, i really, REALLY dont want to get into this argu,ment again.  

i have split this jaunt off of my uber games list.  it is not what the orginal thread was about.  do _NOT_ take this discussion back into that thread.

---

### Post by mike998 on 2005-06-10
Skelooth :  You need to calm down a little.  I read this thread before (when it was part of the uber list), and far from being offended by jdodson et al's remarks, I was offended by yours.
One of the first things that you can read on the 'net about the root (or superuser) account is that it shouldn't be used for trivial things such as playing games.  Why not take the advise here to heart and look to see if you can adjust your game to be playable by a regular user?
I don't think that playing it full screen requires root access, as I am able to play half-life under cedega full screen and also I can play a number of other games (frozen bubble, unreal tournament, alpha centauri) full screen with out any problems.  Unfortunately, I'm not a programmer, and as such can't really help you beyond encouraging you to make these adjustments.

---

### Post by The Na Kun on 2005-06-10
Alright, can someone please help me in both the areas.  I'm sorry and all, but scourge was a 1hour 35 minute download (I think) and I really want to play it.  Also, chmod +x path:to:hor didn't work, it gives me the same error.  I don't know how I could have installed SDL wrong, there was no errors and all...  Sorry for my lack of patience.

---

### Post by jdodson on 2005-06-10
[QUOTE=The Na Kun]Alright, can someone please help me in both the areas.  I'm sorry and all, but scourge was a 1hour 35 minute download (I think) and I really want to play it.  Also, chmod +x path:to:hor didn't work, it gives me the same error.  I don't know how I could have installed SDL wrong, there was no errors and all...  Sorry for my lack of patience.[/QUOTE]

in the root of the gaming section i have created a thread called "steps to getting 3d working."  check that thread out for info on how to get 3d working.... novel.  anyways, sorry for no link, i am on a SLOWWWWW 28.8 modem connection....

---

