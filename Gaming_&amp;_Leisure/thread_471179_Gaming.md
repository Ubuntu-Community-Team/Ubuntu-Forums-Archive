---
title: "Gaming"
date: 2007-06-11
forum: Gaming &amp; Leisure
---

### Post by JohnGalt on 2007-06-11
I had used kubuntu some time back and had no luck with wine. Now I've seen the demo for the new Ubuntu and love it. Using wine or crossover would it be possible to play shadowrun from microsoft? I'm doubting it but just checking

---

### Post by testube_babies on 2007-06-11
You could always try...

But I believe most people use Cedega for playing Windows games on linux.  Check it out.

---

### Post by cogadh on 2007-06-11
> **JohnGalt said:**
> I had used kubuntu some time back and had no luck with wine. Now I've seen the demo for the new Ubuntu and love it. Using wine or crossover would it be possible to play shadowrun from microsoft? I'm doubting it but just checking

It is unlikely that Shadowrun will work, since it is a DirectX 10 game. Wine/Cedega/CrossOver barely have DX 9 functions working 100% and there is almost no way they will have DX 10 functions working anytime soon.

---

### Post by hikaricore on 2007-06-11
Probably not for awhile unless it just magically works.
While this game was originally developed using the Halo engine (which is starting to work under WINE) the a new engine was built which probably will do nothing but crash yet under WINE.  It is heavily reliant on directx9 and while the WINE team has done a great job so far with their implementation of dx9, it's still far from perfect.  Meaning with each new application there are new obsticals to overcome.

This game isn't even listed in the [Wine Application Database]("http://appdb.winehq.org") yet.
If you have time please post any results (or lack there of) in the database to help others who come along after you.

--Aaron

---

### Post by Cappy on 2007-06-12
Microsoft is killing their franchises by making these games (Halo too!) DX10 only. Gamers know what a slow POS Vista is.

---

### Post by hikaricore on 2007-06-12
> **Cappy said:**
> Microsoft is killing their franchises by making these games (Halo too!) DX10 only. Gamers know what a slow POS Vista is.

And the masses are eating it up...

My downstairs neighbor told me he was upgrading to Vista in a year when they fix it... *sigh*

---

### Post by cogadh on 2007-06-12
> **Cappy said:**
> Microsoft is killing their franchises by making these games (Halo too!) DX10 only. Gamers know what a slow POS Vista is.
Tell me about it. It's bad enough when the latest games require massive hardware upgrades to run, but now I need to upgrade my OS!? That's BS, pure and simple. I had no need to upgrade to Vista, XP and Ubuntu work fine for me, but now I can only play old games on both Windows and Linux unless I upgrade Windows to Vista. Worse yet, have you seen the minimum requirements for Shadowrun?
    * Microsoft® Windows® Vista™
    * PC with Dual Core CPU
    * 2 GB of system RAM
    * 4.5 GB available hard disk space
    * NVIDIA 7800, ATI X1800 (256 MB or higher)

[http://www.microsoft.com/games/pc/shadowrun.aspx#sysreqs](http://www.microsoft.com/games/pc/shadowrun.aspx#sysreqs)

It's not even worth it to me to upgrade to Vista for this game, I would still need a whole new computer to run it!

---

### Post by JohnGalt on 2007-06-21
Sorry to be away so long. I saw the minimum requirements but still want to play it. I've been looking to get a dual core laptop with two gigs of ram anyway. I do a lot of graphics, dabble in video editing and hope to get more into it.

I saw on youtube that someone was running vista inside of ubuntu. Would that work? Granted you still have to have a copy of vista bogging down your computer. I use adobe photoshop cs2 and adobe premier in windows as it is, but dual booting isn't happening.

New game. Silkroad online. I'll go look it up in wine and cedega but I'm doubting it will be there. What do yall think?

---

### Post by Cappy on 2007-06-21
I ran debian in XP for a long time. IMO it's not worth it unless you only use it as a server. 

Basically, I feel the power of linux is that you have power to control your applications. I would use "cygwin" if I did it again, but honestly, you already have to be pretty good at linux to use Cygwin since it's CLI.

So it isn't that it isn't possible, but that other than being a server, you can do most things in Windows already. Again, if you want to use linux for its power of scripting there is Cygwin.

---

### Post by ukripper on 2007-06-21
games won't work in Vmplayer or virtualbox, virtual drive uses minimal resources and not designed to play games. I would suggest you to have dual boot with ubuntu/vista if you after playing games and graphics intensive operations.

---

### Post by JohnGalt on 2007-06-21
Thanks. Silkroad is in cedega but a playablility rating of two. I'm not sure if that's rating cedega running the game or the game itself. That game is notorious for server lag and full servers where you can't log into. After two logins that won't connect it closes the game and you have to bring it up again

If I can get Photoshop to work in wine this time and find a linux version of premier then I might just go with ubuntu anyhow. Well that and silkroad.

Thanks for helping

---

### Post by cogadh on 2007-06-23
Silkroad has silver and gold ratings on Wine's AppDB from Ubuntu Feisty users, you will likely be able to play it fine: [http://appdb.winehq.org/appview.php?iVersionId=5391](http://appdb.winehq.org/appview.php?iVersionId=5391)

---

### Post by Enverex on 2007-06-24
> **JohnGalt said:**
> Thanks. Silkroad is in cedega but a playablility rating of two. I'm not sure if that's rating cedega running the game or the game itself. That game is notorious for server lag and full servers where you can't log into. After two logins that won't connect it closes the game and you have to bring it up again

If I can get Photoshop to work in wine this time and find a linux version of premier then I might just go with ubuntu anyhow. Well that and silkroad.

Thanks for helping

Anything rated below 4 stars on Cedega's DB is unplayable normally and 4 stars is normally dodgy.

Those system requirements are a joke... and quite quite insane.

To the person that said about getting a dual core laptop, keep in mind that you'd need one with an absolute top of the range graphics card in it to keep up (mobile cards aren't as powerful as the desktop ones).

---

### Post by trinaryouroboros on 2007-06-28
> **Cappy said:**
> Microsoft is killing their franchises by making these games (Halo too!) DX10 only. Gamers know what a slow POS Vista is.

Good news, I, er, I mean, **a friend** of mine downloaded the Razor 1911 "Patched for XP" copy of Shadowrun, and, so far all that was needed was a few .dll's put in .wine/drive_c/windows/system32

However, the end result is certainly a C++ runtime error (Visual C++ for Windows that is) and I'm not quite certain how that's gonna pan out, more details to come, I suppose.

If anyone wants to work with..._a friend_...of mine, let me know!

:popcorn:

I would suspect the "non-patched" version of Shadowrun as well as Halo 2 could be around the block at this point!

:KS

---

### Post by trinaryouroboros on 2007-06-28
> **cogadh said:**
> Tell me about it. It's bad enough when the latest games require massive hardware upgrades to run, but now I need to upgrade my OS!? That's BS, pure and simple. I had no need to upgrade to Vista, XP and Ubuntu work fine for me, but now I can only play old games on both Windows and Linux unless I upgrade Windows to Vista. Worse yet, have you seen the minimum requirements for Shadowrun?
    * Microsoft® Windows® Vista™
    * PC with Dual Core CPU
    * 2 GB of system RAM
    * 4.5 GB available hard disk space
    * NVIDIA 7800, ATI X1800 (256 MB or higher)

[http://www.microsoft.com/games/pc/shadowrun.aspx#sysreqs](http://www.microsoft.com/games/pc/shadowrun.aspx#sysreqs)

It's not even worth it to me to upgrade to Vista for this game, I would still need a whole new computer to run it!

You know...there was another company who did a similar move a little while ago...but, not nearly as [rear]-backwards!

iD software, and Doom 3, ladies and gentlemen...and which Operating System was favored again? Oh yeah, that's right...linux!

:D

---

