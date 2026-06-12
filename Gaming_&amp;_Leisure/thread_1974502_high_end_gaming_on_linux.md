---
title: "high end gaming on linux"
date: 2012-05-06
forum: Gaming &amp; Leisure
---

### Post by Pally1 on 2012-05-06
Hello everyone, i have a computer that can be considered a high end spec system. I have two hard drives one with windows and second one i decided to use for linux. Ive installed Kubuntu and it seems to be a great operating system overall. 

But i need to know. How will this OS fair with gaming? Im talknig about Games like Skyrim, Mass effect 3, Dragon age Origins and Dragon age 2, World of warcraft.

Im one of those people who play everything on Ultra settings when it comes to graphics, if its any less, i throw the responsible hardware into the the trash and rush to buy an upgrade.


Can this OS and wine Handle Mass effect 3 and World of Warcaft on max settings?


Thank you!

---

### Post by oldrocker99 on 2012-05-06
[www.winehq.org](www.winehq.org) should answer your questions. The people who create wine also have a purchasable product, CrossOver, which (sometimes) works better than wine, and, by the way, funds further development of wine, which is why I bought it.

And welcome to Linux! You won't regret it.

---

### Post by forrestcupp on 2012-05-06
You have to remember that Wine isn't perfect, and it won't run all Windows software. Some games will run very well, but it's not a good substitute for Windows. You shouldn't expect Linux to run Windows games any more than a Mac could. Sometimes we just get lucky.

Most people who want high end gaming dual boot and run the games in Windows.

---

### Post by juancarlospaco on 2012-05-06
Patience Steam is coming (read like a Game of Thrones voice).

So far there are some very good Indie games too.

---

### Post by synaptix on 2012-05-06
> **juancarlospaco said:**
> Patience Steam is coming.

Valve has stated like 58530498093534 different times that they were bringing Steam client natively to Linux, it never happened. :/

---

### Post by ammofreak on 2012-05-06
Hi ):P
Have an Asus gaming laptop, G73. I have dual booted it with 
Windows 7 & Ubuntu 10.04LTS (for development). Unfortunately, one has to stick with Windows for any gaming at this point. Neither EA or Steam (I have accounts with both) support Linux. I have my fingers crossed though....:)

---

### Post by HolgerB on 2012-05-06
GNU/Linux is not up to playing Windows games. Especially if they are the latest and most demanding. All those "emulation" options such as WINE, gametree Linux, Crossover and so on are a hit and miss. 

A decent system with multicore CPU and a performant graphic adapter will enable you to play a lot of older games and even some newer games if you are willing to sacrifice maximum performance and like to tinker. As already referenced Wines appDB gives you a good reference what to expect from each game but the next Wine version or game update can easily break everything that worked before.

Save your nerves and time ! Stay with Windows in dual boot. GNU/Linux is great for a lot of other things including most of your daily work but gaming is a grey area.

---

### Post by earthpigg on 2012-05-07
Keep the windows install that you already have.

---

### Post by ahso4271 on 2012-05-07
Try the X-Plane demo. This is very demanding on CPU, Graphics etc. If you turn up settings, you will bring down any OS to it's knees.

---

### Post by Erik1984 on 2012-05-07
> **earthpigg said:**
> Keep the windows install that you already have.

This. Wine is pretty good for older games but even old games don't always work. Actually it surprises me how many stuff DOES work in Wine but in the end it's no alternative platform for the triple A titles like BattleField 3.

---

### Post by Paddy Landau on 2012-05-07
A useful tip if you want to use Wine:

Wine can be a little complex to master, so instead I suggest you install [PlayOnLinux]("apt:playonlinux"). PlayOnLinux is a front-end to Wine, cleverly hiding its complexity.

---

### Post by htt-thalan on 2012-05-07
Adding to what more people have mentioned: WineHQ all the way. You can look up your game and see the possible and/or unresolved issues with your game of choice.

That said, World of Warcraft runs perfectly on Wine (sometimes even faster than on Windows) and I've played other games on it as well: Plants vs Zombies (via Steam!), Command & Conquer 3, etc. Some games (notably Unreal) have a native Linux engine as well.

I'm not a big fan of using frontends for Wine, I like to be able to see what is happening and (try to) resolve any issues myself - better for the learning process. I still using Windows for some gaming (because my company issued laptop runs it anyway) and have a PS3 on the side.

---

### Post by synaptix on 2012-05-07
> **Paddy Landau said:**
> A useful tip if you want to use Wine:

Wine can be a little complex to master, so instead I suggest you install [PlayOnLinux]("apt:playonlinux"). PlayOnLinux is a front-end to Wine, cleverly hiding its complexity.

I find it best to not use a frontend, and instead learn Wine itself. The problem with PoL is it doesn't always use the latest Wine version for games.

It may pull in say version 1.3 for a game, but a major fix for the game could be located in say 1.5.3 (latest dev).

As for as World of Warcraft goes, I find WoW ran better using the latest dev (1.5.3) over the Wine version PoL used (last I tried it still pulled 1.3 for WoW).

---

### Post by forrestcupp on 2012-05-07
> **synaptix said:**
> I find it best to not use a frontend, and instead learn Wine itself. The problem with PoL is it doesn't always use the latest Wine version for games.

It may pull in say version 1.3 for a game, but a major fix for the game could be located in say 1.5.3 (latest dev).

As for as World of Warcraft goes, I find WoW ran better using the latest dev (1.5.3) over the Wine version PoL used (last I tried it still pulled 1.3 for WoW).

Usually, if you're using the latest version of PlayOnLinux, it will use the best version of Wine for the app you're installing. I've noticed that sometimes there are regressions that make a certain app not work well, and PlayOnLinux knows to use the best older version instead of the newer one with regressions.

In my opinion, the best thing about PlayOnLinux is that it can easily manage several different versions of Wine, which is almost impossible to do manually. It's easy to do separate Wineprefixes, but actually using different versions of Wine is not an easy task, manually. Regressions are a pain in the backside.

---

### Post by Stewie2kill on 2012-05-08
> **synaptix said:**
> Valve has stated like 58530498093534 different times that they were bringing Steam client natively to Linux, it never happened. :/

Which times? The only times I ever heard were the times that Valve actually denied it - and I only ever heard that one time.

Valve has actually confirmed it this time and Valve and Ubuntu are in contact with eachother. Gabe expressed a large portion of hatred towards windows 8 as well (as I'm sure many people will).

As for the original post. Many of the games you listed depend heavily on the hardware that you have and how you go about installing Wine. The games you've listed will likely not run (good or at all) on Ubuntu (yet...*crosses fingers*). World of Warcraft is known to work almost flawlessly on Linux though - so at least there is that.

High End gaming and AAA titles are a dream for us right now and we're getting closer to having native versions but we aren't there yet.

As previously Stated Play-On-Linux is a decent way of pre-configuring wine, but it has some issues and you may find some headaches with it as I did. 

Steam, however, seems to run flawlessly for me on the latest version of wine under Ubuntu 12.04.

Be sure to check out the WineHQ site and read up some reviews on those games if you are interested in trying to install and configure them in Ubuntu under wine. However, if you're like me and you spend a relatively large portion of your time playing lots of different games with friends then your best bet is to dual boot (and or wubi installer) and keep windows until better support is garnered for Linux. 

WineHQ
[http://www.winehq.com]("http://www.winehq.com")

Best of Luck.

---

### Post by ahso4271 on 2012-05-08
> **Euroman said:**
> This. Wine is pretty good for older games but even old games don't always work. Actually it surprises me how many stuff DOES work in Wine but in the end it's no alternative platform for the triple A titles like BattleField 3.

Why? Rage for example runs flawlessly and as fast on Wine.

Crossing fingers about the talks of Canonical and EA. We should know more in the next days.

---

### Post by brainwash on 2012-05-08
> **ahso4271 said:**
> Why? Rage for example runs flawlessly and as fast on Wine.
Rage uses id's OpenGL based engine. So it should perform better than DirectX games.

---

### Post by earthpigg on 2012-05-08
> **brainwash said:**
> Rage uses id's OpenGL based engine. So it should perform better than DirectX games.

And, he already has windows installed on his computer. He gains nothing by axing it, and may stand to gain a bit by keeping it. Cost-benefit analysis clearly says to keep windows if you're a gamer and already have it.

---

### Post by gtayton@nextcom.ca on 2012-05-08
I would give my firstborn to see FSX able to run in Ubuntu !!

---

### Post by HolgerB on 2012-05-09
> **Paddy Landau said:**
> A useful tip if you want to use Wine:

Wine can be a little complex to master, so instead I suggest you install [PlayOnLinux]("apt:playonlinux"). PlayOnLinux is a front-end to Wine, cleverly hiding its complexity.
Yes, basically PoL is nice but you have to keep in mind that most PoL installation scripts are pretty static and rely on certain versions of a game they install. To my limited knowledge when using PoL it is good to understand how the script works in order to fix them if something breaks.

As anything which abstracts a more complex matter, PoL has to make some presumptions and is rather static.

I think it is very important to highlight this.

---

### Post by ahso4271 on 2012-05-09
> **gtayton@nextcom.ca said:**
> I would give my firstborn to see FSX able to run in Ubuntu !!


It does! I've running FSX fine with all default planes.

---

### Post by mastablasta on 2012-05-10
some really good advices in this thread. to the OP and in general about PoL and state of gaming.
 
> It does! I've running FSX fine with all default planes.
 
@**gtayton@nextcom.ca** - we know now where you kid will go .... :twisted:

---

### Post by Posibile on 2012-05-11
Having been a Windows user as well as a hardcore gamer since I was very young, I was a tad depressed when I realised the gaming support was so poor for Linux. 

I hope Steam does finally complete their port to Linux, at least I'll have SOMETHING to work with (or some kind of game/app to stress my rig with :O )

I guess a dual boot is all I can do to run BF3/Skyrim etc. 

Alas! We can dream!

---

### Post by ahso4271 on 2012-05-11
Did you have a look here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13667](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13667)

---

### Post by donkyhotay on 2012-05-12
> **Posibile said:**
> I hope Steam does finally complete their port to Linux, at least I'll have SOMETHING to work with (or some kind of game/app to stress my rig with :O )!

Why? Steam on linux does not mean that any of the games will be compatible with linux.

---

### Post by Zeven on 2012-05-13
> **donkyhotay said:**
> Why? Steam on linux does not mean that any of the games will be compatible with linux.

People always say that but then forget that Valve isn't just bringing Steam to Linux, but also the Source Engine and is currently working on Left 4 Dead 2 with likely more Source Engine based games to follow.

---

### Post by Helios747 on 2012-05-14
> **synaptix said:**
> Valve has stated like 58530498093534 different times that they were bringing Steam client natively to Linux, it never happened. :/

[http://www.geekosystem.com/steam-coming-to-linux/](http://www.geekosystem.com/steam-coming-to-linux/)

Really now?

---

### Post by forrestcupp on 2012-05-15
> **Zeven said:**
> People always say that but then forget that Valve isn't just bringing Steam to Linux, but also the Source Engine and is currently working on Left 4 Dead 2 with likely more Source Engine based games to follow.

Do you have a reliable reference that says that they are porting the Source Engine? Even if that's true, and they are working on Left 4 Dead 2, each game will have to be ported individually. So porting the Source engine will not magically make all Source games work in Linux.

---

### Post by GWBouge on 2012-05-15
> **forrestcupp said:**
> Do you have a reliable reference that says that they are porting the Source Engine?

I can't confirm the reliability of each individual source, but collectively they must count for something:

[http://www.phoronix.com/scan.php?page=article&item=valve_linux_dampfnudeln&num=1]("http://www.phoronix.com/scan.php?page=article&item=valve_linux_dampfnudeln&num=1")
[http://www.extremetech.com/gaming/127475-valve-confirms-steam-and-source-for-linux-signals-low-confidence-for-windows-8]("http://www.extremetech.com/gaming/127475-valve-confirms-steam-and-source-for-linux-signals-low-confidence-for-windows-8")
[http://www.geek.com/articles/games/valve-is-porting-steam-and-the-source-engine-to-linux-20120425/]("http://www.geek.com/articles/games/valve-is-porting-steam-and-the-source-engine-to-linux-20120425/")
[http://www.techspot.com/news/48335-valve-confirms-steam-and-source-engine-for-linux.html]("http://www.techspot.com/news/48335-valve-confirms-steam-and-source-engine-for-linux.html")


> **forrestcupp said:**
> Even if that's true, and they are working on Left 4 Dead 2, each game will have to be ported individually. So porting the Source engine will not magically make all Source games work in Linux.

According to the articles, the port has been going on for a while, but as more of a 'in your spare time' type thing.  But, they've finally put someone in charge of the whole deal, so we can only hope it can get cranked out sometime this year.  While it'll still take a while to move existing games over (I think I read in one of those that Half-Life 2 and Portal were after Left 4 Dead 2), having the native engine in place sure will help get some good, new titles coming our way.

---

### Post by xedi on 2012-05-15
> **GWBouge said:**
> I can't confirm the reliability of each individual source, but collectively they must count for something:

They all have Phoronix as the source so you can count them as a single as a single source.

---

### Post by GWBouge on 2012-05-15
Bah, I noticed they all mentioned Larabel's visit, didn't quite realize they were all based off of it.  Been up too long, I just skimmed them, heh.

---

### Post by forrestcupp on 2012-05-16
> **xedi said:**
> They all have Phoronix as the source so you can count them as a single as a single source.

That's how it has always been for anything about Steam or Source. Everything out there used Phoronix as their source. I hope it's true, but I'm not holding my breath.

---

