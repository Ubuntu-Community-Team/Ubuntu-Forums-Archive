---
title: "Black Screen on OpenGL games"
date: 2009-05-12
forum: Gaming &amp; Leisure
---

### Post by eilam on 2009-05-12
Hello,

Im having some problems with W:ET on ubuntu.

Im a new linux user and i tryed looking up an answer here and on google but couldnt seem to find one.

Basicly what happens is i start the game and it loads but all i see is black.
I know it works becasue when i drop down the console and write /quit it actually quits.

Saw another guy here having the same problem with Doom3 and from my understanding the problem is resulotion and graphic cards..
I have GeForce 8800GT and Ive enabled nVIDIA accelerated graphic driver.

At first when i installed it, the game did load and everything was fine and then when i load my cfg it went black.
now when i load the default cfg it does work but its just unplayable :)

would love some help over here guys..

Thanks.

---

### Post by Shazaam on 2009-05-12
Just a few quick questions that may help you find an answer...
1. Do you have an LCD monitor connected? And how is it connected (analog or DVI)?
2. Are you trying to run in "windowed" mode or "full screen" mode?
3. Can you find the config file for your game in your home folder?
4. Have you reset the in-game video resolution to high or too low?

The reason I ask these questions is that I have an Nvidia card and a new LCD monitor (connected by an analog cable at the moment) and I run into the same problem as you with some games. A few games that try to run in full screen mode turn the screen black and the monitor osd pops up a message that reads "input out of range".
As far as the config file, usually you can find a listing for either a "windowed" mode (and/or screen size/resolution) or "full screen" setting you can change so that the game will run. Make sure you back up your original game config file first.

---

### Post by eilam on 2009-05-12
To answer your question:
1. Yes, i do have an LCD monitor connected [DVI].
2. Im running the game full screen.
3. The config file is in game's directory - /usr/..../enemy-territory/etmain
4. ET's default resolution is 800x600 but when i exec my own config which changes the resolution to 1440x900 then the screen turn black.

anyway im now playing with default config and it seem to be working even though it sucks :<

---

