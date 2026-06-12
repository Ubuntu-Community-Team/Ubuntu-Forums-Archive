---
title: "Need to find a game"
date: 2008-12-23
forum: Gaming &amp; Leisure
---

### Post by xxB33zleBossXx on 2008-12-23
Does anybody know if there is a game like cabal online for ubuntu?  Because linux is awsome but i loved cabal and thats only for windows.

---

### Post by giantoz on 2008-12-23
it doesn't look like you can play it with wine...

there's a number of mmorpgs for linux; regnum online, planeshift... check em out [http://gaming.gwos.org/doku.php/games:mmorpg](http://gaming.gwos.org/doku.php/games:mmorpg)

you can also check [www.winhq.org](www.winhq.org) to see if one you like plays well that way...ive heard you can play wow, another one you may want to check out is perfect world [http://pwi.perfectworld.com/](http://pwi.perfectworld.com/)

---

### Post by dannytatom on 2008-12-23
giantoz, has planeshift improved over the last year or so?  I remember last time I played it, I roamed the are and didn't see on person.  I think I got stuck in a corner, too. :(

---

### Post by eragon100 on 2008-12-23
> **dannytatom said:**
> giantoz, has planeshift improved over the last year or so?  I remember last time I played it, I roamed the are and didn't see on person.  I think I got stuck in a corner, too. :(

The installer messed up my permission system, I couldn't use my desktop anymore.

I wouldn't recommend planeshift.

---

### Post by dannytatom on 2008-12-23
Hah, you replied just in time.  It's 94% downloaded.  Anyone else care to confirm this/share a fix before I mess somethin' up?

---

### Post by MonkeyBoy on 2008-12-23
> **xxB33zleBossXx said:**
> Does anybody know if there is a game like cabal online for ubuntu?  Because linux is awsome but i loved cabal and thats only for windows.

Most games of this type seem to fail because of the gameguard security which won't work on wine.  

However if you are looking for something similar then [Silkroad Online](http://www.silkroadforums.com/screenshots.php) may be worth a look.  It is another of those Asian micro-transaction, free-to-play MMORPGs and it is platinum in the wineappdb so should work almost flawlessly.

---

### Post by binbash on 2008-12-23
> **MonkeyBoy said:**
> Most games of this type seem to fail because of the gameguard security which won't work on wine.  

However if you are looking for something similar then [Silkroad Online](http://www.silkroadforums.com/screenshots.php) may be worth a look.  It is another of those Asian micro-transaction, free-to-play MMORPGs and it is platinum in the wineappdb so should work almost flawlessly.

silkroad online works perfect with wine (playonlinux script)

---

### Post by xxB33zleBossXx on 2008-12-23
Ya as far as linux gaming with cabal i think silk road might be as close as i get but how about mmorpg&#347; cus i like really open ended games and searched the web aimlessly many times but can find any

---

### Post by giantoz on 2008-12-23
> giantoz, has planeshift improved over the last year or so? I remember last time I played it, I roamed the are and didn't see on person. I think I got stuck in a corner, too. 

actually, thats exactly why I quit about 6 months ago.  I got stuck in some corner in the dead realm, but I did see people gather from time to time, so I figured that was just my own stupidity.  I'm glad to know now that it wasn't. :)

---

### Post by dannytatom on 2008-12-23
I didn't realize I made so many typos (are = area, on = one), til I read you quoting me. :(

Anyway, I got it installed last night with no problem (almost).  I ran the installer as root and let it do it's thing, it installed to /opt, then asked for me to set permissions.  If I didn't, only root and people in the "games" group could use it.  When ahead with it, after it installed I created a group named 'games,' and added myself to it then did:

```

sudo chown -R root:games /opt/PlaneShift

```

Everything works fine now.  Also, it's a pretty nifty game, I think.  It doesn't have a big userbase, but the fact that it's so centered around roleplaying keeps me interested.

---

