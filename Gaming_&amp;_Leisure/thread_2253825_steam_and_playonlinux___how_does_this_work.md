---
title: "steam and playonlinux   how does this work"
date: 2014-11-22
forum: Gaming &amp; Leisure
---

### Post by finny388 on 2014-11-22
I thought the advantage of playonlinux was that it housed different versions of wine and used the appropriate one for a given installation.

All of my games have been bought through Steam.

I've installed Steam from within pol and it runs smoothly but the two games I've tried fail to launch or crash (batman ark asylum ("System.NotImplementedException...."), stanley parable (try to move w/a/s/d and stutters and closes as if I exited))

Aren't all the games in Steam more or less invisible to pol? How does it intervene and use different wine versions?

am I doing this wrong?

:|

---

### Post by dannyboy79 on 2014-11-22
no, just because you got a game installed in steam within POL doesn't mean it's going to work. i don't believe any directX 10 or higher work in POL

---

### Post by finny388 on 2014-11-23
i'm not assuming POL waves a magic wand.

I'm hoping someone can explain how it works. It seems to me if I install Steam in POL then any game I install within Steam is going to be using the setup Steam is using on POL and not POL itself.

I found this link that implies that each game needs its own steam virtual drive.

[http://www.gamersonlinux.com/forum/threads/how-to-organize-your-steam-games-with-playonlinux.554/](http://www.gamersonlinux.com/forum/threads/how-to-organize-your-steam-games-with-playonlinux.554/)

I'm just brand new to this and wine. I've never set up a game in linux before. I bought a bunch of games on steam last summer, I've finally got a pc with the horsepower to run them, and I just don't know how to go about it.

---

### Post by oldrocker99 on 2014-11-23
I have had **some** success with POL running Steam for Windows, specifically Oblvion, Skyrim and The Witcher 2. I had no success with X-COM or Borderlands 2, but, of course, they have native Linux versions on Steam for Linux.

Wine is, remember, not a panacea. There will always be games and other Windows programs which cannot run under wine, no way, no how. The ones which do run can sometimes chug, and sometimes (once in a while) run better on Linux using wine than they do on Windows. Usually, they run acceptably well. See [https://appdb.winehq.org](https://appdb.winehq.org) to see how well a particular program can run.

PlayOnLinux is currently the best way to install Windows software, and they do a good job with their scripts, downloading the wine version that will best run the program, etc.

---

### Post by aquablue25 on 2014-11-24
Sup mate,

first of all - welcome to Ubuntu and the world of gaming via Wine.

I agree with Danny and Oldrocker in all but one point, which I will get into further below.

It would be nice of you to post some system details (hard- and software config) and the drivers you are using. Also, a copy of the complete error message you are getting would be nice too.

**About POL and what it does**

 POL basically creates a virtual environment where it downloads and installs a version of vanilla Wine ([www.winehq.org]("http://www.winehq.org")) that it will use for the installation of Steam or any other app. POL basically simplifies Wine by offering you a GUI + an isolated/seperate environment/bottle for you to use. It also offers you a simple way to install missing libraries and other programs into your virtual environment. Using vanilla Wine, you would have to do all of this stuff manually - via a terminal. POL also heavily relies on user-scripts, which you can see [here]("https://www.playonlinux.com/en/supported_apps.html").

**A word of advice**

These scripts are integrated right into the program and are part of the list you see when searching for an app to install. Using one of these scripts, POL knows what to download, install and even tweak for you. Everyone can jump in and create a script for others to use, which can be beneficial and also a bit dangerous at the same time. Why? Beneficial because ppl with knowhow can fix issues right away and share it with the community. Dangerous because a lot of scripts are not checked nor analysed by the POL team. Make sure to look out for these two warnings when browsing the list of available and supported apps:

     [B][I]"Warning
[/I][/B]

*This installer is a beta script. It means that it might not work as expected"*

and...

     [B][I]"Warning
[/I][/B]
[I]This update has not been approved yet by the team.
Use it at your own risk"[/I]

^ It's true though, POL and Crossover 14 both rely on scripts made by both; the devs and the community. But unlike Crossover from Codeweavers, POL offers its users scripts that have not been approved by their team yet. This does not only pose a security risk, but also means that things could go wrong during installation. Codeweavers, on the other hand, checks every single script alias Crosstie before it gets uploaded to the public via their website. The good thing though: Usually there is a copy of the changes/source code of the POL script to be read and if you know what to look for, you can check the script yourself before installing it. But that's something a newcomer won't be able to do or understand.

**About Steam and POL**

If you click on "system information" in Steam, you will notice that it won't directly recognize POL itself, but instead it will see the version of Wine the virtual drive is using. Ppl recommend different things and your experience may vary, but I also recommend using one bottle per app or game. You can also manually change the version of Wine for your Steam bottle, if you wish to do so.

It's also true that installing Steam via POL won't magically make every game run. While Steam should download and install all of the necessary files that a game needs (directx, .net framework, visuall c++ 2k etc.), that won't be enough sometimes. In some rare cases, you might even need to look for system libs that POL needs or for other tweaks for a game to run successfully.

**Batman Arkham Asylum**

According to [this]("https://www.playonlinux.com/en/app-1077-Batman_Arkham_Asylum.html") site, Arkham needs .NET 3.5, but fails to use it somehow. This is also verified by checking WineHQ and Codeweavers. Quote: *"Not sure if this applies to the game without steam as well, but to be  able to run it in steam, install .NET framework and WINE Mono into the  bottle."*

**Final words - the point I don't agree with**

I disagree on the part that POL is suppose to be the _best_ way to install Windows software on Linux. While I understand why ppl might want to use POL (it's free and community driven), it remains a community project that not only mainly relies on the vanilla WineHQ project, but it's also missing the polish, technological features/advancements, support and security of its competitor: [Crossover 14]("https://www.codeweavers.com/compatibility/browse/name/?app_id=6152") (Arkham script + user ratings). Check out [this]("http://ubuntuforums.org/showthread.php?t=2253842") thread for more information on the subject. If POL is giving you a headache, there is nor harm done by downloading the Crossover trial and giving it a try with Steam and Arkham.

Quote from POL website: *"PlayOnLinux mainly relies on [WineHQ]("http://www.winehq.org") project. If you want help them and to get a professional support of wine, please consider buying [codeweavers]("http://www.codeweavers.com/") products. We would also like to thank [ScummVM]("http://www.scummvm.org") and [DOSBox]("http://www.dosbox.com") projects"*

Cheers,
Aqua

---

### Post by oldrocker99 on 2014-11-24
> **aquablue25 said:**
> 
**Final words - the point I don't agree with**

I disagree on the part that POL is suppose to be the _best_ way to install Windows software on Linux. While I understand why ppl might want to use POL (it's free and community driven), it remains a community project that not only mainly relies on the vanilla WineHQ project, but it's also missing the polish, technological features/advancements, support and security of its competitor: [Crossover 14]("https://www.codeweavers.com/compatibility/browse/name/?app_id=6152") (Arkham script + user ratings). Check out [this]("http://ubuntuforums.org/showthread.php?t=2253842") thread for more information on the subject. If POL is giving you a headache, there is nor harm done by downloading the Crossover trial and giving it a try with Steam and Arkham.

Quote from POL website: *"PlayOnLinux mainly relies on [WineHQ]("http://www.winehq.org") project. If you want help them and to get a professional support of wine, please consider buying [codeweavers]("http://www.codeweavers.com/") products. We would also like to thank [ScummVM]("http://www.scummvm.org") and [DOSBox]("http://www.dosbox.com") projects"*

Cheers,
Aqua

I have used Crossover and PlayOnLinux, and, frankly, I have had better results with PlayOnLinux. I tried to install Steam for Windows so I could play Skyrim, and I was unable to play Skyrim, but when I installed Steam and downloaded Skyrim, it ran perfectly. I installed Oblivion from within the same Steam for Windows, and it runs perfectly too. I will also say that when I has a failed installation on some GOG game (can't remember the game), the script was fixed the next day.

Just sayin'.

---

### Post by finny388 on 2014-11-24
Thank you aqua and oldrocker.

Aqua, I won't be home for a few hours. Then I can provide more info.
It's a gigabyte H97N-wifi, i5 4590, and asus strix 970 w proprietary v343.22, using Kubuntu 14.10, plasma 4 and various kwin desktop effects enabled

I may very well try crossover (and likely, eventually, succoumbing and buying some version of Windows just for gaming) but before I do, something confusing about POL:

I thought maybe I have to install Steam under multiple versions of wine (one per bottle/virtual drive) and then install a particular game under the version of wine advised by wine's appdb.
e.g.
Steam1 - Wine v1.5.28 > Vampire Bloodlines
Steam2 - Wine v1.7.12 > Batman Ark
etc

I created a 2nd and a 3rd and in each case installed Steam with different wine versions. but when I go into POL the only Steam is the 3rd instance. If I go into config, all 3 virtual drives are there but only the 3rd has anything installed.

So it appears I have lost the login and installs done on the first instance of Steam.

Oldrocker, glad to hear skyrim worked, that is another I have that I can try.

In the meantime Half-Life 2 is working seamlessly in the native Steam app (ah to dream they could all be this way)

Here's the list of games. I've only tried stanley, bloodlines, batman ark, witcher 1. (witcher 1 was so close. EVERTHING worked except characters had no bodies or heads, just eyeballs and teeth)

1_Platform	Wine Rating	Wine Version	Game
Windows	1_Platinum	1.7.18	Mass Effect 1
Windows	1_Platinum	1.7.15	Mass Effect 2
Linux / Windows	2_Gold?	1.5.26 or 1.7.1	Witcher 2
Windows	3_Silver	1.6	Witcher Enhanced Ed. Dir Cut
Windows	1_Platinum	1.7.5	Bioshock
Windows	1_Platinum	1.4.1	Bioshock 2
Windows	5_Garbage	1.5.26	Bioshock Infinite
Linux / Windows	1_Platinum		Half-Life 2 Ep 1, Ep2, Lost Coast
Windows	3_Silver	1.7.12	Batman Arkham Asylum GOTY
Windows	2_Gold	1.7.10	Batman Arkham City GOTY
Windows	3_Silver	1.7.9	Batman Arkham Origins
Windows	1_Platinum	1.5.28	Vampire: The Masquerade - Bloodlines
Windows	1_Platinum	1.7.21	Elder Scrolls Skyrim
Windows	5_Garbage	1.7.7	Sleeping Dogs
Windows	3_Silver	1.6-rc5	Alan Wake
Windows	4_Bronze	1.5.13	Alan Wake's American Nightmare
Windows	1_Platinum	1.7.4	Stanley Parable
Linux / Windows	Not Found		Gone Home
Windows	2_Gold	1.6	Grand Theft Auto III
Windows	3_Silver	1.6-rc5	Grand Theft Auto: Vice City
Windows	1_Platinum	1.4	Grand Theft Auto: San Andreas
Windows	3_Silver	1.7.11	Grand Theft Auto IV
Windows	3_Silver	Probably	GTA IV: Eps Lib City (lost&damned, gay tony)

---

