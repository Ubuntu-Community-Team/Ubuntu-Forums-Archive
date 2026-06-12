---
title: "NAEV - 2D Space Combat / Trading Game"
date: 2009-09-22
forum: Gaming &amp; Leisure
---

### Post by Deiz on 2009-09-22
To quote the website, "NAEV is a 2D space trading and combat game, in a similar vein to Escape Velocity.

NAEV is played from a top-down perspective, featuring fast-paced combat, many ships and outfits, and a large galaxy to explore. The game is highly open-ended, letting players proceed at their own paces."

There's a handy package available at [**PlayDeb**](http://www.playdeb.net/updates/NAEV) and downloads are also available at our [Google Code page](http://code.google.com/p/naev/).

Screenshots:

[[img]http://naev.googlecode.com/svn/trunk/site/screenshots/0.4.0-beta1/naev0-small.png[/img]](http://naev.googlecode.com/svn/trunk/site/screenshots/0.4.0-beta1/naev0.png) [[img]http://naev.googlecode.com/svn/trunk/site/screenshots/0.4.0-beta1/naev1-small.png[/img]](http://naev.googlecode.com/svn/trunk/site/screenshots/0.4.0-beta1/naev1.png)

Gameplay videos are at Youtube, both [early](http://www.youtube.com/watch?v=MW4OoN4tY8s) and [late](http://www.youtube.com/watch?v=8EO9lmUf9Gg) game. Recorded with glc, which is an awesome piece of software.

0.4.0 is fresh out of the oven, released on September 18th. The [Changelog](http://code.google.com/p/naev/wiki/Changelog) is available for those interested.

Code and data are, of course, completely free. GPLv3 code, various licensing on the media (GPLv2, GPLv3, PD, CC-By (and -SA) 3.0).

Our primary communication method is IRC, **[#naev on Freenode](http://webchat.freenode.net/?channels=naev)**.

---

### Post by NewlyHuman on 2009-09-24
Wow! This is too cool. I spent way too many afternoons playing Escape Velocity back when it came out.

Spent about an hour playing so far; I died a lot, but I'm liking it. Seems to be a little short on missions, but I guess that'll fill out in time. I had some weird issues when I enabled VBOs (Intel drivers, I guess?) but they don't happen when VBOs are disabled.

Thanks for the link! :)

---

### Post by donkyhotay on 2009-09-24
I'll have to check it out. I used to love playing escape velocity on my friends mac 15-20 years ago.

---

### Post by ubudog on 2009-09-24
Looks like a cool game! Might get it. Thanks!

---

### Post by Deiz on 2009-09-25
> **NewlyHuman said:**
> Wow! This is too cool. I spent way too many afternoons playing Escape Velocity back when it came out.

Spent about an hour playing so far; I died a lot, but I'm liking it. Seems to be a little short on missions, but I guess that'll fill out in time. I had some weird issues when I enabled VBOs (Intel drivers, I guess?) but they don't happen when VBOs are disabled.

Thanks for the link! :)

Regarding missions, that's one of the main things we're lacking. Plenty of work has gone into graphics, sound and features, but there haven't been any new campaigns in months.

The latter issue's known about, the drivers are 100% responsible for it. Not sure if the VBO issues are fixed in driver versions newer than what Ubuntu packages.

---

### Post by ubudog on 2009-09-25
Yep, this is one awesome game.  Thanks for the download link!

---

### Post by neferty on 2009-09-26
Hmm.. would love to try it, but it seems not being able to install under karmic. Guess I have to wait...

---

### Post by ubudog on 2009-09-26
> **neferty said:**
> Hmm.. would love to try it, but it seems not being able to install under karmic. Guess I have to wait...

If you used playdeb then you have to install the playdeb package.  Here it is: [http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb)    

Now, after you have that package installed, it should work.  It takes a while for it to start the download though, so be patient.  Good luck!  :P

---

### Post by NewlyHuman on 2009-09-28
I discovered the Lua API last night, and the console. Cheated myself some cash, but I still have trouble killing the biggest Empire cruisers even with a bunch of railgun turrets.

I think I've run out of scripted missions, but that's just as well; I'm quite content just blowing things up.

---

### Post by Deiz on 2009-10-02
> **NewlyHuman said:**
> I discovered the Lua API last night, and the console. Cheated myself some cash, but I still have trouble killing the biggest Empire cruisers even with a bunch of railgun turrets.

I think I've run out of scripted missions, but that's just as well; I'm quite content just blowing things up.

In general, AI ships are well-rounded, so facing off against a ship similar in size to your own either requires shield upgrades or bigger guns than they have.

Against cruisers, I tend to use beam weapons.

---

### Post by ubudog on 2009-10-02
How do I fire missles?  I have bought missles, the launchers, added the launcher to high slot, but when I press space to fire, the missles don't fire.  How do I do this?   Thanks.  :P

---

### Post by Deiz on 2009-10-02
> **ubudog said:**
> How do I fire missles?  I have bought missles, the launchers, added the launcher to high slot, but when I press space to fire, the missles don't fire.  How do I do this?   Thanks.  :P

Some weapons are secondary (Generally if it uses ammo, it's secondary.) and can be cycled through with W and fired with shift.

---

### Post by ubudog on 2009-10-03
> **Deiz said:**
> Some weapons are secondary (Generally if it uses ammo, it's secondary.) and can be cycled through with W and fired with shift.

Ok.  Will try.  Thanks!

---

### Post by Artemis3 on 2009-10-04
This game is looking good, has a solid base to expand on. It is a shame Vega Strike is so buggy, because i like that very much as well.

What naev needs now is content; hundreds, if not thousands of systems, and lots of scripted missions.

You know, its very fun not to complete Operation Black Trinity, you get a Pacifier and 2 Lancelots as your personal escort everywhere :)

Now to make those landlubbers at New Haven lemme land...

---

### Post by ubudog on 2009-10-04
Yeah the key "W" worked.  Thanks for your help. :)

---

### Post by ubudog on 2009-12-30
So, do the scripted missions end after you fail "Operation Black Trinity"?

---

### Post by solitaire on 2010-01-01
> **NewlyHuman said:**
> I discovered the Lua API last night, and the console. Cheated myself some cash, but I still have trouble killing the biggest Empire cruisers even with a bunch of railgun turrets.

I think I've run out of scripted missions, but that's just as well; I'm quite content just blowing things up.

How do you use the console (Lua API) I'm stuck at planet and can't escape (bad choice of ship for a mission!) I need a helping hand lol!!!

---

### Post by Deiz on 2010-01-01
> **ubudog said:**
> So, do the scripted missions end after you fail "Operation Black Trinity"?

For the most part, yeah. There are a few missions outside of that campaign, but it's the only multi-mission campaign at present.

> **solitaire said:**
> How do you use the console (Lua API) I'm stuck at planet and can't escape (bad choice of ship for a mission!) I need a helping hand lol!!!

F2 opens the console, documentation [here]("http://bobbens.dyndns.org/naev-lua/index.html"). If you're just wanting to escape, open the console and enter player.pilot():setInvincible(true), which will make your ship invulnerable.

The next time you load, the effect will wear off. You can also run the above with false to disable it without reloading.

---

### Post by solitaire on 2010-01-01
Ohh.. thanks

Will have to read up on that ^__^

---

### Post by ubudog on 2010-01-01
> **Deiz said:**
> For the most part, yeah. There are a few missions outside of that campaign, but it's the only multi-mission campaign at present.  

So what happens if you beat it?

---

