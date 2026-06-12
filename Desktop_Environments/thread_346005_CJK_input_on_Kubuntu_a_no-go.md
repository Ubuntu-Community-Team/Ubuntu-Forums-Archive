---
title: "CJK input on Kubuntu a no-go"
date: 2007-01-25
forum: Desktop Environments
---

### Post by dauvm on 2007-01-25
Hey, I was wondering if anyone is using CJK (chinese japanese korean) input on a current 6.10 kubuntu desktop...

I have until recently used gnome and setting up Japanese input was super easy (using uim and anthy), however recently I've been trying out KDE. I need to use scim (skim) to input Japanese... it's absolutely necessary for me.

I have followed these outdated guides:
[https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu)
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

The former says I should type:
```
im-switch -z en_US.UTF-8 -s scim 
``` (my locale)

The latter says:
```
im-switch -z en_US -s scim
```
... a slight discrepancy. But either way, after following all the other steps in the guides, this step causes program crashes and in the latter case stops KDE from loading altogether.  

First of all, a language setting shouldn't stop the DE from loading... that's ridiculous. But what's even more ridiculous is that KDE users are left with, as far as I can see, no way to input CJK languages. All references and guides are outdated (even though 6.10 is 3 months old), and Scim appears to be dead in the water: (all links dead)

[http://www.scim-im.org/](http://www.scim-im.org/)
[http://scim.freedesktop.org/Software/ScimQtImm](http://scim.freedesktop.org/Software/ScimQtImm)
[http://scim.sourceforge.net/](http://scim.sourceforge.net/)

Please help ;) This is a basic, basic requirement for me.
-Doug

P.S. what's the deal with bounties? I remember reading about that a while ago... I would so be willing to set up a bounty for someone who could give the community a usable IM. :)

---

### Post by ryukent on 2007-01-29
OK, I just set up Kubuntu for CJK this afternoon. This is what you need to do:

Follow my link:
[http://ubuntuforums.org/showthread.php?t=338991](http://ubuntuforums.org/showthread.php?t=338991)

BUT,

You will need to replace the sudo gedit stuff with "kdesu kwrite". Also nautilus will obviously change to "kdesu konqueror /" etc etc. I'll re write it for Kubuntu soon. Any problems, just ask. Have spent hours on this one finding the best and most stable way. There are a number of them, but I'd recommend following the guide as it turned out to be the most stable.

---

### Post by ushaba on 2007-03-06
has anyone figured out how to get chinese display working 100% in Kubuntu with an english language environment. i always think i've succeeded, and then looking at the KDE china page or [www.qq.com](www.qq.com) shows me that there is still some setting that is off. the black boxes return, and i weep. most characters display fine, except those in titles and whatnot. i've attached a picture of [www.qq.com](www.qq.com) so you can see just what is wrong exactly. i'd say fonts work about 90% of the time in konqueror, but that 10% is rather annoying. i know i could "just use firefox", but i prefer konqueror for its speed, configurability (except in the area of fonts), etc. i am more interested in knowing where this problem is coming from than anything else. is it a fonts problem, a qt problem (i've played around with qt config and /etc/fonts/local.conf), or a problem with the encodings on those websites? i find it odd that firefox works fine, but makes the fonts kind of faded and ugly. what is this problem most likely to be resulting from, and a) is there a solution in edgy? b)will there ever be a solution to this problem in feisty?

---

