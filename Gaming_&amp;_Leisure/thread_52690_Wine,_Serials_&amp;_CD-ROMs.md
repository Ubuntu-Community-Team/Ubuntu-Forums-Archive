---
title: "Wine, Serials &amp; CD-ROMs ??"
date: 2005-07-28
forum: Gaming &amp; Leisure
---

### Post by grofaz on 2005-07-28
I'm trying to get several games, for which I own the CDs or have legitimate serial numbers for, running on my ubuntu hd using wine, but I'm having trouble with copy protection schemes.

My pet peeve is having to insert a CD into a drive to run software installed on my hd. This really ticks me off, so I always use a NoCD fix if I can. My technique works beautifully in Windows but wine coughs it up. I get the "Please insert CD in Drive C" ; Drive C is the fake_windows hard drive!! It's not even a CD-ROM drive!?!

So, my question is how do I fix this no CD problem, preferably without having to insert any stinking CD in a drive. I tried that but like I said, it wants drive C which is the fake windows hard drive.

Another game requires a serial number during installation which I entered when prompted. The installer did it's thing. But now when I run the game with wine a message box pops up stating my serial number is invalid. My serial number is NOT invalid, it is my official legitimate bought and paid for serial number! So something needs tweeking there as well. An invalid serial will abort the installation procedure anyway.

Please can anyone help me out here?? I'd really love to get these games running in ubuntu.

Thanks!

---

### Post by Omnios on 2005-07-28
I think the version of wine in synaptic has a few issues. I had my fake windows and a vfat drive, problem was showing the vfat drive as a cd rom.Hopefully this should be fixed with the new backport we are getting soon. Also Wine is an alfa release so there will be problems.

---

### Post by Mishura on 2005-07-29
Wine doesn't support most copy-protection schemes.  The only one that I can think of that does work, is very simplistic CD-checking.

Cedega, the *other* white wine,  has some support for various copy-protection schemes, and very rarely do I have to circumvent it via cracks.  I know this isn't an option for most people, due to the fact thats its not freeware.  I highly doubt that the CVS version supports these things.

Now onto the wine problem:

I've had a similar problem with the game "Jedi Knight:  Jedi Academy".  This game runs flawlessly under wine and cedega, but does have this "NO CD in Drive" thing, even if you mount your CD.  The fix was to get the actual CD title name ( In this case, "jediacad_1" ) and make a seperate wine drive for it.. similar to this:

```
[Drive Z]
"Path" = "/media/cdrom0"
"Type" = "cdrom"
"Label" = "jediacad_1"
"Filesystem" = "win95"
```

Only this, will Wine recognize the CD.

Now for No-CD patches:

These things usually work fine for me.  If the game is still asking for a CD, then the patch/crack has a problem.   Try using different cracks (most games have several for each version, with a different "cracker" name for each).   If no cracks at all work, then the only thing I can recommend is getting a copy of Cedega and trying that, or a different version of Wine; and try that.

Hope this is useful.

---

### Post by grofaz on 2005-07-29
Thanks for the info, I'm trying cedega now but still not getting much joy out of it. I must be doing something wrong with mapping CD-ROM drives. I've been using default settings without any success. I can't even install a game from a CD, nothing happens.
Very frustrating but then I'm a linux babe in the woods too. I'll keep fooling with it.

Still have the NoCD thing in cedega and wine both. It wants the CD in drive "C" which is the Windows HD. But I'll try labelling a drive as suggested and see if that works.

---

### Post by Mishura on 2005-07-31
May I ask what game this is?  It seems that each game has its own "quirk", and they all act differently when it comes to wine and stuff.  Especially when cracking/bypassing/or complying with CD-checks are conserned.

---

