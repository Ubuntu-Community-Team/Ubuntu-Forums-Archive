---
title: "Compiz: Excessive Font Size"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by iamadam on 2007-07-22
Hi. Just got Compiz Fusion up and running on Feisty. It's all working fine except my font size is too large on all the menus. I've tried adjusting it in System -> Preferences -> Fonts but to no avail. Anyone know why this might be? I'm running Ubuntu on an NX6125 laptop with ATI Radeon XPress 200M integrated graphics. It's taken me ages to get everything working on this bloody machine and this is the final thing that needs sorting :)

---

### Post by gavintlgold on 2007-07-22
Since the menu fonts aren't controlled by Compiz, this can't be a Compiz problem. That is, unless you are talking about the TITLE bar. That is controlled by emerald, and you can fix that in the Emerald Themer.

---

### Post by iamadam on 2007-07-22
Cheers for the reply. I can't find any setting for changing font size in "Emerald Theme Manager" other than the title bar, but that's not where the problem is. It's only menu items that are giving me grief. I still have the problem if I disable Emerald and just use Metacity!

---

### Post by Deco_21 on 2007-07-23
Try installing beryl, just as a Fallback Windows Manager

Only  beryl part.
[HTML]http://ubuntuforums.org/showthread.php?t=488385[/HTML]

Check the emerald manager.

---

### Post by JEdwardP on 2007-10-21
Hello all,

I just ran into something of an opposite problem to that of the original poster. I set up compiz and emerald with no problems on Thursday as soon as I downloaded the Gutsy release, and had no display issues that I could discern until tonight.

I had set my title bar font size to 10pt in emerald. Tonight I rebooted, and found that the size had decreased to what looked to be about 6pt, even though a check of emerald did not show any change in the setting.

I had to increase the  emerald setting for the title bar to 16pt in order to make it appear as large as it originally did when set to 10pt. No other anomalies were evident; only window title bar font size was affected.

Do any of you have an idea of what may have caused this?

---

### Post by berlinbullet on 2007-10-29
Bump. I just did the install with gutsy as well and noticed it defaulting back to the small text size as well. I'm not finding too much on why its reverting to this, but I'm investigating :confused:

---

### Post by lijil on 2007-11-28
Running 'emerald --replace' via ALT+F2 fixes this for me. I don't know what is causing it in the first place, but this makes me think that emerald is not starting up correctly (or maybe in the wrong order)

---

### Post by lijil on 2007-11-28
This may be the issue:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141001)

---

### Post by berlinbullet on 2007-11-29
That may be it. For the time being, I just have a script in my sessions to take care of it at start up.. makes everything a lot easier..

```

#!/bin/bash
sleep 30
emerald --replace

```

Gives it some time to get everything started up with the sleep command in there.

---

### Post by JEdwardP on 2007-11-29
emarald --replace also corrects this for me. Thanks for your help!

---

