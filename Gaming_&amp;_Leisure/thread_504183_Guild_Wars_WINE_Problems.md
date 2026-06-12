---
title: "Guild Wars WINE Problems"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by Shyper on 2007-07-18
Guild Wars Wine Errors
Hey, whenever I try to start Guild Wars under Wine, the game tries to load but shoots out these errors and crashes:

fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x7baed2f0, 260): stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMe m (0x1250ec : stub, simulating 64MB for now, returning 64MB left
Segmentation fault (core dumped)


I have Wine 0.9.33, and can give more spec info if needed. Does anyone know why the heck it does this?

---

### Post by Shyper on 2007-07-19
Bump?

---

### Post by milton1 on 2007-07-19
Have you tried the -nosound flag? Right now GW is only working for me without sound.

---

### Post by cogadh on 2007-07-19
You should probably also update Wine to a newer version. The current version is 0.9.41, but I believe the game works best with 0.9.36 - 0.9.38 versions. 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

The only test data on 0.9.41 has a garbage rating on AppDB, so I would steer clear of that version for now, unless you want to test with it yourself.
[http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

---

### Post by hobieone on 2007-07-19
i would folllow the ratings on wione app data base toomuch and treat as a guidline more or less. i have guild wars running pretty god with the latest wine release. there was a graphical glitch that will ocuur if in guild wars options you have post effects checked if uncheck then it eliminate the issue other than that it runs fairly good.  
 
but for the most i nootice withthe rating on wine datbase it not very acurrate at times due ther arn't very many maintaners  that post to them and some people willhave one minor glitch  and  that has a minor work around and they will mark the app as garbage. so it usally best to try it yourself

---

### Post by cogadh on 2007-07-19
I wouldn't say there are not a lot of maintainers. There are actually over 17,000 registered contributors to the AppDB site and only about 2600 of them appear to be inactive. There were over 4000 active members just in the last month, including myself: [http://appdb.winehq.org/appdbStats.php](http://appdb.winehq.org/appdbStats.php)

As for the accuracy of the test data, you need to consider several factors when trying to interpret it; the Wine version used, the *nix distro used, the comments posted by the contributor, the test history, etc. For example, when a game like Guild wars, which has a history of a silver rating (mostly, it has been rated gold and bronze as well) suddenly gets a garbage rating from an Ubuntu 7.04 user with the latest Wine, I might try running a few tests myself, to see if there was some kind of regression in the latest Wine. If I'm not in the mood for testing and just want to play a game, I'll play it safe and install one of the older Wine versions and just run it. 

Generally speaking, the ratings and information on AppDB are very good and usually consistent. Games that require a little "hand-holding" to get working will usually have inconsistent ratings, due to the special configurations required to launch the game correctly, but, if you read through the ratings and the posts that follow them, the reasons behind that are made plainly clear.

---

### Post by hobieone on 2007-07-19
yes i garee the information inthe wine data base is good. it just with the latest version only that seemed to break was the post processing effects if turned on ingame was causing graphic distortion but it was ealy correctable  by turning  off so in my opinion it hardly rates a  garbage rating . it just seems there ther needs to be tighter guidlines as to what would  rate a garbage ratingor any of the other rating as to say

---

### Post by cogadh on 2007-07-19
We're getting way off-topic here...

If you read the information posted by Shimala (the guy who gave it a garbage rating), the game wouldn't even launch for him. If the game won't launch, it must get a garbage rating, its that simple. 

The fact that you didn't encounter the same problem that Shimala did just means that your configuration is somehow different than his and you should add your stuff to AppDB. Maybe your info will help Shimala get his game working.

The rating standards used by AppDB are very clearly defined (see below). Each submission is reviewed by an application maintainer and/or a group of site administrators for those standards and is only allowed to be added to the database if it has met the correct criteria and is approved. I have only come across one instance where I disagreed with the rating given by a contributor for a single test. That was because an application was given a gold rating when,* in my opinion*, the contributor's own comments indicated it should have been silver.
> Platinum - An application can be rated as Platinum if it installs and runs flawlessly ‘out of the box’. No changes required in winecfg.

Gold - Application works flawlessly with some DLL overrides or other settings, crack etc.

Silver - Application works excellently for ‘normal’ use; a game works fine in single-player but not in multi-player, Windows Media Player works fine as a plug-in and stand-alone player, but cannot handle DRM etc.

Bronze - Application works, but it has some issues, even for normal use; a game may not redraw properly or display fonts in wrong colours, be much slower than it should etc.

Garbage - An application gets this rating if it cannot be used for the purpose it was designed for. There should be at least one bug report in Bugzilla if it gets this rating. Application does not start, or starts but has so many errors that it is nearly impossible to use it.

[http://appdb.winehq.org//help/?sTopic=maintainer_ratings](http://appdb.winehq.org//help/?sTopic=maintainer_ratings)

---

