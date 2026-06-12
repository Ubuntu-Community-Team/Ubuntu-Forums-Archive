---
title: "Amarok shortcut keys not working in breezy"
date: 2005-11-15
forum: Desktop Environments
---

### Post by jubei on 2005-11-15
Hey guys, just upgraded to breezy from hoary and so far its going pretty well.

I'm having a small issue with amarok though. The shortcut keys for pause, play, stop, etc aren't working. They all invovle the windows key (eg winkey+c is pause)

My k hot keys shortcuts that involved the windows key aren't working anymore either so I'm wondering if its related to my keyboard setup or something.

Any help would be greatly appreciated. Thanks.

Jubei

---

### Post by verahsa on 2005-11-17
I started with Ubuntu, (as opposed to Kubuntu), and Amarok shortkeys worked fine in Gnome, but when I switched to KDE, they stopped working.

After a little bit of research, I found out what's going on. Apparently, if you don't have the "layout" set just right, KDE takes the input from multimedia keys on your keyboard and send the input straight to null, interepreting them before they ever hit the application side of things. 

After turning my Layout (Settings -> Regional/Accessibility -> Keyboard Layout) to Logitech (in my case), all my keys started working again. I can't speak for ctrl-alt-(key) combinations, because I wasn't using them. I know this isn't a direct response, but it might be the same root to a slightly varied problem. See if it helps out, either way. 

Hope this helps. =)

---

### Post by jubei on 2005-11-19
Thanks for the info, I tried enabling keyboard layouts and various logitech keyboards but none helped. Any other ideas?

---

### Post by theToolman on 2006-10-08
I had similar problem.  Fresh Dapper install with kubuntu installed, Amarok worked but global keys didn't get picked up. (eg win-C)

as 'verahsa' said, went to "Settings -> Regional/Accessibility -> Keyboard Layout" and flicked to the Xkb tab, enabled 'Enable xkb options' and modified  the section called "Alt/Win key behaviour" to "Meta is mapped to the Win keys", Applied then seems to work!

Hope this helps.

---

### Post by mckayc on 2006-11-11
I have had the same problem since upgrading to Edgy.  It is quite frustrating.  Gnome works just fine, but KDE does not.  It turns off Num Lock (even though it is set to turn on.  It actually turns on then turns off after about half a minute and won't turn back on even if you press it).  The left Alt key works but the right does not.  Frustrating indeed.  I have tried everything here but it does not seem to work.  There are no options available for keyboard layout.  Anyone know how to add layouts?

---

