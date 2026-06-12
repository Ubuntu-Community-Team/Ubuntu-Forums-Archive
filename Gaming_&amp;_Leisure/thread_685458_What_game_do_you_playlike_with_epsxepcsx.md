---
title: "What game do you play/like with epsxe/pcsx ?"
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-02-02
Hi, 
What game do you play/like with epsxe/pcsx ?
[http://packages.dfreer.org/](http://packages.dfreer.org/) 
  
 
Btw,I favour Mario or Zelda like games in general. Is there some like for psx?

---

### Post by fain on 2008-02-02
Final Fantasy 7, It is the best game for the psx imo. As for a mario64 style game you could try spyro its pretty good.

---

### Post by DoktorSeven on 2008-02-02
Castlevania: Symphony of the Night.  I don't care much for FFVII.

Also, try Jumping Flash!.

Edit: and I still stand by my opinion that no matter how much easier pSX is to configure and run, ePSXe still works many times better than it does regardless of its age.

---

### Post by acoustibop on 2008-02-02
To be quite honest, I don't find playing with these emulators very rewarding.  However, if you include [pSX Emulator]("http://psxemulator.gazaxian.com/") - the best of the lot, and the easiest to install and run - in the list (any reason why you didn't?), I'd say

Chrono Cross
Tales of Phantasia (which I only just started playing as a [good translation patch]("http://www.crosser.altervista.org/forums/index.php?showtopic=124") has just become available)
Wild Arms
Alundra
Final Fantasy VII

are my top 5.

---

### Post by BigSilly on 2008-02-02
Acoustibop's PSX emulator is excellent. I can attest to that!

I've been playing Castlevania Symphony of the Night, and also a little known NiGHTS-alike called Klonoa: Door to Phantomile. Great games worth a look I'd say.

---

### Post by acoustibop on 2008-02-02
Hey, it's not my emulator, BigSilly!  It's entirely developed by pSX Author.  I just think it's a great emulator! :P

---

### Post by themacmeister on 2008-02-02
Klonoa: Door to Phantomile. (by Namco)

It is a 3D platformer, but played in 2D and the scenery rotates around the player.

If you can get past it's cutesy story and graphics, you will discover a very enjoyable platformer, that will thrill and frustrate the most hardened game player.

---

### Post by acoustibop on 2008-02-02
Yes, it's something that's quite noticeable about Japanese-made console games, themacmeister - they're often very 'cutesy,' but are nevertheless still good, solid games.  If people worry about these games being 'cutesy,' they're just going to miss out on some great fun ;)!

---

### Post by disturbedite on 2008-02-02
certainly imho pSX is the best playstation emulator.

there'd be too many games i like playing to list if i tried.

---

### Post by acoustibop on 2008-02-02
Hm, I'm not sure the OP didn't mean to include pSX Emulator - his link points to dfreer's repository, which includes pSX but not ePSXe or PCSX.

@DoktorSeven:  We've had this discussion before: I'll accept that you find that ePSXe runs better for you (I don't know why - it shouldn't), but I think you should accept that, for most people and their systems, pSX works far better than ePSXe. :)

---

### Post by Dark Aspect on 2008-02-02
> **frenchn00b said:**
> Hi, 
What game do you play/like with epsxe/pcsx ?


Silent Hill
Final Fantasy 7
Resident evil 1-3

Those are actually the only games I have played on ePSXe,odd for me to own PS1 games but never to have owned a real PS1 console.

---

### Post by frenchn00b on 2008-02-03
> **acoustibop said:**
> Hey, it's not my emulator, BigSilly!  It's entirely developed by pSX Author.  I just think it's a great emulator! :P

This one could be promising, then, but you'd have any idea what may be wrong here ?
```

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or dire
```

---

### Post by DoktorSeven on 2008-02-03
> **frenchn00b said:**
> This one could be promising, then, but you'd have any idea what may be wrong here ?
```

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or dire
```

```
sudo apt-get install libgtkglext1
```

---

### Post by acoustibop on 2008-02-03
Yes, libgtkglext is normally the only extra library that is needed to run pSX in Ubuntu.  Thanks for that, DoktorSeven! ;)

---

### Post by disturbedite on 2008-02-03
yeah, the answer is right in front of you man.

---

### Post by frenchn00b on 2008-02-04
well ...
final fantasy VI:
no way
  
-epsxe crashes:
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
I installed 
libstdc++6 libgtkglext1
 
  
- pSX, well, it is laggy as hell with the sound:
sound : underrun
and ok, I give up this software or trying
  
  
- pcsx looks the very best : 
smooth and sound working very well 
but no fullscreen.
  
How can it be possible that all linux apps are not working ? Is it better with Windows and those emulators ?
  
Greetings to linux community

---

### Post by acoustibop on 2008-02-04
pSX works extremely well in Linux for most people, frenchn00b.  In fact, I'm not sure it doesn't run even better than in Windows.

If you're getting the sound lagging and the Sound: Underrun error, try increasing the values for the Latency sliders on the Sound tab - but not too much, as this is basically a delay; too much and the sound will go out of sync.  This is due to the inherent high latency for sound in most Linux kernels: if you have a soundcard that tends to have a high latency itself, this problem will be exacerbated.

What sort of system are you running - particularly, what soundcard - and which version of Ubuntu?

---

### Post by disturbedite on 2008-02-04
> **frenchn00b said:**
> How can it be possible that all linux apps are not working ? Is it better with Windows and those emulators ?
thats not the case, its a problem on your end.  it works fine for almost everyone if you have sufficient hardware & have it set up right.

---

### Post by frenchn00b on 2008-02-04
> **acoustibop said:**
> pSX works extremely well in Linux for most people, frenchn00b.  In fact, I'm not sure it doesn't run even better than in Windows.

If you're getting the sound lagging and the Sound: Underrun error, try increasing the values for the Latency sliders on the Sound tab - but not too much, as this is basically a delay; too much and the sound will go out of sync.  This is due to the inherent high latency for sound in most Linux kernels: if you have a soundcard that tends to have a high latency itself, this problem will be exacerbated.

What sort of system are you running - particularly, what soundcard - and which version of Ubuntu?
 
it is an old crap sound card. something like ...[https://www.bettertelecom.com.au/zencart/images/Compaq%20EVO%20v1.jpg](https://www.bettertelecom.com.au/zencart/images/Compaq%20EVO%20v1.jpg)
pentium III

---

### Post by disturbedite on 2008-02-04
> **frenchn00b said:**
> it is an old crap sound card. something like ...[https://www.bettertelecom.com.au/zencart/images/Compaq%20EVO%20v1.jpg](https://www.bettertelecom.com.au/zencart/images/Compaq%20EVO%20v1.jpg)
pentium III
well then, i think you proved the point i made in the previous post.

you could get a new soundcard.  they're pretty inexpensive if you buy online...
i'd recommend newegg.com.

---

### Post by frenchn00b on 2008-02-04
> **disturbedite said:**
> well then, i think you proved the point i made in the previous post.

you could get a new soundcard.  they're pretty inexpensive if you buy online...
i'd recommend newegg.com.

ahhhhhh 
I actually got lot of troubles with it.

you were right if i kick away this sound card, the final fantasy VII runs !!
The cpu is loud, on the other hand, and I guess that Pentium III does not like it.

weird since pcsx could run the sound and in smaller window, no fullscreen, and it runned smoother. well I dont know more up to now... still trying ..

I think the only final fantasy that i will have possibitly with that machine to play will be final fantasy V, only. :( :(:(:(

nice website 
thank you

---

### Post by frenchn00b on 2008-02-05
I am working on it. 
epsxe has no fullscreen.
  
pSX is hence the only way to make it psx to work for me.
I got this
```
 ./pSX
Segmentation fault
```

where can I find the source code to compile it for my machine ?
thanks

---

### Post by heatblazer on 2008-02-05
I am using ePSXe on the WinXP. I have successfully installed the Pete O`Deel OGL pixel shadres and now I am playing old games with incredible... I have to repear I-N-C-R-E-D-I-B-L-E graphics. For witness let me show you the site where I got that:
[http://planetemu.net/index.php?section=articles&id=293](http://planetemu.net/index.php?section=articles&id=293)
Take a look and have a good time. Right now I am playing "Tales Of Destiny II" it`s an incredible game!

---

### Post by acoustibop on 2008-02-05
The source for pSX isn't available, frenchn00b.

pSX is, in fact, much more dependent on a decent soundcard than a videocard.  That may have to do with the reason for your problem.  What is the soundcard?  in fact, what sort of machine?  I asked you before and you just made a very vague reference to a Compaq Evo.  I'm beginning to suspect your problem is that you're trying to run applications on a machine that's just too old for the perfect results you seem to be expecting.

@heatblazer: most people would get [ePSXe]("http://www.epsxe.com/") and [Pete Bernert]("http://www.pbernert.com/")'s (Pete O'Deel??) plugins from the official pages.

And this is a Ubuntu forum, not Windows.

I have to say, though, ePSXe' enhanced graphics are *not* incredible for me.  Once you start playing an accurate emulator like pSX, you start realising just how much enhancement distorts the game.

I played Playstation games on ePSXe for 5 or 6 years and enjoyed it very much, but when pSX Emulator came out, even the imperfect first version was enough to make me realise ePSXe just wasn't in the game any more.  It's no coincidence, I think, that the two Playstation emulators still in active development (pSX and Xebra) both aim at accuracy rather than enhancement.

Xebra is Windows only, so you may want to try that - it's supposed to be extremely good, if hard to understand.

---

### Post by Zzzach on 2008-02-05
For playstation one the best games that I've played (so far) are Gran Turismo 2, Street Fighter EX 2, Street Fighter Alpha 3, Puzzle Fighter 2, Castlevania SOTN, Metal Slug X, Tekken 3, Test Drive 2 4x4, Initial D, Need 4 Speed High Stakes... There are still quite a few games I haven't played yet though. Those are my favorite of the ones I've played. :guitar:

---

### Post by Python88 on 2008-02-06
When I had epsxe on Windows XP I constantly played Medievil, Final Fantasy 7 and Destruction Derby. 
I have to download epsxe again to play those games because I miss the emulator.

---

### Post by acoustibop on 2008-02-06
Well, of those games, Python88, Final Fantasy VII certainly plays much better in pSX than it ever did in ePSXe.  The others, I don't know.  You should try it.  ;)

---

### Post by disturbedite on 2008-02-06
> **acoustibop said:**
> 
I played Playstation games on ePSXe for 5 or 6 years and enjoyed it very much, but when pSX Emulator came out, even the imperfect first version was enough to make me realise ePSXe just wasn't in the game any more.
lol, hadn't epsxe's development been dead for years by then?

---

### Post by acoustibop on 2008-02-06
Yes, disturbedite.  But until pSX came out, there didn't seem to be a viable alternative.

---

### Post by Python88 on 2008-02-07
> **acoustibop said:**
> Well, of those games, Python88, Final Fantasy VII certainly plays much better in pSX than it ever did in ePSXe.  The others, I don't know.  You should try it.  ;)

I'll give them both a try. Can't hurt. :)

---

### Post by disturbedite on 2008-02-07
> **acoustibop said:**
> Yes, disturbedite.  But until pSX came out, there didn't seem to be a viable alternative.
oh, ok.  i didn't realize that.

---

### Post by punong_bisyonaryo on 2008-05-18
A newer version of ePSXe (1.6) has been released last month. Has anyone been able to try that out for comparison?

---

### Post by acoustibop on 2008-05-18
Really?  It's not on the ePSXe site and it's not in the ePSXe forums.  There was an announcement a little over a month ago that an update would be issued - sometime...

Although this would seem to be a little more concrete than the usual claims that 'ePSXe is not dead,' I'll believe it when I see it.  And if it does come, I very much doubt that it will restore ePSXe to its former glory days - the newer breed of pluginless emulators have have proved that simplicity and accuracy are the way to go, except for diehard ePSXe fans.

And the update is unlikely to be any easier to set up and run in Linux than previous versions were.

---

### Post by punong_bisyonaryo on 2008-05-18
Whoops, my mistake. 1.60 was released last 2003, but they did report last month that their back working on it and hoping to release a new version soon.

Does anyone know about software renderer of pcx? I read somewhere a software renderer for epsxe, though I haven't tried it.

For games I play, I personally think FFVII and Castelevania:SOTN are classics. I also play Jackie Chan's Stuntmaster, just for kicks. I also once tried [Poy Poy]("http://en.wikipedia.org/wiki/Poy_Poy"), quite fun, unfortunately I lost my copy.

---

