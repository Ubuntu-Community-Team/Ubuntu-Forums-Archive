---
title: "Wine resolution change screws up Plasma, Wine, and Firefox"
date: 2014-04-24
forum: Desktop Environments
---

### Post by Zeikcied on 2014-04-24
I posted this over on Kubuntu Forums, but I'm cross-posting it here in hopes that I can get a faster answer.  Even though the problem was caused by Wine, its effects reach beyond Wine itself, so I'm hoping it's fine to put it here.

I was using Crossover 13.0.1 to run the Windows version of Steam, and I started up Star Wars Knights of the Old Republic. It started running at an extremely low resolution, and it messed up Plasma, Windows Steam, and Firefox somehow. When it happened I was still using Kubuntu 13.10, but I upgraded to 14.04 hoping it would fix whatever is wrong. It did not.

What happened was the resolution was so low that my Plasma desktop was larger than the screen itself, so it was sort of zoomed in on the mouse. Moving the mouse toward the edge of the screen moved the screen itself so I could see the other parts. KOTOR wasn't displaying properly, or at all, really, even though it and Wine set my resolution that low. I was eventually able to reset my resolution back to 1280x1024, and I was even able to get KOTOR to display and set its resolution to 1280x1024. All well and good, or so I thought.

I first found out that Windows Steam was completely borked. It suffered horribly in the incident. The full window won't display, none of the dialogs will display, I can't bring up the menu on the taskbar button, nothing works. I can't even quit out of it because of this, so I have to force it to close.

Firefox was affected in that any menu (namely my bookmarks menus) that is longer than the screen has a large chunk of the top missing. As in, it thinks it's scrolled all the way up, but it is not. There is still an arrow at the bottom to scroll down, but the top arrow and everything up to a certain point are above the screen where my mouse can't reach. I can still use my arrow keys to select the missing entries, so they're still there, but they're beyond the screen.

Also, the splash screen after I login goes bonkers. I can't explain it, really. The box with the fading icons goes away and the background sort of cuts itself up and shuffles around. Not in any sort of smooth animation, but in an instant it's all wonky.

So as far as I can tell, Plasma, Windows Steam, and Firefox are all screwed up from this one incident and I have no clue how to fix it all.

[This part was added later]
So I just found out that it affects not only the Windows Steam, but also all Crossover bottles as well as regular Wine. Wine and CO seem to only display windows and portions of windows in a very small portion of the screen at the very top. Any part of the window below that part cannot be clicked, and in most cases can't be viewed.

So far, Firefox seems to be the only native program that it affects. But that could be due to it being the only one I regularly use that has menus as long as my bookmarks menus. I suppose I could try doing a fresh install, but I'm afraid even that won't work. It might be something with my KDE session or some configuration somewhere, but I have no clue how to fix it.

---

### Post by jbaerboc on 2014-04-24
This doesn't help you fix it but I've had the same issue in the past. I've played games where when it dropped me back on my desktop after a crash or normal exit and they I had a funky resolution. 

However I have not had this issue in the regular Ubuntu 14.04 [unity]. Must be something between the different DM's? Anyway goodluck on finding a fix!

---

### Post by Zeikcied on 2014-04-25
I found out how to fix it myself.

I went to nvidia-settings and set my desktop resolution using that, and it seems to have reset everything.  Or at least Firefox.  But everything else should be fixed, based on that.

---

### Post by jbaerboc on 2014-04-27
> **Zeikcied said:**
> I found out how to fix it myself.

I went to nvidia-settings and set my desktop resolution using that, and it seems to have reset everything.  Or at least Firefox.  But everything else should be fixed, based on that.


Awesome to hear, great job!

---

