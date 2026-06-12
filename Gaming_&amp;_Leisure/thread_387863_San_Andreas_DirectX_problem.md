---
title: "San Andreas DirectX problem"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Eindringling on 2007-03-18
Since San Andreas won't run in wine, I tried running it with Cedega, but it couldn't find my sound card. I fixed that by installing the drivers, but now I get a notice that says that I do not have directx installed. I've installed directx with wine and with cedega, but it still gives me the error. I'm at a total loss to what I should do...any ideas?

---

### Post by Lystrodom on 2007-03-18
A better place to ask would be the cedega forums. Most people here don't know much about cedega, and, presumably, you're paying for support.

---

### Post by Eindringling on 2007-03-18
> **Lystrodom said:**
> A better place to ask would be the cedega forums. Most people here don't know much about cedega, and, presumably, you're paying for support.

presumably.

any other suggestions?

---

### Post by hikaricore on 2007-03-18
You can't install directx in linux.  End of story.

Search for your game here:

[http://appdb.winehq.org](http://appdb.winehq.org)

Last I checked it didn't work at all.

For nearly everything that works at all, wine works just as well or better than cedega and it doesn't cost a damn thing.

---

### Post by lakersforce on 2007-03-19
Well, actually cedega works quite well with a lot of games and the ones that uses directX or uncircumventive copy-protection works better with cedega than it does with wine. But its all a matter of tweaking. If you have the technical knowledge you can in almost all cases use wine instead of cedega. Cedega could be considered the "easy solution". Wine the "better".

As to your directX problem, I dont know :(

Last time I installed GTA:SA with wine it ran without complaining. The framerate was real bad though, practically rendered the game unplayable.

---

### Post by Eindringling on 2007-03-19
> **hikaricore said:**
> You can't install directx in linux.  End of story.

Search for your game here:

[http://appdb.winehq.org](http://appdb.winehq.org)

Last I checked it didn't work at all.

For nearly everything that works at all, wine works just as well or better than cedega and it doesn't cost a damn thing.

i've already installed it a number of times "successfully" using different methods...the problem is getting wine and cedega to recognize it.

---

### Post by lakersforce on 2007-03-19
> **hikaricore said:**
> You can't install directx in linux.  End of story.
Since the wine library already contains the simulated directX dll's you cant install directX. The end result would be the same as when you try to install the same or an inferior version of directX on windows: it does not install, only it gives the dialog of doing so. But if you remove those native wine dll's refering to directX (and directX only) you should be able to install it. That should not be neccesary though, as the native ones work just as well. Might be worth a shot though...?

@Eindringling: are you sure you are using the newest version of wine from winehq.com?

---

