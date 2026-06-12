---
title: "Guild Wars"
date: 2006-05-17
forum: Gaming &amp; Leisure
---

### Post by flaak_monkey on 2006-05-17
Does Guild Wars work in Wine?

---

### Post by handy on 2006-05-17
I have asked the same question a few times & never got an answer??

Hopefully you will...

It certainly works very well with cedega 4.4.3.

Follow [**this link**]("http://ubuntuforums.org/showthread.php?t=123715") for details about that.

---

### Post by Gannin on 2006-05-17
If you want to play Guild Wars in Linux, your best bet, for now, is to use Cedega.

---

### Post by leech on 2006-05-18
[http://appdb.winehq.org/appview.php?versionId=4643](http://appdb.winehq.org/appview.php?versionId=4643)

There is your answer.  Though maybe that has changed, since it hasn't been updated for 0.9.13 of Wine yet.

Leech

---

### Post by KingBahamut on 2006-05-18
Well hold up though. 

Their newest release Factions doesnt jive well with Cedega, as that release requires DX9.

---

### Post by handy on 2006-05-18
[QUOTE=KingBahamut]Well hold up though. 

Their newest release Factions doesnt jive well with Cedega, as that release requires DX9.[/QUOTE]

That is important news that I did need to know, I would not have been happy if I bought factions & had to boot into windoze to play!

Is there a solution on the horizon?

---

### Post by KingBahamut on 2006-05-18
Based on interactions and questions on the Transgaming side, I believe so. But, we will have to see.

---

### Post by Gannin on 2006-05-18
The newest version of Cedega is supposed to have some DirectX 9 support, implemented so that Cedega could support Battlefield 2.  In fact, while installing Battlefield 2, you also install the DirectX 9 libraries, and it works just fine.

However, I've never tried Factions with Cedega.  Just because Battlefield 2 works with DirectX 9 support in Cedega doesn't mean any other games will.  But by the same token, you can play Guild Wars without Factions.  Factions is optional.

---

### Post by KingBahamut on 2006-05-18
Factions Directly asks for DX9.0c , Im not sure that is the version that BF2 asks for , but I could be wrong.

---

### Post by Gannin on 2006-05-18
I'm not sure either, but because of Cedega's enhanced support of DirectX 9, you might be able to install DirectX 9.0c within it and have it work.  The only way to know for sure is to test it with a game that requires DirectX 9.0c, but I don't have a current Cedega subscription.

---

### Post by handy on 2006-05-23
Is the directXc call backward compatible?

If not, it will be demanding a certain standard of graphics card!??

---

### Post by handy on 2006-05-23
[QUOTE=flaak_monkey]Does Guild Wars work in Wine?[/QUOTE]


Hmmm!  Looks like we still don't know the answer to than one!!

Still, if some one had got it sorted with Wine, I'm sure that by now, they would have made it **VERY** obviouse that they could do it!!

So, looking at the replys so far I would have to say that NO, you can not run GW under Wine!

To be able to play GW, under Linux for free is a reality that is still only a little ways off, as I see it any way! :)

---

### Post by handy on 2006-05-23
[QUOTE=leech][http://appdb.winehq.org/appview.php?versionId=4643](http://appdb.winehq.org/appview.php?versionId=4643)

There is your answer.  Though maybe that has changed, since it hasn't been updated for 0.9.13 of Wine yet.

Leech[/QUOTE]

If that IS an answer, could you please interpret it for the rest of us?? :)

---

### Post by drfalkor on 2006-05-23
I have tryed to run Guild Wars with wine with no luck at all ](*,) 

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  296
  Current serial number in output stream:  299

```
Oh well :neutral:

btw: I only get the updating screen, and when the game starts, I got that error from above !

---

### Post by drfalkor on 2006-05-23
my run command:
```
wine Gw.exe
```

My wine version is 0.9.13 ( in dapper, with the latest updates )

---

### Post by KingBahamut on 2006-05-23
Hmmmmm, is DirectXwine up to date? As far as I knew, DirectXwine was a series of patches against wine to correctly run a DirectX9 install.

---

### Post by handy on 2006-05-23
This is a good thread!

At least we are getting some **YES, NO & MAYBE's!**  :KS

---

### Post by KayinStorm on 2006-06-07
under wine, my install well, installs, updates, and loads, but after it gets to 100% loading it freezes.

Still working on Cedega here, but that may be cause me and the CVS version get along better than me giving away my hard earned money.

---

### Post by handy on 2006-06-07
According to the Transgaming forum, GW in any shape or form runs on the same foundation.

So, Prophecies or Factions is the same as far as Cedega is concerned.

I expect that there was probably a way for me to say that, which would have made you feel more secure!?

Sorry, best I could do...

---

### Post by handy on 2006-06-09
From what I have read on the Transgaming forums, Cedega uses next to no DX9 features.

You can run GW with the **-dx8** command line argument & possibly see performance impovements!

The **-noshaders** arguement will speed the game up, but the game will ***look different!?***

This is of course all hear say, I have not done it!

---

### Post by HeSh on 2006-06-09
There are 2 new rating entries for GW on transgaming gameDB. They say 4/5 playability on Cedega 5.1.3.

---

### Post by drfalkor on 2006-06-09
updated wine to 0.9.15 today, still not working (same error) :roll:

---

### Post by KayinStorm on 2006-06-09
Well, I find a LOT of lag, even with some of the ATi switches on...

I can chat and sell, but fighting is still not possible.

---

### Post by Thoop on 2006-06-09
I play factions and it does work on cedega and its very well playable, but it's not very fast ;)

---

### Post by HeSh on 2006-06-10
yes, today i managed to run it as well. It runs great. No glitches, no net-lag. It's great. However i have to decrease quality to minimum or it becomes a slideshow.

---

### Post by ironfistchamp on 2006-06-10
I find the Factions works better than Prophecies with Cedega. The map isn't as messed up. On the original its all black and distored (anyone know of a fix?). To get Factions installed I registered my factions on a mates computer and created a character. Then I logged in on mine on Ubuntu and selected my Factions character. It downloaded all the maps and that and I was good to go.

This is the only game I can get woking with Cedega. Nothing else works with it. I am using the 5.1.4 engine. I can prob post my settings if anyone needs them.

Ironfistchamp

---

### Post by handy on 2006-06-10
[QUOTE=ironfistchamp]I find the Factions works better than Prophecies with Cedega. The map isn't as messed up. On the original its all black and distored (anyone know of a fix?). To get Factions installed I registered my factions on a mates computer and created a character. Then I logged in on mine on Ubuntu and selected my Factions character. It downloaded all the maps and that and I was good to go.

This is the only game I can get woking with Cedega. Nothing else works with it. I am using the 5.1.4 engine. I can prob post my settings if anyone needs them.

Ironfistchamp[/QUOTE]

You should find speed improvements if you use version 4.4.3 of Cedega.  Most, if not everyone else does!

---

### Post by ironfistchamp on 2006-06-11
I logged into the Transgaming website but couldn't find the download. I shall try again. If I can't find it can someone point me in the right direction?

Thanks

Ironfistchamp

EDIT: Found it now testing :D

---

### Post by ironfistchamp on 2006-06-11
Not much difference. The only big problem is the map. That is messed up in every engine. Anyone know a fix for it?

---

### Post by gaminggeek on 2006-06-12
Play the game in fullscreen and it fixed the map problem for me :)

---

### Post by ironfistchamp on 2006-06-12
I will try that thanks for the tip.

---

### Post by handy on 2006-06-13
Anyone found the Cedega Demo on the Transgaming site?

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Simulation/Cedega-9843.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Simulation/Cedega-9843.shtml)  is the only place I know of to find it now?

I have also asked for **support** directly & via the forums...

Transgaming support is non-existant from my experience! 

I am not too impressed with Transgaming at the moment.  

I look forward to Wine being able to run Guild Wars, BIG TIME!

---

### Post by handy on 2006-06-14
I finally got a reply from Transgaming, re: there **Cedega_time_demo**, it follows:

[I][B]Hello,

Thanks for contacting us.  The demo has been taken offline for
retooling.  We hope to have an improved demo available in the future.

Let us know if you have any other questions.

--
Kevin Ip
Quality Assurance and Technical Support
[www.transgaming.com](www.transgaming.com)[/B][/I]

So there you have it!

---

