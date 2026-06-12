---
title: "Thoughts on XFire-like features in linux"
date: 2009-02-09
forum: Gaming &amp; Leisure
---

### Post by maddog39 on 2009-02-09
Hey everyone,

As a long time linux gamer myself, I was thinking lately how much I've really been needing a lot of the features I used to use in xfire back in windows. There were a lot of things I particularly missed that were not chat specifically; those being: time tracking, favorite server management, and of course in-game chat. Lately I've been thinking about this issue alot, and how to solve it under Linux. Those 3 features of xfire are so critically important to the way I operate and communicate with my clan and others that I'm really becoming desperate to have them again.

Now we can already do things like manage our favorite servers under linux with tools like XQF, although in my experience they haven't really worked well. But what makes xfire's implementation so particularly useful is that it saves everything in the "cloud."

So recently I've become so enthrolled with trying to come up with a way to have these kinds of features on linux that I started to write a whole bunch of proof of concept code in Qt/Django to do time tracking. My thought was that the community could build our own top to bottom open source implementation of these kinds of features and have a sort of alternative to the xfire service itself.

But then I ran into a dilema because I thought, why dont we simply create our own implementation thats well integrated into linux that sits on top of the existing community and the existing infrastructure. Theres already quite a bit of information out there about the protocol and so forth, so perhaps we should make our own xfire client that works really well instead and has many of the same features as its Windows equivalent. I figure this is also a good idea because it could really drive more gamers to move to linux if they have a more well integrated xfire client and then we have the xfire community at our disposal.

So I have found xfire to be an extremely useful tool in the past as with many people I know and have a real need for an alternative or replacement on lnux. To be honest too, gFire doesnt really cut it, because its just chat and you dont get any of the extra benefits of using xfire. So im curious what everybody else thinks about this, firstly.  And secondly, what would be more beneficial for us to do, build our own system, or build a well integrated client for linux?

Just some thoughts, would love to hear others' opinions on this.

Thanks!
-Alec

---

### Post by Polygon on 2009-02-09
the hard part comes in that, unlike in windows, things in linux do not get installed to the same directory, usually

xfire works by just having a giant inf like configuration file showing the filepath to the games binary, and it searches all of the paths that it knows a game binary can be in, and if it finds a file there, then it marks that game as installed

however, on linux, the game might not be installed in the same place. Some people might have it in /usr/games, or like me, i keep my games in /home/markgames, and maybe some other person keeps it in /home/joe/Games. Some thinking is going to have to be done on how to get around this, either by specifying a directory where games are installed and just having it search and use md5hashing/filenames to put game binaries against a list to see which game that games belongs to...etc

and of course the staple of xfire, the concept they built themselves around in the early days is fast joining, as in you see your buddy is playing a game of X game, and you can see what server he is in (again hard, you have to figure out how to ping  and parse information from every time of videogame server out there....) and then you click a button, and somehow get the game to launch and join the server ip your buddy is in. I'm pretty sure for most cases this can be done by just adding parameters to the executable, like ./game +join_server 000.000.000.000 +password something

but otherwise its very possible. except for the last problem, we really dont have very many 'real' ' commercial' video games to support.

---

### Post by braveheart2 on 2009-02-10
> **Polygon said:**
> the hard part comes in that, unlike in windows, things in linux do not get installed to the same directory, usually

xfire works by just having a giant inf like configuration file showing the filepath to the games binary, and it searches all of the paths that it knows a game binary can be in, and if it finds a file there, then it marks that game as installed

however, on linux, the game might not be installed in the same place. Some people might have it in /usr/games, or like me, i keep my games in /home/markgames, and maybe some other person keeps it in /home/joe/Games. Some thinking is going to have to be done on how to get around this, either by specifying a directory where games are installed and just having it search and use md5hashing/filenames to put game binaries against a list to see which game that games belongs to...etc

and of course the staple of xfire, the concept they built themselves around in the early days is fast joining, as in you see your buddy is playing a game of X game, and you can see what server he is in (again hard, you have to figure out how to ping  and parse information from every time of videogame server out there....) and then you click a button, and somehow get the game to launch and join the server ip your buddy is in. I'm pretty sure for most cases this can be done by just adding parameters to the executable, like ./game +join_server 000.000.000.000 +password something

but otherwise its very possible. except for the last problem, we really dont have very many 'real' ' commercial' video games to support.

than make it so that you select the exact file path's that you have each game in, i think its a good idea.

---

### Post by chewit on 2009-02-10
Hi,

I'm a developer for Gfire!

Gfire does have some advanced features such as time tracker, works fine. Its not all about chat, which version are you using??? 0.1.0!?! :P

However, 0.8.0 coming soon will have even more great features. Like group chat, get info, improved game detection.

If you have any more questions, join our IRC channel!

---

### Post by maddog39 on 2009-02-10
> **Polygon said:**
> the hard part comes in that, unlike in windows, things in linux do not get installed to the same directory, usually

xfire works by just having a giant inf like configuration file showing the filepath to the games binary, and it searches all of the paths that it knows a game binary can be in, and if it finds a file there, then it marks that game as installed

however, on linux, the game might not be installed in the same place. Some people might have it in /usr/games, or like me, i keep my games in /home/markgames, and maybe some other person keeps it in /home/joe/Games. Some thinking is going to have to be done on how to get around this, either by specifying a directory where games are installed and just having it search and use md5hashing/filenames to put game binaries against a list to see which game that games belongs to...etc

and of course the staple of xfire, the concept they built themselves around in the early days is fast joining, as in you see your buddy is playing a game of X game, and you can see what server he is in (again hard, you have to figure out how to ping  and parse information from every time of videogame server out there....) and then you click a button, and somehow get the game to launch and join the server ip your buddy is in. I'm pretty sure for most cases this can be done by just adding parameters to the executable, like ./game +join_server 000.000.000.000 +password something

but otherwise its very possible. except for the last problem, we really dont have very many 'real' ' commercial' video games to support.
Not only are all these problems trivial, I've already solved them in my proof of concept code. :P I solved the problem by using an XML file with containing the full text name of each game and then a list of binary names they commonly have (without paths). Then I launch a QProcess (im using Qt 4) to run "ps -A -o comm" and split the output by \n and cycle through all the names of the running programs searching for a match. If a match is found, it breaks out of the loop and emits a gameStarted signal. This runs forever, once every second, until the application quits. The class that monitors this also runs in a separate thread (of course).

Parsing game server data to get information about number of players, list of players, server cvar settings, etc is not very hard. In fact there is alot of open source code already written out there that implements the majority of them. On top of that I also found documentation for many of the most popular protocols/engines. To let people launch games I was just going to have a little interface that lets them setup run commands for specific games if they wanted to launch them.

> **chewit said:**
> Hi,

I'm a developer for Gfire!

Gfire does have some advanced features such as time tracker, works fine. Its not all about chat, which version are you using??? 0.1.0!?! :P

However, 0.8.0 coming soon will have even more great features. Like group chat, get info, improved game detection.

If you have any more questions, join our IRC channel!
To be honest with you, I don't really consider those features to be 'advanced' by any means and gfire is still missing many of my most used features. Gfire still doesnt support clan friends in your buddy list, nor favorite game servers. Also, in-game chat, looks highly unlikely from what I've been able to find on your forums/site/bug tracker. Then not only does time tracking not work (in my experience), but its requires work to get going and is severely limited by the XQF requirement.

I've known Sam Jordan for quite a long time and I know that he works with you guys and hosts your wiki, etc. He's the one who originally told me about game detection in gfire and told me how he got it working. He also pointed me to a wiki article about it on the gfire wiki. Except that, the wiki really isnt clear about some things, and at the end of the day after many attempts at toying with it, I still havent been able to get it work. I even went so far as to start digging into the source code to try and decipher what exactly gfire is trying to do. What I discovered in the source code gave me some new ideas to try, but still no luck.

Also, I just wanted to say that I have posted quite a bit of feedback concerning a bunch of things on your forums and on your bug tracker. So far there hasnt been much of a response and some important features I just mentioned dont seem like they will ever be implemented, or are only planned for the distant future. This basically sums up all my frustrations with gfire and why I consider it inadequate as an xfire alternative on linux. I would be perfectly willing to work on it with you but this problem needs to be solved, is all im saying. I propose to make my own client if need be.

-Alec

---

### Post by chewit on 2009-02-11
I'm very surpised you were unable to get game time tracker to work. Your the first person I know who has had this many issues. Everyone we have helped, had got their issue fixed. If you are unable to get game time tracker to work, cant see how your going to make your own client :P .

As I have said, in 0.8.0, much improved game detection is included as well as auto game detection.

Clan friends is coming!

Favourite server maybe coming soon!

Ingame chat maybe possible with the use of opengl

So it seems u dont need to make your own client. All we need is people to stop complaining (its a OS project not micrsoft!) and help us out.

---

### Post by Polygon on 2009-02-12
> **maddog39 said:**
> Not only are all these problems trivial, I've already solved them in my proof of concept code. :P I solved the problem by using an XML file with containing the full text name of each game and then a list of binary names they commonly have (without paths). Then I launch a QProcess (im using Qt 4) to run "ps -A -o comm" and split the output by \n and cycle through all the names of the running programs searching for a match. If a match is found, it breaks out of the loop and emits a gameStarted signal. This runs forever, once every second, until the application quits. The class that monitors this also runs in a separate thread (of course).

that seems to work well, but what about games that are different, but use the same binary name? One good example is source engine games, all source engine games with the exception of left 4 dead, ALL use the binary name hl2.exe.....so if you just search by file name, that still only narrows it down to a pretty large list, it seems to me that your going to have to at least check some paths or something. But since steam does not exist on linux you don't need to worry about stuff like that...yet =)

and also, if the goal of the project is just to intergrate the basic features of xfire (game detection, chat, clan list support, etc) then i would suggest building a plugin (for pidgin/telepathy) rather then building a entirely new client.

---

### Post by ShooterKI on 2009-03-08
i have become extremely interested in G-Fire however, after installation i cannot login...i am using 8.10 "Intrepid" and i cannot tell u the number version of my pidgin however i can tell that at this time it is the most up to date version. please help me.

---

