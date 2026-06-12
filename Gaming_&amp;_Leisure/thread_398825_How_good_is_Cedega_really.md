---
title: "How good is Cedega really?"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by M$LOL on 2007-04-01
Cedega seems to be a complete waste of time, as I have only managed to get one out of four games I've tried working with it, and even then the videos don't work. Should I give up and shell out for VMWare Workstation so I can use the 3D acceleration support?

The games I can't run are Shrek2, Mechwarrior 4 Mercenaries and Pirates of the Caribbean. Is Cedega actually supposed to run more games than Wine? Can someone explain why it can't do stuff a real Windows box can?

---

### Post by hikaricore on 2007-04-01
[http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)

^According to their database:

Shrek2: [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3732](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3732) (5/5 Playable (likely acomplete lie))
Mech: [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3406](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3406) (1/5 Playable)
Pirates [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3173](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3173) (Not Playable)

No actual info on any of these games is listed in the database nor are there screenshots.

Comparing to wine from the [wine application database]("appdb.winehq.org"):

Shrek2: [http://appdb.winehq.org/appview.php?iVersionId=7184](http://appdb.winehq.org/appview.php?iVersionId=7184) (garbage rating, citing nonworking installer)
Mech: [http://appdb.winehq.org/appview.php?iVersionId=5686](http://appdb.winehq.org/appview.php?iVersionId=5686) (garbage rating, citing game not starting.)
Pirates: [http://appdb.winehq.org/appview.php?iVersionId=5356](http://appdb.winehq.org/appview.php?iVersionId=5356) (garbage rating, game starts but unplayable, screenshots look promising however)

So if we take transgaming's word for it they're running 2 out of 3 of your games... and wine is running 0 out of 3 of your games.

But that's only if we take their word for it.

They had no user input or screenshots of anything, nor was there any info on how the games ran aside from the stupid stars system.

At this point it obvious that cedega is ****, and transgaming is fronting it as the Holy Grail of linux gaming.  None of your games are going to be even remotely playable with either wine or cedega for now anyway, I'm sure wine will be running pirates soon from the looks of those screenshots.

If you can't bear to give up your windows games, you'll have to keep them in a windows world by dual booting.  This probably isn't what you want to hear but it's the truth.  Running any of these games even with vmware & 3d acceleration is probably a pipedream as well as thier direct rendering is lacking support for many functions used in games today.  Seriously I think you need to dual boot ubuntu/windows and that's the best you can hope for.

** Edit **

You may want to personally test pirates yourself, as the last test done on appdb.winehq.org was
June 08 2006, it may run by this point so test it and see.  :)   If you have any luck please post
your results there for others like yourself to come across.

---

### Post by M$LOL on 2007-04-02
OK, thanks for all that. Now I am pretty much fed up of Cedega, and I think I'll uninstall it.

Despite it being my best chance of getting them working, I have no intention of ever using Windows on my PC again. That might just be me being snobby towards it, but IMO Linux is just so much better that I'm just not gonna use Windows.

If vmware isn't going to do it, then I won't buy that either. I'll just hope Wine will improve to the point where I can play the games.

Thanks for all the info. It helps me out a lot.

I'm interested as to why Cedega can't run everything. Isn't it just a DirectX implementation on Linux?

---

### Post by Jovec on 2007-04-02
> **M$LOL said:**
> I'm interested as to why Cedega can't run everything. Isn't it just a DirectX implementation on Linux?

Not exactly.  It's a Windows and DIrectX API implementation on Linux.

1) Linux video card drivers do not understand Direct3D API calls, so Wine/Cedega/Crossover must translate (wrap) D3D into OpenGL and often times it isn't a 1-to-1 conversion.

2) Linux has no suite of APIs to equal to the DirectX suite, which means that all of the other things Direct X does, like query video hardware for feature support, provide networking, handle (realtime) keyboard and mouse input, sound, etc.  must also be translated into the appropriate Linux calls.

3) At best, the DirectX documentation will describe a given function, its input parameters, and its output parameters.  The "how" of what it does, the Wine team must reverse engineer.

4) Even with perfect DirectX emulation, games still wouldn't work perfectly until the Windows API emulation from Wine worked perfectly.  That is, games make use not only of DirectX calls, but also of Windows calls.  True, games can be designed for portability, but most of the time that takes more work (and more competency/experience).

---

### Post by M$LOL on 2007-04-02
OK, thanks for the info. You have made me hate M$ by 1.5% more, lol.

---

### Post by Jovec on 2007-04-02
> **Jovec said:**
> 2) Linux has no suite of APIs to equal to the DirectX suite, which means that all of the other things Direct X does, like query video hardware for feature support, provide networking, handle (realtime) keyboard and mouse input, sound, etc.  must also be translated into the appropriate Linux calls.

For correctness, there is the SDL project: [http://www.libsdl.org/](http://www.libsdl.org/) but I have no clue about the completeness of its feature set, and anyway there would probably need to be a DX-to-SDL wrapper on Linux if/until there was enough momentum (and financial incentive) for developers to use SDL natively.

---

### Post by justin whitaker on 2007-04-02
> **M$LOL said:**
> Cedega seems to be a complete waste of time, as I have only managed to get one out of four games I've tried working with it, and even then the videos don't work.

That is not an uncommon reaction. In fact, even with games they say are supported, you are better off without the cut scenes. Cedega no likey. 

>  Should I give up and shell out for VMWare Workstation so I can use the 3D acceleration support?

I thought gaming was a big weakness of VMware. Is that no longer the case?

> The games I can't run are Shrek2, Mechwarrior 4 Mercenaries and Pirates of the Caribbean. Is Cedega actually supposed to run more games than Wine? 

Transgaming claims that they have 200 or so titles supported, but I have had trouble with most of them. I think the number is way inflated....more games seem to run successfully via WINE, but it really is a question about how much work you want to do. 

> Can someone explain why it can't do stuff a real Windows box can?

Proprietary, closed code, a poorly defined API (Direct X) that keeps shifting with each generation.....the list goes on and on.

---

### Post by handy on 2007-04-03
Cedega pays for a copy protection thing worked out with some companies, so it can play some things that Wine can not, apparently.  

If Cedega does play something satisfactorily, that can't be done via Wine, then a user can get away with the minimum $15.50 US, 3 month subscription to legally be able to play that game forever.

Like many other's I think that the payment method that Transgaming uses sucks big time. They are too expensive in the long term, but many think that Cedega is quite reasonably priced if you only need the 3 month thing to get something(s) going...

---

