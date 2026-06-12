---
title: "What is Game quality like in ubuntu?"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2006-10-01
Hi all, i finally got fglrx working and was going to try to put some games on my linux machine....i have a few questions first...will the games run as fast as in window's? I will install Doom 3 and Doom 3 Resurection of evil which i know can run nativly after being patched...what is the quality like...i have been told that they run slower in linux then in windows..is this true? I will also install Steam and a whole bunch of games made by Valve that run with steam...what do the steam games run like? Note i will be running steam and windows games with Wine....what is the quality like? Are the graphics up to par? Also, i have not yet put XGL on my machine yet (note i am running edgy beta 1) but i have put on beryl and was planning on putting on XGL...will i run into any issues while gaming...O and i am certainly going to put on Americas army and True Combat Elite on :)

P.S: is there any good open-source FPS? Thanks.
P.S.S: How do you run your Windows games? Just Wine, Cedega (which costs $ and i try to support opensource and free only), or crossover (which also costs $). What do you find they (crossover and Cedega) do for you? do the games run faster? i was just wondering even tho i have my mind set on Wine.

---

### Post by Linkiboy on 2006-10-01
I just installed Steam and it runs better on Linux than it does on my spyware-filled Windows.

---

### Post by =Kevin= on 2006-10-01
As far as I know, if games can be played natively they run just as fast as in Windows, or even faster (for example:ut2004 runs much faster for me @ ubuntu). 

If you use wine to play games you will lose some quality because you need to emulate something (not quite sure what, I think the directx layer??).

Anyway, games as Unreal Tournament,doom 3, tc:elite run fine for me :)

-Kevin

---

### Post by rekahsoft on 2006-10-01
hmm...i thaught wine is not an emulator? so what is it emulating...i have also head that the wine shaders are not up to the current direct X version yet so you loose some quality there. Is that correct? Also what is the difference between products like Cedega and crossover? BTW i would never buy Cedega because it can hurt WINE development...buying crossover is a good idea because it is like supporting the WINE project (because Codeweavers back WINE and crossover is basicly a front end for wine). Am i right?

---

### Post by strikeforce on 2006-10-01
You are right they aren't up to current direct X shaders however they are significantly better than what they used to be.

[http://wiki.winehq.org/DirectX-ToDo](http://wiki.winehq.org/DirectX-ToDo)

That link will provide you with how much is done regarding Direct X

---

### Post by rekahsoft on 2006-10-01
> **strikeforce said:**
> You are right they aren't up to current direct X shaders however they are significantly better than what they used to be.

[http://wiki.winehq.org/DirectX-ToDo](http://wiki.winehq.org/DirectX-ToDo)

That link will provide you with how much is done regarding Direct X
ok..nice to know...anybody got anymore answers to my ?'s above and opinions about linux gaming. Thanx

---

### Post by skymt on 2006-10-01
Using XGL is not advised if you're a gamer. You need some special hacks to get reasonable framerates.

Wait for Edgy, when XGL won't be needed.

---

### Post by rekahsoft on 2006-10-01
Why won't XGL be needed? AIGLX? becuse fglrx does not support AIGLX!!

---

### Post by Pyr3 on 2006-10-01
> **=Kevin= said:**
> As far as I know, if games can be played natively they run just as fast as in Windows, or even faster (for example:ut2004 runs much faster for me @ ubuntu). 

If you use wine to play games you will lose some quality because you need to emulate something (not quite sure what, I think the directx layer??).

Anyway, games as Unreal Tournament,doom 3, tc:elite run fine for me :)

-Kevin

If you do install any of the Unreal Tournaments (namely 2003, 2004) patch them right after install.

I had the same memory leak problem with them in Linux that I did in Windows after installing... kind of odd, but it works properly now.

If you use something like IceWM or a really simple window manager, you can squeek out a few more FPS.

I do notice however, that Unreal runs about 15% better on Linux then Windows.

---

### Post by billyfoxtrot on 2006-10-02
I play Quake 4 and Doom 3 and they run very well.  I never played them on Windows (I was a Mac guy before I switched to Ubuntu), so I can't really compare it to that.  But I can run them on the High setting without any problems.  Just make sure you have your graphics card set up correctly.  I've also installed Steam with Cedega, and though Half-Life 1 runs fine, I've had some problems with Half-Life 2.  I think it's my graphics card driver.  For some reason, no text is displayed on any of the menus.  I could try installing the latest drivers from nVIDIA, but I've been too busy lately to mess around with that. :) 

Overall, I've been very happy with my experience with Ubuntu and gaming.  But then again, I'm not a really big gamer, so I may not be the best judge.

---

### Post by Lord Illidan on 2006-10-02
fglrx might not give you as good performance as on Windows..since OpenGL is better suited to NVIDIA cards.

As for open source FPS, try Tremulous and nexuiz.

---

### Post by bastiegast on 2006-10-02
> **Pyr3 said:**
> 
If you use something like IceWM or a really simple window manager, you can squeek out a few more FPS.

OR, just dont use a window manager :) something like this:
*hit ctrl-alt-f1*
sudo killall gdm
X :1.0
*ctrl-alt-f1 again to switch back to your commandline*
export DISPLAY=:1.0
ut2004 or any other game

---

### Post by skymt on 2006-10-02
> **rekahsoft said:**
> Why won't XGL be needed? AIGLX? becuse fglrx does not support AIGLX!!

It will.

---

### Post by rekahsoft on 2006-10-02
> **skymt said:**
> It will.
what will you do?

---

### Post by skymt on 2006-10-02
> **rekahsoft said:**
> what will you do?

Nothing. I have an nVidia card.

I'm sure fglrx will be updated with the relevant changes eventually. Then it will run AIGLX, and there will be much rejoicing throughout the land.

---

### Post by rekahsoft on 2006-10-02
what does AIGLX have that XGL doesn't? What makes it better?

---

### Post by Perfect Storm on 2006-10-03
Correct me if I'm wrong (I'm not into those nauseous eyecandy, I get ill watching it ;) )

XGL is a "layer" (some call it a big ugly hack) run above xorg so it's consuming more horsepower from your computer, where AIGLX is intergrated into xorg.

---

### Post by rekahsoft on 2006-10-03
> **Artificial Intelligence said:**
> Correct me if I'm wrong (I'm not into those nauseous eyecandy, I get ill watching it ;) )

XGL is a "layer" (some call it a big ugly hack) run above xorg so it's consuming more horsepower from your computer, where AIGLX is intergrated into xorg.

yes that is right...XGL is a OpenGL layer on top of X...where as AIGLX is integrated into X and wants to "improve it incrementally" to moderize it. You can read more about XGL at [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl) and about AIGLX at [http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX)

---

### Post by 1oki on 2006-10-03
> **rekahsoft said:**
>  Also what is the difference between products like Cedega and crossover? BTW i would never buy Cedega because it can hurt WINE development...buying crossover is a good idea because it is like supporting the WINE project (because Codeweavers back WINE and crossover is basicly a front end for wine). Am i right?

so is Cedega...

---

### Post by justin whitaker on 2006-10-03
> **rekahsoft said:**
> Hi all, i finally got fglrx working and was going to try to put some games on my linux machine....i have a few questions first...will the games run as fast as in window's? I will install Doom 3 and Doom 3 Resurection of evil which i know can run nativly after being patched...what is the quality like...i have been told that they run slower in linux then in windows..is this true? 

Not on my machine. I had a helluva time getting Quake 4 audio to work right though.

> I will also install Steam and a whole bunch of games made by Valve that run with steam...what do the steam games run like? Note i will be running steam and windows games with Wine....what is the quality like? Are the graphics up to par? 

I got better frame rates on Ubuntu with Cedega than on XP. Quality is comparable to XP. Some mods work, others do not, but other than that, no real issues.

> P.S: is there any good open-source FPS? Thanks.

Nexuiz, Tremulous, Open Arena. All based off various Quake engines, all quite good. 

> P.S.S: How do you run your Windows games? Just Wine, Cedega (which costs $ and i try to support opensource and free only), or crossover (which also costs $). What do you find they (crossover and Cedega) do for you? do the games run faster? i was just wondering even tho i have my mind set on Wine.

That's a religious question, I think.  :mrgreen: 

Some people really hate Cedega, because they cannot give all their code back: they include proprietary DRM code to get games to run. And in the past they did not share much with the WINE developers. 

That, to me, is a philosophical issue. They are a business, they try to comply with the GPL as they can. Much of their work with Direct X has been shared according to the lead developer....

It works, and works well on the supported titles. The really nice thing about it is that you don't have to tweak the games manually (usually, or much, depends on the game)-the GameDB chooses the proper settings for you. 

Crossover office does run games as well, but it's not their focus: they want office applications to run, and games tend to be a side benefit. They work very closely with WINE, so it tends to get a pass from WINE purists.

You can also run games via WINE. Steam titles have been made to run, as have World of Warcraft, and others, with some tweaking. WINE doesn't hold your hand, you have to get your hands dirty in the config files. It's free, however, so it's not all bad. Direct X is coming along, and in some cases, surpasses Cedega.

Up to you, really. :mrgreen:

---

### Post by rekahsoft on 2006-10-03
> **justin whitaker said:**
> Direct X is coming along, and in some cases, surpasses Cedega. :mrgreen:
What do you mean by that?

---

### Post by rekahsoft on 2006-10-03
> **skymt said:**
> Nothing. I have an nVidia card.

I'm sure fglrx will be updated with the relevant changes eventually. Then it will run AIGLX, and there will be much rejoicing throughout the land. I just read that fglrx already has support for AIGLX extenstions (i read it [here]("http://en.wikipedia.org/wiki/AIGLX") under the deployments section)...maybe i am wrong but can i run AIGLX with my Radeon 200M and fglrx???

---

### Post by justin whitaker on 2006-10-03
> **rekahsoft said:**
> What do you mean by that?

The core issue with WINE has always been that it does not handle DirectX that well-that's what allowed Transgaming to step in. 

The WINE team has been hacking away, and I've seen reports that Steam, WoW run better, with better framerates, and better resolution, than with Cedega. 

Take a look at the Transgaming forums.

---

### Post by gigiya on 2006-10-07
The only game I've played so far has been CSS with wine, and the framerates are much, much worse than on XP.  FPS drops drastically every time you shoot or any other sound is heard.  It's unplayable while it ran fine on Windows with even higher graphics settings.

---

### Post by bastiegast on 2006-10-07
> **gigiya said:**
> The only game I've played so far has been CSS with wine, and the framerates are much, much worse than on XP.  FPS drops drastically every time you shoot or any other sound is heard.  It's unplayable while it ran fine on Windows with even higher graphics settings.

I had the same with a geForce 6800, if you tweak some stuff it might run decent, read this: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam")

---

### Post by gigiya on 2006-10-07
> **bastiegast said:**
> I had the same with a geForce 6800, if you tweak some stuff it might run decent, read this: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam")

That's the howto I used to get it running.

---

### Post by haxer on 2006-10-07
I think all people prefer this as long as you got your video card drivers installed 


wget [http://steam4linux.freepages.dk/down...a/download.php](http://steam4linux.freepages.dk/down...a/download.php)

Then write tar xvfz steam4linux.tar.gz

then type in

cd steam4linux
./configure


Then run it and then when it freezes on 26% type in

WINEPREFIX="$HOME/.steam4linux" wine "C:/Program Files/Steam/steamTmp.exe" SelfUpdate "C:/Program Files/Steam/Steam.exe" "14"

---

### Post by NoTiG on 2006-10-07
[http://www.phoronix.com/scan.php?page=article&item=357&num=1](http://www.phoronix.com/scan.php?page=article&item=357&num=1)
[http://www.phoronix.com/scan.php?page=article&item=359&num=1](http://www.phoronix.com/scan.php?page=article&item=359&num=1)

Basically if you have an nviidia card... expect similar framerates as to what you will get in windows (some better... some worse)

If you have an ATI card, expect about 1/2 to 3/4 the fps as you get in windows... with the binary driver. with the open source driver its about half the binary . so around 1/4th.

---

### Post by haxer on 2006-10-07
Ive got an nvida  card setup up with the right drivers and it works the same as in windows :) ;) :rolleyes: :-k :p :cool:

---

### Post by rekahsoft on 2006-10-09
WOW that is apsolutly horable!!! Something has to be done about that!!

---

