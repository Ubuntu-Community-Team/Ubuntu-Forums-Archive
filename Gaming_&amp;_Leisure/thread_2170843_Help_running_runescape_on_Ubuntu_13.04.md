---
title: "Help running runescape on Ubuntu 13.04"
date: 2013-08-27
forum: Gaming &amp; Leisure
---

### Post by kener2 on 2013-08-27
I recently bought a laptop for my little bro, the acer C7 chromebook. And surprise his favorite game cannot be played on Chrome OS because it doesnt allow Java I guess. But a friend suggested I put Ubuntu on it so I did. Downloaded 12.04LTS and upgraded the little thing to 13.04. Now Ive looked up a lot of resources to try playing the game such as downloading the client and the packages on synaptic but nothing seems to work.

The game client is useless and crashes after log in.
Firefox does the same thing as said above.
Chromium at least loads in mmmm about a quarter percent of the in game graphics and then freezes for eternity.

Ive noticed the sources I've come upon are all outdated as well and since this is runescape 3 is there a different run around I must do. Im beginning to think its the hardware, poor kid. But any help is much appreciated.

---

### Post by DarkAmbient on 2013-08-27
Not sure if this works with 13.04. Have you tried this?

```
sudo apt-add-repository ppa:hikariknight/unix-runescape-client
sudo apt-get update
sudo apt-get install perl p7zip unix-runescape-client
~/runescape/install-desktop-icons
```

You also need java if you haven't installed it already, i'd recommend openjdk.

```
sudo apt-get install openjdk-7-jre
```

---

### Post by oldrocker99 on 2013-08-27
This was typed and posted after DarkAmbient's post, so sorry for the duplication.

Runescape, eh? I am typing this on a C7, on which I can run a LOT of games: a bunch of stuff from the repos, including Warzone 2100 and MegaGlest (both pretty graphically-intensive games), a number of Desura games, including The Sparkle 2:Evo and Goodfolks (and, of course, Dominions 3;)), and a bunch of Steam Games, including Half-Life and its expansions, every Orange Box game, etc. 

Since it's a Java game, install openjdk, which should run it in a browser just fine. If you want to download it, Google "runescape linux" which will point you to a page which will tell you how to run it with wine, or how to install the native Linux client (which is a bit more complicated, since you have to compile it).

Good luck, and tell me how you did.

---

### Post by kener2 on 2013-08-28
yeah Ive already tried all that. The client loads faster than the browsers but it just freezes after logging in.

---

### Post by kener2 on 2013-08-28
thanks for the replies..Im still in the process of digging things up finding out how in the world to run this game lol. But in time I will find out I hope..

---

### Post by Zirts on 2013-08-29
RS is not java game anymore...  It uses HTML 5 . Just run it and it will work.

---

