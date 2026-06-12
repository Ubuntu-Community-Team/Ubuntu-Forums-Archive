---
title: "testers needed: TuxFighter version 0.54"
date: 2008-02-24
forum: Gaming &amp; Leisure
---

### Post by HorstJENS on 2008-02-24
Hi gamers,

just released a new version of my TuxFighter game. It is just a minor release, but i am glad for anyone who helps me testing it.

Main questions: does the .deb file work at your system ?
[I](i still search for experts who know how to make a perfect .deb package from a python program. - my .deb package is rather messy).
[/I]
does the credit screen works at your system ?

the game needs python and pygame to be installed. Tested with Ubuntu Gutsy and Windows XP.

download from:
[SIZE="3"]
[http://pygamebook.sf.net](http://pygamebook.sf.net)[/SIZE]

new in this version: Fullscreen support, joystik support, minor bug fixes, headshots better visible.

screenshot:
[IMG]http://pygamebook.sourceforge.net/Screenshot_bomb.png[/IMG]

---

### Post by HorstJENS on 2008-02-25
re-uploaded debian package, should work better now.

---

### Post by josh92176 on 2008-02-25
Congrats on the game it is quite fun, the deb works fine, It installed the correct dependencies and put the game in games menu. My system is a 32bit near clean ubuntu install. A nice feature would be if possible to hide the bar at the top of the window and make it automatically on top of the taskbar.

But overall well done.

-josh

---

### Post by HorstJENS on 2008-02-26
Hi Josh,
thanks for your feedback. I'm glad the .deb worked, i had troubles with it.


There is a fullscreen mode selectable (hidden under the menu "Screen resolution". Is that what you mean ? I could turn on fullscreen-mode by default for the next release. Do you think that would be meaningful ?

greetings,
-Horst

---

### Post by josh92176 on 2008-02-26
Aah, yes that is what I meant. Personally I would make it the default but I'm not sure what other people would want.

I havn't yet found any bugs but I will let you know if I do.

-josh

---

### Post by Het Irv on 2008-02-26
I am planning on taking a look at it later (e.g. when I can get to Ubuntu and have some free time.)  Looks good from screen cap, the only thing I can see so far is that the onscreen instructions are behind the game elements, just a minor annoyance.

---

### Post by Zaphod on 2008-02-26
.deb worked fine for me :)

---

### Post by josh92176 on 2008-02-26
That doesn't happen in fullscreen

-josh :)

---

### Post by Het Irv on 2008-02-26
> **josh92176 said:**
> That doesn't happen in fullscreen

-josh :)
Was that for me? Right now I am planning on getting around to testing Thursday night.

---

### Post by Crafty Kisses on 2008-02-26
> **HorstJENS said:**
> Hi gamers,

just released a new version of my TuxFighter game. It is just a minor release, but i am glad for anyone who helps me testing it.

Main questions: does the .deb file work at your system ?
[I](i still search for experts who know how to make a perfect .deb package from a python program. - my .deb package is rather messy).
[/I]
does the credit screen works at your system ?

the game needs python and pygame to be installed. Tested with Ubuntu Gutsy and Windows XP.

download from:
[SIZE="3"]
[http://pygamebook.sf.net](http://pygamebook.sf.net)[/SIZE]

new in this version: Fullscreen support, joystik support, minor bug fixes, headshots better visible.

screenshot:
[IMG]http://pygamebook.sourceforge.net/Screenshot_bomb.png[/IMG]

I'll give it a shot. :)

---

### Post by SOULRiDER on 2008-02-26
Ill check it out, but mostly im interested in reading the code, theres a few things i could learn :)

---

### Post by HorstJENS on 2008-02-27
Thanks for the testing, guys !
It's true, game instructions that hide behind evil enemy sprites look stupid... i have to do soemthing about it in the next release. Thanks for pointing me to it, i really never thougt much about it.

---

### Post by HorstJENS on 2008-02-27
SOULRider:

Please don't learn any bad habits from looking too much into my code. It was my first pygame-game and i developed it by playing around with the "aliens" demo in the pygame documentation. 

Someday i will have to rewrite it from scratch and i'm sure it will be more elegant and only half the size.

To really learn from the masters, look at the various games on the pygame website [www.pygame.org](www.pygame.org).

Will McGugan released a chapter of his excellent pygame book into the wild that you can find here: [http://www.apress.com/book/downloadfile/3765](http://www.apress.com/book/downloadfile/3765)

---

