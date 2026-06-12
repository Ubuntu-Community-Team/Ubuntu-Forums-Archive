---
title: "Wine running slow"
date: 2007-02-14
forum: Gaming &amp; Leisure
---

### Post by rossjman1 on 2007-02-14
I have a few games that I want to run in Wine, but am having serious troubles. I have a fast computer, but for the applications that load, they run too slow to play.
Intel Core Duo 1.83GH (I am running the generic kernel to utilize both cores)
1 Gb Ram
512MB ATI Mobility Radeon x1400 (fglrx drivers)

Here are the games that I tested so far and their rating on WineHQ and how it runs on my computer. For all of these the sound doesn't work, but that's not a big deal right now.
**Age of Empires: The Rise of Rome**
*According to WineHQ:* Gold
*How it actually runs:* Doesn't, logs me out of gnome to GDM
**Cameleon (small freeware puzzle game like 7colors)**
*According to WineHQ:* N/A
*How it actually runs:* Runs perfectly, but for a game that's less than 1 MB I would expect that.
**Crimsonland (freeware top-down shooter)**
*According to WineHQ:* Bronze
*How it actually runs:* Textures don't load making the game unplayable.
**Highway Pursuit (freeware clone of a game)**
*According to WineHQ:* N.A
*How it actually runs:* Bass.dll failed to load, game crashes on startup
**Icy Tower (another freeware arcade game)**
*According to WineHQ:* Garbage
*How it actually runs:* Runs way too slow (exactly what is said on WineHQ)
**SuperMarioPac (an original freeware game)**
*According to WineHQ:* N/A
*How it actually runs:* Runs way too slow
**Command & Conquer: Tiberian Sun**
*According to WineHQ:* Bronze
*How it actually runs:* Runs way too slow

As you can see if wine actually runs a game (Tiberean Sun, for example) the game runs way to slow to be playable. Disabling Beryl doesn't make things run faster at all. Any help would be appreciated.

---

### Post by Drezliok on 2007-02-15
Are you using the latest version of wine? [If you going to the AppDB alot I think you would be but you didn't say]

If you are, try purging it and installing fresh, winecfg and try again.
Try to compile wine yourself [I've never had to so I don't know all that it involves, I've compiles some small stuff but wine is huge.]
If that doesn't work maybe it's something else than wine.


I hope this helps


PS
Do you turn off Beryl before trying to play games?

---

### Post by rossjman1 on 2007-02-15
If by turning of Beryl you mean selecting Metacity as a window manager in the notification area, then yes. I got Wine through the repositories.

---

### Post by hikaricore on 2007-02-15
Usually the version of wine in the repos is ancient, but I think it's been updated in the edgy backports as of recent.

You can always get the most up to date version of wine here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Or to find the version of wine you are using from a terminal type:

```
wine --version
```

Aside from that have you tried running any native games (3d or otherwise) to see if maybe it's an issue with your video settings / drivers?  Just a thought.

Good luck,

--Aaron

---

### Post by Mongoose on 2007-02-15
I would guess your ATi card is going to hold you back regardless of anything else.  You need to make sure your GL support is working properly as well.  Try looking around for ATi setup howtos, and you may need to switch to the Open Source drivers.  

You may need to alter your Wine settings to take into account how well your ATi card supports certain features like pixel shaders, etc.  I don't even claim to keep up with ATi support levels for features.  Last time I tried an OpenGL driver on ATi I was very disappointed in just feature support -- not to mention stability and performace.  You have to work with what you got I guess.  =)

---

### Post by Toxicity999 on 2007-02-15
"Mobility" so you must be on a laptop, and probably no drop-in nvidia for you... that sucks... ATis drivers truly do suck though. Not necessarily the problem here (might be) buuuuut still. Read up on appdb.winehq.org, and see  what others a say and how they rate it and go from there. Might just be the games.

---

### Post by rossjman1 on 2007-02-16
```
jeff@ubuntu:~$ wine --version
wine-0.9.30
```
same as the latest version on that web site.
> Aside from that have you tried running any native games (3d or otherwise) to see if maybe it's an issue with your video settings / drivers?
I run other native games (Gnome games like solitaire and the like, Bomberclone, 
Frozen-Bubble, Lincity-NG, Ltris, SuperTux, SuperTuxCart, and Widelands. I also have Scorched 3D, but the fonts are screwed up. I can't run OpenGL games (crazy looking fonts - see the thread [here]("http://ubuntuforums.org/showthread.php?t=51486"). The ATI card is working because Beryl runs so smooth. Are the fglrx drivers OSS?

---

### Post by Ptero-4 on 2007-02-16
no. The fglrx are the propietary ones.

---

### Post by rossjman1 on 2007-02-16
If I run the OSS drivers (if they exist for my card) will I still be able to run Beryl? If so, can someone please post a link to the installation instructions of said drivers? Thanks for your help.

---

### Post by rossjman1 on 2007-02-18
bump

---

### Post by Toxicity999 on 2007-02-19
Well yea, any drivers that give you 3D acceleration will let you use berl (at varying speeds and awesome levels) just switch from fglrx to radeon to try it (in the video card section of /et/X11/xorg.conf) if it works glxinfo | grep "direct rendering" should yield a yes. But I think you might have to play with symlinks after using fglrx then going to radeon... I truly don't remember.

---

