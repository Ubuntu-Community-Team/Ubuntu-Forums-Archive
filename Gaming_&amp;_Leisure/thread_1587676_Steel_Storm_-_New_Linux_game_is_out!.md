---
title: "Steel Storm - New Linux game is out!"
date: 2010-10-04
forum: Gaming &amp; Leisure
---

### Post by motorsep on 2010-10-04
Hi Ubuntu community!
We have released our first game few weeks ago and it's native to Linux. It was developed on Ubuntu!!!
I hope you guys like old school top-down action :)
The game is titled Steel Storm Episode I and is available for free at [http://www.steel-storm.com](http://www.steel-storm.com) (it's not FOSS; only the engine is under GPL).
Currently 4 official game servers are running, 2 in EU and 2 in US.
The game is shipped with single-player and multi-player (DM and Coop).
I hope you will enjoy it.

---

### Post by Naiki Muliaina on 2010-10-04
Played it to near the end single player, when I gave it a go there was a bug that stopped me near the end. That was a month ago though? Must re try :) They seemed pretty on the ball so doubt the bugs still there :)

---

### Post by Rustybolts on 2010-10-04
Great game, highly polished graphics, nice feel to the controls, will be buying episode 2 when available.

---

### Post by Shazzner on 2010-10-04
Cool game, I noticed you said you developed this on ubuntu, could you talk about some of the utilities and steps you went through to make it? Like how is working on the darkplaces engine like? What level mapper did you use etc? Anything you didn't like?

---

### Post by motorsep on 2010-10-04
Thanks guys!
@ Shazzner: Sounds like an interview to me ;) Or post-mortem. Or both :D
We can do that, yes. Where is it going to be published though?

---

### Post by Shazzner on 2010-10-04
> **motorsep said:**
> Thanks guys!
@ Shazzner: Sounds like an interview to me ;) Or post-mortem. Or both :D
We can do that, yes. Where is it going to be published though?

Ah in that case, I would love for you to talk about it, but I would refer you to these sites as they have the most visibility when it comes to linux and gaming:
[http://www.ubuntugamer.com/](http://www.ubuntugamer.com/)
[http://www.gamingonlinux.info/](http://www.gamingonlinux.info/)
[http://linuxgamingnews.org/](http://linuxgamingnews.org/)

Just tell them Shazzner sent you ;)

---

### Post by Vrroom on 2010-10-05
> **motorsep said:**
> Thanks guys!
@ Shazzner: Sounds like an interview to me ;) Or post-mortem. Or both :D
We can do that, yes. Where is it going to be published though?
I wrote about the game on my blog and the response has been great so far. 
[http://www.ubuntuvibes.com/2010/10/addictive-linux-game-steel-storm.htm]("http://www.ubuntuvibes.com/2010/10/addictive-linux-game-steel-storm.html")l
Someone submitted on reddit too: [http://www.reddit.com/r/linux/comments/dmm8e/addictive_linux_game_steel_storm_episode_1/]("http://www.reddit.com/r/linux/comments/dmm8e/addictive_linux_game_steel_storm_episode_1/")

---

### Post by ELD on 2010-10-06
> **Shazzner said:**
> Ah in that case, I would love for you to talk about it, but I would refer you to these sites as they have the most visibility when it comes to linux and gaming:
[http://www.ubuntugamer.com/](http://www.ubuntugamer.com/)
[http://www.gamingonlinux.info/](http://www.gamingonlinux.info/)
[http://linuxgamingnews.org/](http://linuxgamingnews.org/)

Just tell them Shazzner sent you ;)

Wow my site (gamingonlinux) is gaining some traction then :).

I did post about it before, but now i see it's the full release i think a new post is needed!

---

### Post by Landior on 2010-10-06
downloading it now, will let you know what i think later:)

---

### Post by Landior on 2010-10-06
just tried the game, quite liked it, need to play it more :) when will there be more episodes?

---

### Post by Rob2687 on 2010-10-06
It doesn't respond to mouse clicks. I am using Maverick RC. The mouse moves and the menu items get highlighted but clicking does nothing.

In game is the opposite. I can left click to fire but I can't control move the mouse to control the unit. It just spins in a circle.

---

### Post by Shazzner on 2010-10-06
> **Rob2687 said:**
> It doesn't respond to mouse clicks. I am using Maverick RC. The mouse moves and the menu items get highlighted but clicking does nothing.

In game is the opposite. I can left click to fire but I can't control move the mouse to control the unit. It just spins in a circle.

I just went back after upgrading to Maverick RC to see if anything had broken but it all checks out. Can you post anymore info?

---

### Post by Rob2687 on 2010-10-06
I'm not sure what other info I can post. I am using the xorg-edgers ppa to get the radeon gallium driver. It's not really an option to use the r300 classic driver because the 3D driver on gallium is light years better than classic.

---

### Post by ELD on 2010-10-06
No doubt the open source drivers are your problem. Official ATI drivers always work better.

---

### Post by motorsep on 2010-10-06
Try launching the game as following:
./steelstorm +joy_enable 0 (or steelstorm64, depending on your system)

Also try fullscreen mode.

---

### Post by Rob2687 on 2010-10-06
In fullscreen it loses the mouse completely (can't move it at all).

The option +joy_enable 0 fixes the mouse in the menus. In game it does not spin out of control anymore but it still does not give any directional control (can still click to fire).


I am using a wireless keyboard/mouse set. There are no other input devices(gamepads or joysticks) on this system. Dunno if this is any use but here's my xinput list.
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver V1.0    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver V1.0    id=8    [slave  keyboard (3)]


---

### Post by volneilo on 2010-10-07
**Rob2687**, I'm facing the same problems as you. Have NVidia graphics here, proprietary drivers enabled, under Lucid 32bit. Using wireless mouse & keyboard too, by the way.

PS: Launching with "./steelstorm +joy_enable 0" did the trick for me. Everything works ok now.

---

### Post by tito_torrisi on 2010-10-19
I have the same problem, the mouse does not work in the menu (in fullscreen) AND it does not work in game mode, I can fire, but I can't move the ship!
The given command does not solve anything...

What can we do?

---

### Post by ubudog on 2010-10-19
Will try it out.  Sounds cool.  Thanks for posting. :)

---

### Post by motorsep on 2010-10-19
> **tito_torrisi said:**
> I have the same problem, the mouse does not work in the menu (in fullscreen) AND it does not work in game mode, I can fire, but I can't move the ship!
The given command does not solve anything...

What can we do?

No idea. I need a trace back or at least what's in the terminal (all of it). Try updating video drivers.
Might want to check mouse sensitivity.
If you use WASD, does player move?

---

### Post by Perfect Storm on 2010-10-20
Quite fun. But I get emotion sickness after 30 min - it rarely happens :-/

---

### Post by motorsep on 2010-10-20
A new version is out! It has 4 camera modes, so you choose how you play the game! Also it has gamepad support and difficulty selector. If you are going to do clean full install (or rather clean untar ;) ), remove older version first, to avoid any incompatibilities and conflicts.
Thank you.

---

### Post by Valthar on 2010-10-20
Not really my style of game, but I enjoyed it all the same.

When I get home I will be pre ordering episode 2 to show some love for the native linux version.

---

### Post by ELD on 2010-10-20
Downloaded the new version, gonna play around with the camera and see what it's like.

Also for anyone interested (the makers maybe?) there's people chatting about it here on my site -> [http://www.gamingonlinux.info/community/viewtopic.php?f=6&t=46](http://www.gamingonlinux.info/community/viewtopic.php?f=6&t=46)

I also added it to the database for you :) [http://www.gamingonlinux.info/item.php?iid=61](http://www.gamingonlinux.info/item.php?iid=61)

---

### Post by Valthar on 2010-10-20
I am actually having an issue lauching the game.

If I launch it from the terminal by navigating to the folder it is in everything works fine..

But I added an application to my menu and directed the command to the steelstorm64file via

/home/name/games/steelstorm/steelstorm64

and the game takes up the entire screen and gives me an error

the game gives me the option to look in the console and i see this error

/home/darren/games/steelstorm/steelstorm64 is not a pk3 file

So i can run the game, I just can't get my menu shortcut to work.

---

### Post by motorsep on 2010-10-20
try this for the command field of your app launcher:
/home/_your_user_name_/games/steelstorm/steelstorm64 -basedir /home/_your_user_name_/games/steelstorm/

Don't forget to mark "Allow to execute"

---

### Post by Shazzner on 2010-10-20
> **Artificial Intelligence said:**
> Quite fun. But I get emotion sickness after 30 min - it rarely happens :-/

That must be quite a story telling if you make some emotion sick!

---

### Post by Perfect Storm on 2010-10-20
> **Shazzner said:**
> That must be quite a story telling if you make some emotion sick!

Hahahaha :popcorn:

---

### Post by Valthar on 2010-10-20
> **motorsep said:**
> try this for the command field of your app launcher:
/home/_your_user_name_/games/steelstorm/steelstorm64 -basedir /home/_your_user_name_/games/steelstorm/

Don't forget to mark "Allow to execute"

That did it!

I dont understand why I had to do that though, wasn't it just repeating the directory path?

---

### Post by M!K3_$ on 2010-10-20
downloading now. looks fun. :)

---

### Post by motorsep on 2010-10-20
> **Valthar said:**
> That did it!

I dont understand why I had to do that though, wasn't it just repeating the directory path?

That's just how it is :)

---

### Post by tito_torrisi on 2010-10-23
> **motorsep said:**
> No idea. I need a trace back or at least what's in the terminal (all of it). Try updating video drivers.
Might want to check mouse sensitivity.
If you use WASD, does player move?

I downloaded the newer version of the game and now everything is working as it should!!

Thank you! :D

---

### Post by motorsep on 2010-10-23
I am glad it all worked out :)

---

### Post by ubudog on 2010-10-26
One of the best Linux games out there.  I will buy Episode 2.  (Once I get the spare change :lolflag:)

---

### Post by DooM55 on 2010-10-26
[http://www.linuxgames.com/](http://www.linuxgames.com/)

[http://games.linux.sk/](http://games.linux.sk/)
very good site  :guitar:

---

### Post by motorsep on 2010-10-26
Well, just like many other sites linuxgames hypes up MineCraft. 
The other site doesn't have Steel Storm covered either.

What we really need is to get onto Software Center.

Thank you for your support guys! It seems that Linux community has been the most supportive one.

---

### Post by Legeril on 2010-10-27
I have downloaded this game, but I don't know how to install it.

I have the .tar.gz archive in my Downloads folder

---

### Post by ubudog on 2010-10-27
> **Legeril said:**
> I have downloaded this game, but I don't know how to install it.

I have the .tar.gz archive in my Downloads folder

Double click it, extract it, double click the steelstorm folder, double click on "steelstorm".  It should run then.

---

### Post by Legeril on 2010-10-27
I see, thank you

---

### Post by ubudog on 2010-10-27
> **Legeril said:**
> I see, thank you

NP, it works, right?  There are also some other files in there, like 64bit versions I think.

---

### Post by motorsep on 2010-10-27
Copy .tar.gz file into /home/_your_user_name_/games/ (or into /home/_your_user_name_/ )

Open terminal. Type:

cd /home/_your_user_name_/games/ (or cd /home/_your_user_name_/) and hit Enter

tar xvfz steelstorm-ep1-v10001723.tar.gz and hit Enter

cd steelstorm/ and hit Enter

./steelstorm and hit Enter (or ./steelstorm64 and hit Enter)


That's the best way of doing it.

---

### Post by ubudog on 2010-10-27
> **motorsep said:**
> Copy .tar.gz file into /home/_your_user_name_/games/ (or into /home/_your_user_name_/ )

Open terminal. Type:

cd /home/_your_user_name_/games/ (or cd /home/_your_user_name_/) and hit Enter

tar xvfz steelstorm-ep1-v10001723.tar.gz and hit Enter

cd steelstorm/ and hit Enter

./steelstorm and hit Enter (or ./steelstorm64 and hit Enter)


That's the best way of doing it.

Or that. :guitar: Actually easier. :)

---

### Post by babai on 2010-10-27
This game has a major memory leak issue(especially when playing the latter levels), the game takes whole of my 1gb ram and swap kicks in.

---

### Post by motorsep on 2010-10-27
How did you figure it out, genius?
As I am writing this, my memory usage is 900+ Mb. And all I have is FF opened and IRC chat.
The game's engine is somewhat similar to iD Tech 4 (Doom 3, Quake 4, Prey, ETQW) and has high quality assets. As you load latter levels, the game has to load up all the enemies and huge level and high quality textures into RAM.
So instead of saying, without having facts, that game has memory leaks issues, just get more RAM :)

---

### Post by ELD on 2010-10-27
> **motorsep said:**
> How did you figure it out, genius?
As I am writing this, my memory usage is 900+ Mb. And all I have is FF opened and IRC chat.
The game's engine is somewhat similar to iD Tech 4 (Doom 3, Quake 4, Prey, ETQW) and has high quality assets. As you load latter levels, the game has to load up all the enemies and huge level and high quality textures into RAM.
So instead of saying, without having facts, that game has memory leaks issues, just get more RAM :)

This 1GB RAM really isn't much if you want to play games better than worms clones...

---

### Post by motorsep on 2010-10-27
> **babai said:**
> This game has a major memory leak issue(especially when playing the latter levels), the game takes whole of my 1gb ram and swap kicks in.

If you can not expand your RAM and yet, you want to play Steel Storm, turn down texture quality. Way down. That might help.

---

### Post by ubudog on 2010-10-27
> **motorsep said:**
> If you can not expand your RAM and yet, you want to play Steel Storm, turn down texture quality. Way down. That might help.

Thanks.  :)

---

