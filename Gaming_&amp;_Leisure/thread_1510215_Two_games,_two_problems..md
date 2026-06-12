---
title: "Two games, two problems."
date: 2010-06-15
forum: Gaming &amp; Leisure
---

### Post by MikeB214 on 2010-06-15
There are two games that I've been trying to install and play for a couple days now, but I can't seem to get them running properly. 

1) Wolfenstein: Enemy Territory - Whenever I load this game normally (through the shortcut) I can not connect to any servers at all. Nor can I create my own server and run it. The only way to get it to work is by using...
> cd /usr/local/games/enemy-territory
sudo ./et
each and every time. 

I'm also trying to figure out how to install bots into the game. Help with that is kind of secondary, but if you know what to do, any and all help is appreciated.

2) CoD: Modern Warfare, using Wine1.2 - After installing it the first time, it crashed right after saying "setup.exe has encountered a serious problem". Trying to re-install it on top of itself has lead to the Terms of Agreement text not appearing and on the start of the install it crashes with the same message as before.

Notes on MW: I have installed d3dx9_34 and added it to the Libraries tab. No changes.

---

### Post by Dougie187 on 2010-06-15
For the wolfenstein problem, it sounds like a network problem. Maybe you have iptables or a firewall filtering the ports?

For the CoD problem, did you go through this thread?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

---

### Post by MikeB214 on 2010-06-15
Yeah, I've gone there. I'm not sure what I'm looking for in that link, though. Beside not to install Punkbuster.

---

### Post by Dougie187 on 2010-06-15
> **MikeB214 said:**
> Yeah, I've gone there. I'm not sure what I'm looking for in that link, though. Beside not to install Punkbuster.

Well, the thread says you have to patch wine for the game to work. Did you do that? There appears to be several steps before the game works.

---

### Post by MikeB214 on 2010-06-15
I'm not exactly sure how to patch it. I see the instructions at the bottom, but I'm a new Xubuntu user and I'm very unfamiliar with it.

---

### Post by Dougie187 on 2010-06-15
Well, I don't have the game, so I can't help you test it or anything, but if you scroll down to the section labeled "How To Make Punkuster Work", there are instructions right there that should help you out.

Basically, you have to download the source for wine. Apply the patch to the source, compile the source, and install the source. Then you should be able to install modern warfare and play it.

The instructions say download the source and patch it. The three links above the instructions are the three patches you need to apply to the source. Though I don't see 1.1.5 in their source, so maybe just try the source for 1.2.
[http://sourceforge.net/projects/wine/files/Source/wine-1.2-rc3.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.2-rc3.tar.bz2/download)

---

