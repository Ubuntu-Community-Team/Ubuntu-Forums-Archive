---
title: "How do I play games on Ubuntu for free?"
date: 2009-02-02
forum: Gaming &amp; Leisure
---

### Post by Uubnewb on 2009-02-02
I'm still new to Linux and only just learned about Cedega and Wine that allows Windows games to be played on Linux.  However, apon further investigation I realized that neither of these are free.

I did hear rumuours that you can get both of them for free (legally) if you compile them yourself.  Is this true?  If so, how do you compile them?  Or is there any other way to play games on Linux for free?

Just in case the distro have anything to do with it:  I'm running Ubuntu 8.10 64-bit.

Any and all help will be greatly appreciated.

---

### Post by RaiCoss on 2009-02-02
> **Uubnewb said:**
> I'm still new to Linux and only just learned about Cedega and Wine that allows Windows games to be played on Linux.  However, apon further investigation I realized that neither of these are free.

I did hear rumuours that you can get both of them for free (legally) if you compile them yourself.  Is this true?  If so, how do you compile them?  Or is there any other way to play games on Linux for free?

Just in case the distro have anything to do with it:  I'm running Ubuntu 8.10 64-bit.

Any and all help will be greatly appreciated.

WINE is completely free dude!!

---

### Post by Neural oD on 2009-02-02
go to command line type: sudo apt-get install wine

---

### Post by lukjad on 2009-02-02
I think that you are mixing up Wine and Crossover Linux. Wine is free, Crossover Linux is not.

Go to Synaptic (*System->Administration->Synaptic Package Manager*) And search for **wine**.

---

### Post by Vadi on 2009-02-02
Or [just click here]("apt:wine") to install Wine :)

---

### Post by kbutcher5 on 2009-02-02
Wine tends to have alof of windows games it won't work with, but i found that one might bump a few more games into compatible mode, if you install DirectX 9.0c in wine.
To do so, follow this guide: [http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

---

### Post by kutagh on 2009-02-02
Also take a look at [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php) and other Linux gaming sites.

---

### Post by LinuxFox on 2009-02-02
Like everyone is mentioning, you can get Wine through the repository.  Though it will take tweaking to get some games to run.

Also, there are plenty of open source games that can be added through Add/Remove.  These don't cost anything.  Though if you play online (Nexuiz for example), you're better off downloading the latest version from the website.  Some of the games in the repository might be outdated.

I recommend Add/Remove if you're a beginner, since it's the easiest way to install games. ;)

I hope this helps.  Happy gaming if you play a Wine game or a Linux native game. 8)

---

### Post by Uubnewb on 2009-02-02
:oops: Oops, sorry for that mix-up, I didn't realize Wine was free.  Well, to be honest, I had something like Xwine or WineX in the back of my mind when I posted the thread.  I was using my cell-phone so I couldn't open a new tab to quickly verify my info.

As for installing DirectX on Linux via Wine, well thats just absolutely brilliant!  I'd never think of something like that.  Thanks.

About the open source games, and please don't take this the wrong way, but are they any good?  I'm not trying to be an A-hole here, it's just that I never heard about any decent free games (but then again Linux is free, and that's better than Windows :) ).

I guess by now you know that I'm still an utter newb with Linux, open source and freeware in general so, like I said, please don't be offended.  Truth be told I would quite like to try some of these free games out.  I'm not exactly a heavy gamer, but it's always fun to play a nice RPG or FPS with a good story line.

Thanks for all the help with this, I really appreciate it.

---

### Post by willbe1kenobi on 2009-02-02
It just depends on what your taste is.

I like Nexuiz (It's like Unreal Tournament) and Openarena (It is a clone of Quake 3 using the same source code). I wish i had the money for a proper broadband connection (I live in South Africa) to try some more, but those are very good quality open source games.

Plus you could try 'Supertux' if you like platform side scrolling games (it is a near clone of super mario bros).

and if you are in doubt just google the title of the game and see how well people have been reviewing it.

---

### Post by Uubnewb on 2009-02-02
Thanks, Nexuiz and Openarena sounds pretty cool.  I'll give it a try.  Do you maybe know of some RPG titles I can try out?

---

### Post by Uubnewb on 2009-02-02
> **Uubnewb said:**
> Thanks, Nexuiz and Openarena sounds pretty cool.  I'll give it a try.  Do you maybe know of some RPG titles I can try out?

It always helps to have a name as reference, so even if the game is not all that good, please mention it so I can have something to work with.

Thanks.

---

### Post by Grishka on 2009-02-02
check out [http://happypenguin.org/](http://happypenguin.org/). it lists pretty much every linux game in existence, free or not.

---

### Post by LinuxFox on 2009-02-02
> **Uubnewb said:**
> About the open source games, and please don't take this the wrong way, but are they any good?  I'm not trying to be an A-hole here, it's just that I never heard about any decent free games (but then again Linux is free, and that's better than Windows :) ).

I guess by now you know that I'm still an utter newb with Linux, open source and freeware in general so, like I said, please don't be offended.  Truth be told I would quite like to try some of these free games out.  I'm not exactly a heavy gamer, but it's always fun to play a nice RPG or FPS with a good story line.

Thanks for all the help with this, I really appreciate it.No offense taken. :)  I'd say it's a matter of opinion on games being good or bad.  Personally, some of my favorite Ubuntu games are open source games.

Since you can get games using Add/Remove, you can add it to see if you like it.  If you don't, you can always remove it easily using Add/Remove. ;)

I don't know of any open source FPS games with story, Nexuiz and Open Arena is pretty much single player with bots and multiplayer.

---

### Post by Crafty Kisses on 2009-02-02
SuperTux Kart all the way!

---

### Post by raydeen on 2009-02-03
Regnum Online is a good MMOG that's in sort of a perpetual beta. It's not the prettiest thing but it's not bad either.

[http://www.regnumonline.com.ar/](http://www.regnumonline.com.ar/)

The only hitch you might run into is initially trying to run the game. There's a weird command you may have to run.

```

MALLOC_CHECK_=0 ./rolauncher

```

or 
```

MALLOC_CHECK_=1 ./rolauncher

```

I had to run the first one to get the game to launch the first time but after that, no problem.

Two other good games are Savage and Savage 2

[http://savage2.s2games.com/main.php](http://savage2.s2games.com/main.php)

Savage is completely free to play and Savage 2 has free and paid versions.

---

### Post by Uubnewb on 2009-02-04
Thanks for all the replies.

Unfortunately I'm super busy at work as well as with my studies so it will take some time before I can try out all the games.  :(

My World of Warcraft characters have been inactive for more than a month now :cry: and I don't even know when was the last time I KO'ed someone in Splinter Cell... <sigh>

But I digress.  I'll let you guys/girls know as soon as I tried something out.

Thanks again for your help, really appreciate it.

---

### Post by Bölvaður on 2009-02-04
> **Uubnewb said:**
> Thanks, Nexuiz and Openarena sounds pretty cool. 

Nexuiz is okayish game, but omg opanarena is bad. Warsow is much better than openarena and for me it is just as important to linux gamer as eletricity is for computers.

You may also want to look into toribash and crack attack if you are into more of a... uh.. yes well just check those out on youtube and see if you'll like them.

---

### Post by janicejan on 2009-02-05
Have you tried final fantasy? for me its the best in today's MMORPG.. clean and detailed graphics also nice strategic gameplay.

---

### Post by donkyhotay on 2009-02-05
> **janicejan said:**
> Have you tried final fantasy? for me its the best in today's MMORPG.. clean and detailed graphics also nice strategic gameplay.

According to winehq that game has a garbage rating.

---

