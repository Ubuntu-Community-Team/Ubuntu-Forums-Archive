---
title: "Secret Maryo Chronicles is in the Gutsy Repo's! (+important install note)"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by Ubuntiac on 2007-10-29
WOO HOO!

After all this time, my favourite linux game [Secret Maryo Chronicles ]("http://www.secretmaryo.org")(a very cool, high res, GPL3, alternate version of Mario Brothers) is in the repo's!

[IMG]http://i234.photobucket.com/albums/ee164/gorrgot/1.png[/IMG]

No more figuring out missing libraries from the only app that ever convinced me to compile anything. Joy! There's only one problem:
[CENTER]
:shock:**Ubuntu's repositories have an error that installs the wrong dependency!** :shock:[/CENTER]

When you install the game (called "SMC" in repos) _make sure that you *also* select libcegui-mk2-1**-dev**_ (synaptic / adept have the non -dev version incorrectly as the dependency)

The versions also kind of old, but still about the most single player fun I've had on my (K)ubuntu machines.

Go crazy kids! :lolflag:

**PS** If anyone knows who we'd talk to to get the dependency changed, *please* post here. The package lists Ubuntu MOTU developers as the maintainer, but the MOTU games group has been disbanded?!

---

### Post by disturbedite on 2007-10-29
[newer version]("http://www.getdeb.net/app.php?name=Secret%20Maryo%20Chronicles") (1.0) has been available for a while on getdeb.

---

### Post by Ubuntiac on 2007-10-29
Ewww! And there's no menu item for it! Still... It's a (great) start!

Run it just by going to the terminal / konsole and typing SMC (enter)

---

### Post by Ubuntiac on 2007-10-29
disturbedite@ True! That version worked great on my Feisty machine. Wouldn't install at all on my Gutsy (testing) system. I was thinking I'd have to wait for getdeb to update, which is why I was so happy to see it already in the repos. :D

---

### Post by Crafty Kisses on 2007-10-29
> **Ubuntiac said:**
> WOO HOO!

After all this time, my favourite linux game [Secret Maryo Chronicles ]("http://www.secretmaryo.org")(a very cool, high res, GPL3, alternate version of Mario Brothers) is in the repo's!

[IMG]http://i234.photobucket.com/albums/ee164/gorrgot/1.png[/IMG]

No more figuring out missing libraries from the only app that ever convinced me to compile anything. Joy! There's only one problem:
[CENTER]
:shock:**Ubuntu's repositories have an error that installs the wrong dependency!** :shock:[/CENTER]

When you install the game (called "SMC" in repos) _make sure that you *also* select libcegui-mk2-1**-dev**_ (synaptic / adept have the non -dev version incorrectly as the dependency)

The versions also kind of old, but still about the most single player fun I've had on my (K)ubuntu machines.

Go crazy kids! :lolflag:

**PS** If anyone knows who we'd talk to to get the dependency changed, *please* post here. The package lists Ubuntu MOTU developers as the maintainer, but the MOTU games group has been disbanded?!
Cool!

---

### Post by cogadh on 2007-10-29
> **Ubuntiac said:**
> Ewww! And there's no menu item for it! Still... It's a (great) start!

Run it just by going to the terminal / konsole and typing SMC (enter)
You can create your own menu entry, you know.

---

### Post by Crafty Kisses on 2007-10-29
> **cogadh said:**
> You can create your own menu entry, you know.

That's super cool dude. :KS

---

### Post by Ubuntiac on 2007-10-30
> **cogadh said:**
> You can create your own menu entry, you know.

I know I can... (in fact have) but a lot newbies wouldn't know how to find the program and stick it in a menu item. I remember being stunned when I first used ubuntu and installed a .deb only to have no idea where it went.

Ahhh... those were the days! None of this fancy pants shiny 3d desktop stuff... CLI? Wimps! We started *our* apps in *binary code!* ;)

---

### Post by cogadh on 2007-10-30
Ha! That's nothing, back when I first started using Linux, I had Slackware installed from 27 floppy disks. Package repositories? Nothing doing, we had to compile all our apps from scratch... ah, memories.

Man, am I glad those days are gone! :smile:

---

### Post by Crafty Kisses on 2007-10-30
> **cogadh said:**
> Ha! That's nothing, back when I first started using Linux, I had Slackware installed from 27 floppy disks. Package repositories? Nothing doing, we had to compile all our apps from scratch... ah, memories.

Man, am I glad those days are gone! :smile:

That's the definition of l337, haha. :KS

---

### Post by BigSilly on 2007-10-30
I spotted this in the repository too, but sadly it's an old version.  :(  Top, top fun, but worth waiting for GetDeb to update with a new version for us Gutsy users. I have the new one on my Mandriva install (*they* have the new one on *their* repos!) and it's even better now.

---

### Post by El Zoido on 2007-10-30
I cant find libcegui-mk2-1-dev in the repository...

---

### Post by por100pre1 on 2007-10-30
> **El Zoido said:**
> I cant find libcegui-mk2-1-dev in the repository...

It should be libcegui-mk2-dev:

```
sudo apt-get install libcegui-mk2-dev
```
[B]
BTW, great tip Ubuntiac![/B]

---

### Post by El Zoido on 2007-10-31
It worked, thanks!

---

### Post by Ubuntiac on 2007-11-09
> **por100pre1 said:**
> [B]
BTW, great tip Ubuntiac![/B]

Thanks! By the way I just noticed:
**GetDeb.net has updated its SMC package to the _latest version_ (1.2)!**

They have 32 and 64 bit versions. You can download them from the link below:
[Click here for SMC v1.2 .debs at GetDeb.net]("http://www.getdeb.net/app.php?name=Secret+Maryo+Chronicles") :popcorn:

Not sure if it includes the game music pack from [secretmaryo.org]("http://secretmaryo.org") or not...

---

### Post by BigSilly on 2007-11-09
Installed this just great from GetDeb, and yes you do need to manually install the music pack zip file. Just extract it somewhere, then copy it into SMC's music directory, and Bob's your uncle.

---

### Post by Ubuntiac on 2007-11-11
Just for the record (I think) the path to copy the music to is:

```
/ust/local/share/smc
```

I think it *may* vary depending on if you compiled or used getdeb. Can anyone confirm how they installed and where the music went?

---

### Post by BigSilly on 2007-11-11
Yes. Drop the whole extracted music data package into:

```
usr/share/games/smc/music
```

That's what I did anyway. Hope this helps.

---

### Post by sub2007 on 2007-11-11
You can also get an up to date version, with music by adding this repository to Synaptic:

[https://edge.launchpad.net/~berteh/+archive](https://edge.launchpad.net/~berteh/+archive) ;)

---

### Post by Ubuntiac on 2007-11-13
Hey, SMC just made GetDeb's top 10! Mind you, I suspect at least part of that could be because the repo's don't install fully working (yet)!

Still, very cool. Roll on v1.3!

---

### Post by Virgilius on 2008-03-03
No wonder the window for SMC opens and rthen closes after I type smc in the Terminal :lolflag:

---

### Post by elasto1mania on 2008-03-09
Hello,
I installed the lastest smc 1.4.1 but i cannot start it.
Help please.

---

### Post by PLiNkO on 2008-03-09
Installing with these instructions worked for me.

[http://gaming.gwos.org/doku.php/guides:32bit:secretmaryochronicles]("http://gaming.gwos.org/doku.php/guides:32bit:secretmaryochronicles")

---

### Post by PC_load_letter on 2008-04-03
> **PLiNkO said:**
> Installing with these instructions worked for me.

[http://gaming.gwos.org/doku.php/guides:32bit:secretmaryochronicles]("http://gaming.gwos.org/doku.php/guides:32bit:secretmaryochronicles")

+1, and I followed the amd64 instruction. With Feisty, I got an error like "libGL cannot be found", but that was nothing a symbolic link couldn't fix ;)
Great game by the way and runs flawlessly even under Fiesty. Oh, one more thing, the first time I ran it, it took a while loading maps, closed it then it refused to display anything but a black screen after that.**_ FIX:_** turned off the GL Desktop. Now it runs flawlessly! 8)

---

### Post by Perfect Storm on 2008-04-03
follow the 64-bit guide instead, works well for 32-bit also. I don't update the 32-bit anymore, because I've moved to 64-bit. Mainly with Open Source + compiling there's no diffrences

---

### Post by forrestcupp on 2008-04-03
Well, the good news is that Hardy has SMC 1.4-1 in the repos and the dependency bug has been fixed, so you just have to install it and it works.  It's too bad they still don't have it worked out so the package will create a menu entry, though.  You still have to type **smc** in the terminal, or make your own entry.

The new version is way better than what I played a while back in Gutsy (or maybe it was Feisty).

---

