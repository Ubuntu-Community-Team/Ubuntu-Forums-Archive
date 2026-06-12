---
title: "[SOLVED] Finally a Compiz update from Trevino... but now I can't move my windows"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-08-19
Hi,

I updated compiz fusion just now from trevino's repositories and found that all my settings were gone.  No big deal... I just opened up compiz config and put them all back in.  Now everything works... I can rotate cube, have expose, all that good stuff.  But I can't move my windows anywhere. For example, if I have pidgin open and it's on the right of the destop, I can't take my mouse and drag to the left of the desktop.

Does anyone else have this problem?  Better, does anybody know how to fix this problem?

Thanks a million in advance,
Douglas

---

### Post by gtrtx on 2007-08-19
Under window management, make sure you have the Move Window box checked.

I can't seem to get the cube to work. I can get it to flip when dragging a window, but I can't control it with my mouse. Many of the items in the ccsm don't seem to be working properly as mentioned in another post. 

Did you do anything in particular to get the cube to work. Or did it just work?

---

### Post by Lord Illidan on 2007-08-19
It's working fine. with the keyboard. But I cannot move the cube with the mouse as I used to do so by clicking on the desktop and dragging. I have to press CTRL ALT and then drag with the left mouse button.

Also Water isn't working.

---

### Post by gtrtx on 2007-08-19
Ahh....ok....that works.

Guess I'll have to live with that for the time being....

thanks

---

### Post by hyperair on 2007-08-19
These are all symptoms to the underlying problem. CompizConfig Settings Manager is having problems, as is the "ccp" plugin with Compiz Fusion. The next update should fix it I reckon. I'm using Vorian's repositories until everything blows over.

---

### Post by djrobthaman on 2007-08-19
Hmm... 

@gtrtx  You're a lifesaver.  That one little checkbox fixed it.

@ Everybody  I just checked Desktop Cube and Rotate Cube underDesktop section and I have rotation with keyboard and mouse working fine.  Sorry if this doesn't help.

But thanks for all the info

---

### Post by klato on 2007-08-19
i just updated too and now all my settings are gone :(

also i have no window borders any more... :(:( (nvidia)

---

### Post by KhaaL on 2007-08-19
All my settings are FUBAR aswell. 3D windows & Screensaver plugins dosen't work for me, and move window can't be setup... gah!

Anyone who can point me to vorians repository?

---

### Post by theanswriz42 on 2007-08-19
Well, it's refreshing to see I'm not the only one having the problem :lolflag:

---

### Post by Syirrus on 2007-08-19
I updated today and when I run compiz --replace, I can see only 1/4 of my screen in the upper left hand corner.  I'm a 8800 GTX nvida user.

---

### Post by theanswriz42 on 2007-08-19
> **Syirrus said:**
> I updated today and when I run compiz --replace, I can see only 1/4 of my screen in the upper left hand corner.  I'm a 8800 GTX nvida user.

Clearly your graphics card isn't  good enough to run Compiz :lol:

---

### Post by KhaaL on 2007-08-19
hmm, i put vorians repo in my sources.list file and ran update/upgrade... with no success... anyone who can guide us out of this mess? :(

---

### Post by hyperair on 2007-08-19
@Khaal: Once you've added Vorian's GPG key and his server to the sources.list and whatnot:
```

sudo apt-get autoremove --purge compiz*
sudo apt-get install compiz compizconfig-settings-manager ubuntu-desktop

```

@theanswriz42: Actually the GTX is one nVidia card that's so new it has not been completely supported yet. That's what I hear anyway. If my nVidia Geforce 4 MX 440 AGP 8x can run Compiz Fusion smoothly, then obviously the GTX can. Please don't go spreading misinformation like that.

---

### Post by KhaaL on 2007-08-19
Thanks, I'll try that tomorrow after work if it hasn't been fixed by then...By the way, I assume that with GTX you're referring to 8800GTX, right? because my 7900GTX has been working nicely with me here :)

---

### Post by hyperair on 2007-08-19
Yes I mean the 8800GTX

---

### Post by djrobthaman on 2007-08-22
Whoa... I guess I'm not the only person having problems.  I hope all you guys figure yours out, but on the subjet of compiz problems... has anybody found that they have a problem with their scale plugin?

I have scale enabled (it gives the mac expose type functions) and in previous versions I was able to drag a file from one window to the top right corner and the windows would all pop up, then if i kept it over another window it would focus and i could drop it in there.

That doesn't work anymore.  Any ideas on how to get it to work like that again???

Thanks

Edit:  Now that I'm trying I actually can't drag files across sides of the cube either.  Before if I dragged a file to the right edge the cube would flip and I'd be on the other side.  Any ideas there?

---

### Post by santiagoward2000 on 2007-08-22
Hi everyone! I'm having all those problems since I updated Compiz-Fusion yesturday from Treviño's repositories.
djrobthaman, about the problem with the scale plugin, when I turn it on, it doesn't show me the windows on all viewports, only the ones in the actual view.
Besides, the Viewport Switcher and the ScreenSaver plugins aren't working any longer, and I can't move windows from one viewport to another by draging.
I hope these problems will be fixed with the new update.:???:

---

### Post by gtrtx on 2007-08-22
From this post it doesn't look as if the next update is going to fix these issues:

[http://forum.compiz-fusion.org/showthread.php?t=1012&page=9]("http://forum.compiz-fusion.org/showthread.php?t=1012&page=9")

Of course it's quite possible that I've interpreted that incorrectly....but....

I've gone back to the Trevino repos that worked fine prior to all of this happening. I did so by following these instructions:
[URL="http://forum.compiz-fusion.org/showthread.php?t=3432"]
http://forum.compiz-fusion.org/showthread.php?t=3432[/URL]

Now everything is peachy.......:guitar:

hope this helps someone....

---

