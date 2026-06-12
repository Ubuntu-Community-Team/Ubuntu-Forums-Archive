---
title: "Just one problem to make my wife transfer to Linux completely ;)"
date: 2007-05-16
forum: Gaming &amp; Leisure
---

### Post by letherian on 2007-05-16
Hey everyone!

Just wondering about something, my wife has finally come to her senses and let me install Kubuntu on her machine. She really likes those small flash/shockwave games that you find around the internet, especially ones on [www.freeworldgroup.com](www.freeworldgroup.com). (I'm not really sure if it's shockwave or flash)

So, i really want her to stick to linux and learn it as good as windows, cause we all know that windows should have ceased to exist.

When i run the games in Crossover Office they start and, sound is coming up, but there is no picture, the only thing there is the desktop. When i click the button on the panel i can see various icons of the game etc.

Anyone ever tried these games and gotten them to work?

Any answer would be greatly appreciated.

Thanks

--- leth

---

### Post by hikaricore on 2007-05-16
For flash games you'll need to install flash9.  You can do this from the adobe website or use ubuntu packages to install it, either pretty much work.  Search around for "flash install" or something of the sort, and you'll find an easy way.  ^_^

As for running windows software under linux with Crossover and or WINE (which are essentially the same thing), have a look here:  [http://appdb.winehq.org](http://appdb.winehq.org)

For info on how well certain titles run on linux.  I believe Crossover also have a database of software and it's rating using their product, but I don't have time to track it down at the moment.  Good luck.

If you need help here with a specific game that is known to work under crossover/wine please mention the name of the game so someone knows what you're talking about >.<

--Aaron


quick edit:  The games on freeworld group seem to work just fine for me /w firefox and konqueror using the flash9 plugin.

[http://img.photobucket.com/albums/v414/hikari_corgan/snapshot32.png]("http://img.photobucket.com/albums/v414/hikari_corgan/snapshot32.png")
[http://img.photobucket.com/albums/v414/hikari_corgan/snapshot33.png]("http://img.photobucket.com/albums/v414/hikari_corgan/snapshot33.png")

---

### Post by letherian on 2007-05-16
Hey mate!

Thanks for the quick response, and sorry for not giving an exact example. 

One of these games are Diner Dash 2, my wife likes to download them play/buy them. 
There the problem is, they work in Firefox but not when downloaded, as she has to download/buy certain games and run them on her computer to get them to work.


-- Leth

---

### Post by rjstaaf on 2007-05-16
Flash works fine in Linux, the problem is more than likely Shockwave.  Not all Windows apps are going to run in Wine/Crossover.  I have the same issue with my kids.  I have Ubuntu on their computer and they too like to play the Flash and Shockwave games.  For now they can only play Flash games.  The only solution I think is going to be for people to nag Adobe and get them to hurry up and port Shockwave over to Linux.  

Here is a link to the Adobe feedback page, if even a fraction of the Unbuntu community would let them know there is a demand it could only help.

[http://www.adobe.com/aboutadobe/contact.html](http://www.adobe.com/aboutadobe/contact.html)

---

### Post by letherian on 2007-05-16
Hehey, great!

I'll just have to get on Adobe's neck and make them make it ;)

Cause i don't want her to slip over to the dark side...again....


Thanks for all your help mates :)


---- Leth

---

### Post by hikaricore on 2007-05-16
Well there is lame work around for something like this.  I havn't tried it but I'm about to.

If install Internet Explorer and run it under wine, you should be able to install the shockwave plugin for IE.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

I'm going to test out my theory and I'll let you know if I have any success.  But as far as downloaded games that use shockwave libraries, you might be SOL.

---

### Post by hikaricore on 2007-05-16
Update on my attempt:

**[COLOR="Red"]I Completely Fail[/COLOR]**  Sorry figured it was worth a shot.  >.<

[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/snapshot34.png[/IMG]

---

### Post by letherian on 2007-05-16
Hehe.

Thanks for trying anyways mate :)

Guess we'll have to wait for Adobe :/

-- Leth

---

### Post by ShadwWulf on 2007-12-30
On the topic of Diner Dash, I have the same problem.  My wife is somewhat resistant to the Linux as the only OS on the machine situation due to games.

I am happy to report that the retail (installed from CD) version of Diner Dash 2 can be made to work under the newest Wine (0.9.52).  You have to install it by running the installer from the CD and then when the icon is created, edit the executable target so it runs the dinerdash2.exe that is under the 'game' subdirectory and not the launcher front end (that oddly enough is also named dinerdash2.exe) that the icon initially targets.

Once this is done, it works for the most part and is mostly playable.  It appears that there is a bug somewhere in the RGBA loader for the .ani files used as animation resources because some of the animations are corrupted due to a bit/byte shifting issue.  But it's a start.  I have also found that if you turn on the virtual desktop option in winecfg for Diner Dash 2, the performance is a bit higher.

I'm going to dig into some potential DLL overrides and will report back with any findings.  Anybody else's input would be great as well, given that it is also my wife's favorite game of late.

---

### Post by rgb1701 on 2008-01-20
> **ShadwWulf said:**
> On the topic of Diner Dash, I have the same problem.  My wife is somewhat resistant to the Linux as the only OS on the machine situation due to games.

I am happy to report that the retail (installed from CD) version of Diner Dash 2 can be made to work under the newest Wine (0.9.52).  You have to install it by running the installer from the CD and then when the icon is created, edit the executable target so it runs the dinerdash2.exe that is under the 'game' subdirectory and not the launcher front end (that oddly enough is also named dinerdash2.exe) that the icon initially targets.

Once this is done, it works for the most part and is mostly playable.  It appears that there is a bug somewhere in the RGBA loader for the .ani files used as animation resources because some of the animations are corrupted due to a bit/byte shifting issue.  But it's a start.  I have also found that if you turn on the virtual desktop option in winecfg for Diner Dash 2, the performance is a bit higher.

I'm going to dig into some potential DLL overrides and will report back with any findings.  Anybody else's input would be great as well, given that it is also my wife's favorite game of late.

Great info!  It's a sad fact that at present, the last string holding many non-techie/ "normal" people back from Linux is just some games :(.  Open Office and the various Linux media players appear to be more than able to satisfy most average users at this point.  The rising popularity of Firefox across Win and Linux has effectively made the web platform neutral (again, after a few years of IE-centric malfeasance)

Of course, DirectX, .NET and other nefarious schemes were MS's plan to accomplish the games-lock in.

What is so infuriating is that games written in Flash, Java or other platform independent authoring environments *Should* have no issue running in Linux.  I assume Diner Dash is basically Flash- correct me if I'm wrong.

I believe that Flash, Java and similar are the gateway for Linux adoption, as kids/Moms/Wives increasingly use web based Flash/Java games- the Runescapes  and Pogo.coms of the world.  

The problem is, once they get hooked on the "free" web based version, they too often can't run the downloadable executable on Linux :(

My approach has been to not be an enabler for Win/MS any longer.  I no longer answer any Win-related questions, nor offer any assistance with WIn/MS related software, after 16 years or so of supporting MSDOS-Win31-WIn95-Win95B-Win98-Win98SE-XPSP1 (I never went beyond SP1, my  "line in the sand")  for a LOT of people.  I can't count the number of times I've helped family/coworkers remove malware and bloat from their Win boxes.  I wish I never had.  But now when someone asks, I offer to install a new, faster OS like Ubuntu or Mint.  A coworker asked last week how he could control access to Runescape for his kids due to excessive time spent playing, for both IE and Firefox.  I sent him links for Firefox parental control plug-ins.  As for IE, I told hime I know nothing about it and haven't used it for 5-6 years, which is the truth.  In the past, I might have volunteered to do the research and testing for him as a technical exercise, but I only do that for Linux stuff now.  

No matter how much a kid/wife/Mom whines, either find an alternative in Linux (or a Mac), tell them to get a dedicated game console (PS2's are cheap and still get current games) or have them do without.  The line in the sand has to be drawn somewhere, sometime.

As someone mentioned in a related thread recently, too many of the web-freebies have spyware in their downloaded executables by design, anyways, so you don't *want* to install them.  Teach your kids/ wife/Mom why that's wrong.
[http://ubuntuforums.org/showthread.php?t=515040](http://ubuntuforums.org/showthread.php?t=515040)

Plus, introduce them to the Synaptic repository.  Let them browse and search for games themselves.  And the number of free, web-based Flash/Java games is only growing, that play in Firefox without a download.  My mom uses Pogo.com a LOT, and has never needed to download anything- all web/Flash/Firefox/Linux compatible.

Tell them that after they've played everything in Synaptic, plus every web flash/Java game, plus all the commercial Win games that *do* run fine under Wine, *then* you *might* help them with the ones they *can't* run on Linux.  Focus on the 1000's of things they *can* do in Linux, not the optional "fun to haves" they may want in the short term.

Remember that for every year old a Win game is, the more likely it is to run under Wine.  The amount of DOS games and Win games prior to 2004 is huge, and can be had for very little on ebay or other sources.  Dosbox/Freedos can be used for DOS games.  So with all these options, the amount of games you *can* run without Windows is *huge*.

And I haven't even mentioned emulators for game consoles, which enable the playing of basically every game for every console and arcade machine from the year 2000 and before, literally numbering into the 10's of thousands.

The "wife/Mom/kids want xxx or YYY game or they won't switch to Linux" meme is getting *really* long in the tooth.  It's an example of what I call the "Infinity+1 Fallacy" or conundrum.  Basically, people will give up an effectively *infinite* amount of great free (speech and beer) software, give up control over their computer, and subject themselves to malware and bloat all for an effective trade of that +1 game.  

Is Infinity+1 *really* much better than simply Infinity?

Is the trade of liberties and control worth the bloat, malware and costs?

---

### Post by Murrquan on 2008-01-20
Have you tried installing the Windows version of Firefox under Wine, and installing the Shockwave plugin on that? Instead of installing IE under Wine.

I installed the Move Networks media player on the Windows version of Firefox (used by [http://www.byu.tv](http://www.byu.tv)), and it worked like a charm in Fedora. Although in Gutsy there was extensive sound skipping, I probably could've fixed that if I'd learned how to tweak it a bit.

---

