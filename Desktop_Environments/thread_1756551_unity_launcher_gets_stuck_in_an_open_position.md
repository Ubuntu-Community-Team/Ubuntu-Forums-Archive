---
title: "unity launcher gets stuck in an open position"
date: 2011-05-12
forum: Desktop Environments
---

### Post by Yohai on 2011-05-12
hi


[LIST=1]
[*]I'm running ubuntu 11.04. from time to time, the unity launcher gets stuck in an open position, preventing me from clicking anything on the left side of the screen. this is terribly annoying.
I couldn't find anything on the help or in the forums. ideas?
[*]is there a *simple* way to change the properties of the icons in the launcher? I have there some custom application launchers that were automatically imported to the launcher during upgrade (they were in the top menu).
[/LIST]
thanks,
yohai

---

### Post by wojox on 2011-05-12
You can tweak unity settings with this:

```
sudo apt-get update; sudo apt-get install compizconfig-settings-manager
```

Then Alt+F2

```
about:config
```

Will open the Unity plugin.

---

### Post by Yohai on 2011-05-12
thanks. 
I know this tweak. I set it to auto hide. it doesn't hide. just gets stuck there on the right.
very annoying. might it be a bug?

---

### Post by cronius on 2011-05-26
Hi,

I'm experiencing the same problem. I think it's a bug with the drag-and-drop code.

If I e.g. drag a song in spotify, the launcher pops up, probably so that you can easily drag-and-drop something from one application to another. However, when I drop the song inside spotify, the launcher stays open (seemingly forever, even when I change applications, workspaces etc.). So it's "stuck", like you said.

If I then go to e.g. an open workspace and simply move an icon around, the launcher finally disappears.

Hope this helps! (Definitely a bug.)

---

### Post by dumbo on 2011-05-26
Yep - it's a bug, for me I think dragging items that partially appear underneath the launcher caused it to lock open, no amount of messing around in ccsm et al made any difference.

The "critical" bugs:
- there is no way to force-close the unity launcher that I can find (e.g. clicking the icon at the top, pressing the reveal button or right clicking etc *could* be used force the launcher to close - but nothing works).
- there is no obvious way to restart the launcher process, I couldn't even work out which process renders it.

The only real workaround is to set the panel to 'never' hide, but I'm not sure that's everyone's cup of tea.

---

### Post by jaywink on 2011-05-28
Affected by the same bug. The workaround of moving some icons around in a workspace hides the stuck panel, thanks for that!

Very annoying, digiKam especially seems to cause it almost every time I process photos.

---

### Post by okey666 on 2011-05-31
I too am affected by this bug. It forces me to use Spotify through Wine.

I can confirm that moving an icon on the desktop hides the launcher again.

---

### Post by wildmanne39 on 2011-05-31
> **Yohai said:**
> hi


[LIST=1]
[*]I'm running ubuntu 11.04. from time to time, the unity launcher gets stuck in an open position, preventing me from clicking anything on the left side of the screen. this is terribly annoying.
I couldn't find anything on the help or in the forums. ideas?
[*]is there a *simple* way to change the properties of the icons in the launcher? I have there some custom application launchers that were automatically imported to the launcher during upgrade (they were in the top menu).
[/LIST]
thanks,
yohaiHi, you can not drag an icon to to the launcher in natty, you open the app you want on the launcher and then go to the launcher and right click on it and check keep in launcher.In my signature below this text check out the guides they will tell you how to customize unity to your liking.

---

### Post by chinamike on 2011-05-31
yes, been using Natty Nar for about three days. Before then I have been using Lupu and Puppy 4 (love Puppy 4, so-so with Lupu). So my Unity sidebar is stuck; this is the first thing to go wrong since I've been using/updating things on it. I tried the various things discussed here and it doesn't close. I even deleted two shortcuts that I knew I wouldn't use to see if it would wake it up!

Be glad to hear a solution. Meanwhile I am going to google how to use apt-get to add/fix/install missing dependencies in a new program. Wish me luck! ;)

If anyone finds an immediate solution, you can email me/message me.

Thanks for the support and help

CHINA

---

### Post by wildmanne39 on 2011-05-31
> **chinamike said:**
> yes, been using Natty Nar for about three days. Before then I have been using Lupu and Puppy 4 (love Puppy 4, so-so with Lupu). So my Unity sidebar is stuck; this is the first thing to go wrong since I've been using/updating things on it. I tried the various things discussed here and it doesn't close. I even deleted two shortcuts that I knew I wouldn't use to see if it would wake it up!

Be glad to hear a solution. Meanwhile I am going to google how to use apt-get to add/fix/install missing dependencies in a new program. Wish me luck! ;)

If anyone finds an immediate solution, you can email me/message me.

Thanks for the support and help

CHINA
Hi, there is not a perfect way to do it,but if I keep my window open by the edge and I followed this set of instructions it stays hidden almost all the time it will only open when I hit the super key. ) In the Unity plugin, set Reveal to Auto hide and the Reveal edge to None or Disabled. screenshot 6 shows that the edges are disabled so that it will not open ,you can tell because all around the little window it is in red, if it was set to open when the mouse was moved to the edge it would be in green. Every now and then it still opens if the window is not against the left side of the screen even if I use the window not maximized I keep it against the left edge anyway. I never have a problem with it getting stuck so far. You do have to have ccsm installed to change unity plugin settings.

---

