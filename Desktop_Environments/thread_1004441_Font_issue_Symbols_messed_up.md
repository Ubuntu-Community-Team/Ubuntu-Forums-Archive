---
title: "Font issue: Symbols messed up"
date: 2008-12-07
forum: Desktop Environments
---

### Post by .zolder on 2008-12-07
Some of the symbols shown on my system are messed up. I'm using Ubuntu on which i installed XFCE. I'm using the same font as I was when in Gnome. In Gnome, everything was fine.

In XFCE, the problem comes and goes without any noticable pattern/cause. Sometimes, I only have the problem in Firefox, sometimes it's only in the XFCE environment (tasklist), and sometimes everything is fine. The way the issue affects my desktop can change any minute without me doing anything.

Changing to a different font "fixes" the issue, but I want to use the font i like best (Aquabase btw).

Click the link to see a screenshot of what I see when both Firefox and XFCE have the issue: [http://www.plaatjesupload.nl/bekijk/2008/12/07/1228654256-580.png](http://www.plaatjesupload.nl/bekijk/2008/12/07/1228654256-580.png)

Does anyone have any idea on how to address this issue?

(I wanted to submit a bug on launchpad, but I don't know which package/project to select)

---

### Post by kerry_s on 2008-12-07
it looks to me the font your using is not 100% utf8/unicode compatible. i'm not really sure what it's called, lets just say it's not fully compatible. ;)
the stock dejavu fonts in linux are.

---

### Post by .zolder on 2008-12-07
Thank you for replying. However, if the font isn't utf8/unicode compatible, I don't think it would ever be able to function properly. I just came home, sat behind the pc (didn't reboot) and all of a sudden everything looks okay. I'm fairly sure that it will fail on me again, since it has been acting like this all week (just installed xfce this week)

[http://www.plaatjesupload.nl/bekijk/2008/12/07/1228677842-410.png](http://www.plaatjesupload.nl/bekijk/2008/12/07/1228677842-410.png)

Btw, it's an official Mac font. Because of that alone, I don't think the font is the problem.

---

### Post by kerry_s on 2008-12-07
> Btw, it's an official Mac font. Because of that alone, I don't think the font is the problem.

mac uses a different font system (dfont) can only be read on osx, they have to be converted to ttf to work properly.

---

### Post by .zolder on 2008-12-09
Okay, assuming you're right, I edited Aquabase.ttf with Fontforge and replaced the three exotic symbols with copies of the symbols I wanted to see (nothing else!), It's not like I need any of those strange symbols.. Ubuntu did not like that and showed a mix of empty squares (you probably know what I mean), squares with some sort of asian sybols in them and a bunch of nothing all over the place. After an hour or so of fiddling, I gave up and put the old ttf file back in place.

Still not getting why the problem isn't persistant..

---

