---
title: "[SOLVED] Emerald only works partially with compiz fusion"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by stillwaters130 on 2007-07-05
Hello,

I recently installed compiz fusion, which went flawlessly.  All of the effects work, except for the window decoration.  I previously used beryl with emerald - no problems there.  However, when I start up emerald, it does not skin the borders except for a little sliver at the top left corner.  The rest of the borders are invisible, however you can still grab them with the mouse.

I've searched all over and haven't found a thread that's helped me yet.  I've reinstalled everything, changed xorg.conf, installed and uninstalled beryl again, but nothing has made any changes.

Hopefully somebody can help me fix this, or at least point me to a thread that maybe I missed, which might help me out.

Thanks,
Jessica :-)

---

### Post by trinaryouroboros on 2007-07-06
> **stillwaters130 said:**
> Hello,

I recently installed compiz fusion, which went flawlessly.  All of the effects work, except for the window decoration.  I previously used beryl with emerald - no problems there.  However, when I start up emerald, it does not skin the borders except for a little sliver at the top left corner.  The rest of the borders are invisible, however you can still grab them with the mouse.

I've searched all over and haven't found a thread that's helped me yet.  I've reinstalled everything, changed xorg.conf, installed and uninstalled beryl again, but nothing has made any changes.

Hopefully somebody can help me fix this, or at least point me to a thread that maybe I missed, which might help me out.

Thanks,
Jessica :-)

Just a hot question, since you had Beryl installed before, I'm suspecting you had Beryl in the "Startup" section in System -> Preferences -> Sessions?

If it's still there, delete that and Beryl Manager, and replace them with two entries:

Name: Compiz Fusion
Command: compiz --replace

Name: Emerald
Command: emerald --replace

Then do a reboot, and see if that fixes things. I had many problems because of Beryl still being stuck in the startup, all were resolved after getting rid of it from there.

If this is redundant, and you did that stuff already, my apologies.

Otherwise, it might be a prudent idea to get into a terminal and do:
```
killall emerald && emerald --replace
```

See what pops up, perhaps some conflict somewhere in there you can repost here.

---

### Post by stillwaters130 on 2007-07-06
I get a bunch of these errors:

(emerald:10068): Wnck-WARNING **: Unhandled action type (nil)

Beryl is definitely not running, and is definitely not in my startup list.

That little sliver in the top left corner is no longer there, however the borders still are... but they're still invisible.  I can still grab on to them, and all the effects are working... just no decoration.

---

### Post by stillwaters130 on 2007-07-06
Interesting thing -- when I boot into my session, compiz and emerald are running, but don't seem to be functioning right.  I have to restart them before they'll do their jobs.

Compiz is also working fine with metacity, I don't think I mentioned that before; It's just emerald that's giving me a hard time.

I tried running compiz --replace from the terminal, and I got this error:

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

I'm guessing that's the problem, them, but I don't know how to fix that.  Do I have to do a force version in synaptic?  Not sure what the best course of action here would be.

---

### Post by stillwaters130 on 2007-07-06
Got it!  I don't know why, but the package libberyldecoration0 was the cause.  It was holding back emerald from updating it's version (?), but it caused the following to be done:

Remove the following packages:
beryl-plugins
beryl-settings

Upgrade the following packages:
aquamarine [0.2.0~0beryl1 (feisty, now) -> 0.2.1.dfsg+git20070318-0ubuntu2
(feisty)]
emerald [0.2.0~0beryl1 (feisty, now) -> 0.3.0+git20070621~3v1ubuntu0 (feisty)]
libemeraldengine-dev [0.2.0~0beryl1 (feisty, now) ->
0.3.0+git20070621~3v1ubuntu0 (feisty)]
libemeraldengine0 [0.2.0~0beryl1 (feisty, now) -> 0.3.0+git20070621~3v1ubuntu0
(feisty)]

Go figure.

Anyways, thanks for your help! :)

---

### Post by trinaryouroboros on 2007-07-06
> **stillwaters130 said:**
> Got it!  I don't know why, but the package libberyldecoration0 was the cause.  It was holding back emerald from updating it's version (?), but it caused the following to be done:

Remove the following packages:
beryl-plugins
beryl-settings

Upgrade the following packages:
aquamarine [0.2.0~0beryl1 (feisty, now) -> 0.2.1.dfsg+git20070318-0ubuntu2
(feisty)]
emerald [0.2.0~0beryl1 (feisty, now) -> 0.3.0+git20070621~3v1ubuntu0 (feisty)]
libemeraldengine-dev [0.2.0~0beryl1 (feisty, now) ->
0.3.0+git20070621~3v1ubuntu0 (feisty)]
libemeraldengine0 [0.2.0~0beryl1 (feisty, now) -> 0.3.0+git20070621~3v1ubuntu0
(feisty)]

Go figure.

Anyways, thanks for your help! :)

Well, I'm glad you resolved the problem!

I would've responded sooner, but, I got stuck in traffic en route to home.

At least someone will be able to see this post, if they experience a similar issue with it.

:KS

---

