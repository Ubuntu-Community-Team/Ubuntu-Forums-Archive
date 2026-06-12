---
title: "Title Bars Gone"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Ebtoulson on 2008-05-03
Well ever since I upgraded to 8.04 my title bars started out being translucent and now they have just disappeared. I did a little searching and some people think it could be the windows manager. Any help would be helpful.

Thank
p.s. - I am using emerald and compiz, even though I didn't see a setting for this.

---

### Post by Kizlum on 2008-05-04
Hello,

I have already got a similar error.
1) Go into your CompizFusion Settings Manager and verify the "Window decorator" option is checked.
2) Try to start compiz by the command-line, the verify there is no errors.

---

### Post by Ebtoulson on 2008-05-04
Yes that fixed it, didn't have window decorations enabled. Thanks

---

### Post by Junior Varsity on 2008-05-04
I'm having the same problem, title bars as in X - or minimize/maximize and the title of my program aren't showing up when i enable effects I'm using GNOME though. What do I do? They work on normal and at one time Extra effects worked perfectly with the title bars. I don't know what went wrong.

BTW: Using Hardy Heron 8.04

---

### Post by Enlitend on 2008-05-04
@ Junior, are you running any window decorator like Emerald? I used to have that problem when I was runnning Gutsy a few weeks back. I did a fresh install of Hardy and I'm currently running Compiz,Emerald and AWN without any problem.

---

### Post by Junior Varsity on 2008-05-04
Um I don't think so, I have a theme Moomex in use right now (from gnome-look.org) but I don't think that affects anything because when I add Extra's it doesn't matter what theme i'm using I still don't have title bars. I did a fresh install of gutsy and then upgraded to hardy earlier today.

---

### Post by c4v3m4n on 2008-05-04
Make sure you have window decorations enabled.  And make sure that you don't have "reflection" plugin in compiz enabled. That caused me to not be able to see my window decorations.

---

### Post by Junior Varsity on 2008-05-04
How can I find out if I have any or how do I disable them? I'm really new as to using Ubuntu as my primary operating system.

---

### Post by rolnics on 2008-05-04
You need the advanced settings for compiz installed.

Open up terminal and type "ccsm" without quotes. this should bring up the settings manager and there you'll an option for windows decorations click it and at the top you'll see if it's enabled or not.

---

### Post by Junior Varsity on 2008-05-04
Okay windows decorations were on and reflection wasn't enabled. Then I turned them off and tried to apply extra effects, it still didn't work the title bars are gone. Then i turned decorations back on and reflections and i tried it and it didn't work. So what should I do now?

[img]http://i31.tinypic.com/302w4md.png[/img]

Screenshot. Visual effects=None. Title bars work and everything is perfect except one thing...no effects.

[IMG]http://i27.tinypic.com/28bzbqo.png[/IMG]

Screenshot. Visual effects=Extra. No title bars, but the effects work. Same thing happens with normal effects.

sorry for the lack of thumbnails.

---

### Post by KaliVoid on 2008-05-04
look here

[http://ubuntuforums.org/showthread.php?t=779828](http://ubuntuforums.org/showthread.php?t=779828)

---

### Post by Junior Varsity on 2008-05-04
crap crap crap. I need help, urgently. This is kinda off topic of the effects thing but i went into my xserver settings and accidently changed kernel debuffer settings and now my screen resolution is 800x600 and it won't go higher as you saw from the screenshots before my actual screen resolution is 1400x900 how do I change it back? (I hate being a n00b

Nevermind. Thanks to all who tried to help. For some reason now everything works perfectly.

---

### Post by Kizlum on 2008-05-04
Junior, on my computer, if I tweak CompizFusion settings with CFSM and modify the Appearence Preferences's VisualEffect tab, it erease my tweaks... Then, try to don't touch this parameter.

---

