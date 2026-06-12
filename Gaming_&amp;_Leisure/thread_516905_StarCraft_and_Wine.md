---
title: "StarCraft and Wine"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by Criminosis on 2007-08-03
With StarCraft II coming around the corner (a rather far corner though I suppose :roll:), I figured I would pull out my StarCraft and Brood War discs and brush up on  my game. Installation/Gameplay/etc are all flawless, I didn't have an issue. However I'm having a little bit of a bizarre video messup. 

There are no apparent error messages, but when I launch SC it loads, and goes to full screen. But it seems like it doesn't have *enough* room. It full screens (with the GNOME bar above it, however) but the lower portion of the screen just disappears off the screen. 

I dropped the bar to the bottom the screen, still no avail. I found a launcher script to start the game in it's own x session; no avail there either. I heard SC runs at 800x600, and I have that as a setting in my xorg.conf. 

Help would be great, I've heard so much of the quick help from the Ubuntu community. :grin:

---

### Post by cogadh on 2007-08-03
In winecfg, turn off the "Allow window manager to control..." option, it should allow the game to go fullscreen correctly.

EDIT - Hey, this sounds an awful lot like the problem a different user was having with Diablo [here]("http://ubuntuforums.org/showthread.php?t=506875"). You aren't using a widescreen monitor by any chance?

---

### Post by Criminosis on 2007-08-03
> **cogadh said:**
> In winecfg, turn off the "Allow window manager to control..." option, it should allow the game to go fullscreen correctly.

EDIT - Hey, this sounds an awful lot like the problem a different user was having with Diablo [here]("http://ubuntuforums.org/showthread.php?t=506875"). You aren't using a widescreen monitor by any chance?

Actually I am. Presario V6000 at 1200x800

 Your suggestion didn't change it, and it caused my Compiz Transparency to phase through :lol:. No worries though, progess has to start somewhere. I'll check out that thread

(as a side note - dang that was fast :lolflag:

---

### Post by cogadh on 2007-08-03
Actually, we never solved that guy's problem, but it can't hurt to try it anyway, maybe what we tried there will work for you.

---

### Post by Criminosis on 2007-08-03
Gah, beat me to the repost :p. It really does seem like it would be easy to modify. I'll head back out to google..ing I suppose. Thanks for the attention :guitar:.

---

### Post by splintercellguy on 2007-08-03
The Wine AppDb is always a good place to get information about applications: [http://appdb.winehq.org/appview.php?iAppId=72](http://appdb.winehq.org/appview.php?iAppId=72)

---

### Post by Criminosis on 2007-08-03
> **splintercellguy said:**
> The Wine AppDb is always a good place to get information about applications: [http://appdb.winehq.org/appview.php?iAppId=72](http://appdb.winehq.org/appview.php?iAppId=72)

You speak the truth, but I've already trolled those comments many times, the last one comes close to my issue, but isn't quite it.

---

### Post by splintercellguy on 2007-08-03
What version of Wine are you using? I forgot to ask.

---

### Post by Criminosis on 2007-08-03
> **splintercellguy said:**
> What version of Wine are you using? I forgot to ask.

```

allan@allan-laptop:~$ wine --version
wine-0.9.33
```

---

### Post by cogadh on 2007-08-03
Try updating to the latest, 0.9.42

---

### Post by splintercellguy on 2007-08-03
The instructions for obtaining latest are at the Get Wine Now link on [http://winehq.org/](http://winehq.org/).

---

### Post by arsenic23 on 2007-08-03
I have similar issues when running Starcraft while beryl/compiz is running.  Quickly switched to Metacity and it worked for me.

---

