---
title: "Wine 0.9.25 As a Gamer I'm Happy!! :-)"
date: 2006-11-14
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2006-11-14
Just went to winehq.org and added their repo to my custom list and installed wine 0.9.25 from the repo(according to the directions for Ubuntu).  According to them this version doesn't need a patch for WoW any more, and they were right, World of Warcraft runs just fine on my system now with a repo installed wine so I can keep it up to date a little better.  Half Life (the steam version) works flawlessly now as well, but with the same glitch I had way back when I had to compile wine manually for World of Warcraft.  If you try to kill the game instead of using all of the in-game and in-Steam exit commands, Steam.exe goes zombie and will "not" die.  The only way I've found to kill it is to restart my system.  As long as I don't try to kill it abnormally though the game, and steam, all work with no issues and exit normally if I use the in-game options to do it(which I do most all of the time but I thought this was worth mentioning).  I did also have to make the launcher myself.  It didn't properly place the shortcut on my desktop so I had to boot Windows to see what arguments the Half Life shortcut passed to bypass Steam and go straight to half life.  For those of you who want to know how to make a custom launcher for the Steam Version of Half Life, this is that the launcher should run:
```
wine "C:\Program Files\Steam\Steam.exe" -applaunch 70
```
The C:\Program Files\Steam can be replaced with the proper location of your Steam folder.  Other than these two problems it was almost as easy as in Windows, I popped in the CD, installed it, fixed the launcher and started playing.  It's weird though, even though it's being emulated(per say) it has a higher framerate, "much" faster load times and crisper sound in Linux than it does in Windows...

Anyway, just wanted to express my happiness that I no longer have to spend an hour sitting there watching wine compile just because there is a patch I have to apply to the source code so I can play WoW.  Now I can keep wine updated via synaptic and play World of Warcraft flawlessly.  W00t!

---

### Post by alinuxfan on 2006-11-14
Awesome!
Like I said in another post, when I get home this weekend, I am going to try it out and see how it works.

By the way, what are your system specs?

---

### Post by scrooge_74 on 2006-11-14
> **marcusdean.adams said:**
> Just went to winehq.org and added their repo to my custom list and installed wine 0.9.25 from the repo(according to the directions for Ubuntu).  According to them this version doesn't need a patch for WoW any more, and they were right, World of Warcraft runs just fine on my system now with a repo installed wine so I can keep it up to date a little better.  Half Life (the steam version) works flawlessly now as well, but with the same glitch I had way back when I had to compile wine manually for World of Warcraft.  If you try to kill the game instead of using all of the in-game and in-Steam exit commands, Steam.exe goes zombie and will "not" die.  The only way I've found to kill it is to restart my system.  As long as I don't try to kill it abnormally though the game, and steam, all work with no issues and exit normally if I use the in-game options to do it(which I do most all of the time but I thought this was worth mentioning).  I did also have to make the launcher myself.  It didn't properly place the shortcut on my desktop so I had to boot Windows to see what arguments the Half Life shortcut passed to bypass Steam and go straight to half life.  For those of you who want to know how to make a custom launcher for the Steam Version of Half Life, this is that the launcher should run:
```
wine "C:\Program Files\Steam\Steam.exe" -applaunch 70
```
The C:\Program Files\Steam can be replaced with the proper location of your Steam folder.  Other than these two problems it was almost as easy as in Windows, I popped in the CD, installed it, fixed the launcher and started playing.  It's weird though, even though it's being emulated(per say) it has a higher framerate, "much" faster load times and crisper sound in Linux than it does in Windows...

Anyway, just wanted to express my happiness that I no longer have to spend an hour sitting there watching wine compile just because there is a patch I have to apply to the source code so I can play WoW.  Now I can keep wine updated via synaptic and play World of Warcraft flawlessly.  W00t!

Why can't you kill the running application? kill -9 ID# of application?

---

### Post by digilink on 2006-11-14
That's good to know! I am definitely going to try this out tonight, does Counter Strike source as well as any of the other Steam games work well with this? 

Are you running Dapper or Edgy and what are your system specs?

---

### Post by alinuxfan on 2006-11-14
i was searching the forums and there was a post by someone saying that with the new wine (0.9.25) the steam games are working with some tag at the end...let me see if I can find it

---

### Post by gerowen on 2006-11-14
I'm running Edgy.  Here are my system specs:

2.2 Ghz Intel Celeron Processor
1 GB Dual Channel DDR1 SDRAM(DDR1 cause' it's the same RAM that was in my old PC which used an AMD chip)
256 MB NVidia GeForce FX 5500

---

### Post by Polygon on 2006-11-15
the original half life will run better as it was written to use directx AND open gl... and since windows has no native support for open gl (open gl for windows is just a layer ontop of directx) its slower. But since linux in general has direct native support for open gl, open gl games run much faster.

---

### Post by ericesque on 2006-11-15
WHA?  Lie-nux = gameses?

I have yet to make any real use of wine.  Any good tuts to look over?  

Somebody tell me that America's Army 2.7 works nicely as well...

---

### Post by gerowen on 2006-11-15
Haven't tried America's Army, but I've heard about and talked to lots of people who play it.  As far as a tutorial, you don't really need one, it's pretty much just install and play.  Half Life was weird b/c I have the Steam version which doesn't have an hl.exe file that I can find, so you have to make a weird launcher for it, but WoW I just copied the WoW folder over from my Windows hdd, and edited config.wtf to use opengl.  You can launch it with opengl without editing the file just by adding -opengl to the command.  You may also want to turn up the sound buffering to about 150.  There are specific instructions on the Winehq appdb.

---

### Post by Breepee on 2006-11-15
For the record: you're talking about Half Life 1, not 2?

---

### Post by Tamacracker on 2006-11-15
Which WoW are you guys talkin about? Is that the same one that's for online game play only?

---

### Post by Sammi on 2006-11-15
I was going to write a tread about just the same thing :-D

I LOVE Wine 0.9.25!!!!!!!!!!!!!!!!!

Gaming on Linux has never been better! This release is just fantastic!

---

### Post by Tamacracker on 2006-11-15
I'm playing Dofus on Kubuntu Edgy, but that's Flash based :D

And it's actually a little more smoother than on Windows XP.

---

### Post by gerowen on 2006-11-15
Yes Half Life 1.

---

### Post by gerowen on 2006-11-15
> **Tamacracker said:**
> Which WoW are you guys talkin about? Is that the same one that's for online game play only?

Yes I'm talking about [World of Warcraft](http://www.worldofwarcraft.com).  I play it and until now had to apply a patch to the source code and compile wine myself, which took freakin' forever.  If I tried just installing wine from the repos WoW would play, but it would flicker really badly.  This new version 0.9.25 doesn't require that patch, so now I can install wine from the repos and keep it updated that way too, which is much less time consuming than the previous method.

---

### Post by Tamacracker on 2006-11-15
> **marcusdean.adams said:**
> Yes I'm talking about [World of Warcraft](http://www.worldofwarcraft.com).  I play it and until now had to apply a patch to the source code and compile wine myself, which took freakin' forever.  If I tried just installing wine from the repos WoW would play, but it would flicker really badly.  This new version 0.9.25 doesn't require that patch, so now I can install wine from the repos and keep it updated that way too, which is much less time consuming than the previous method.


That's the online game you've gotta pay monthly right? Heh sorry for the simplistic questions, only MPORPG I played was FFXI.

---

### Post by gerowen on 2006-11-15
Yeah you pay montly like FFXI.  You can also buy cards at Wal-Mart if you don't wanna use a debit/credit card.

---

