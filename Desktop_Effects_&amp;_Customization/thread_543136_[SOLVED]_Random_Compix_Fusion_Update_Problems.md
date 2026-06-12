---
title: "[SOLVED] Random Compix Fusion Update Problems"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by phynix on 2007-09-04
I am curious to see if anyone has these problems. I am using trevinos repos and it seems it wants to update Compiz Fusion every other day. I am hesitant to do this because everytime something is not right. First time some settings were put back to default while others were not. Second time it crashed awn and no i can no longer do ctrl-alt-Right to switch desktops. On the whole not that big of a deal but I would like to fix it. 

Thanks

---

### Post by jackmc on 2007-09-04
Trevino's repo is bleeding edge, and it normally does get updated every day. I can't remeber the repo, but there is another one that is more stable. Have a look on forums.opencompositing.org

---

### Post by smithman89 on 2007-09-04
Im also having the problem with turning right, devs probably forgot to put a keyboard input select for it when updating the gui of ccsm.  Edit:  Also, almost all of the "extra" unsupported options are missing in the new update.

---

### Post by rainwalker on 2007-09-04
My icon for CCSM disappeared...

---

### Post by amadeus266 on 2007-09-04
You should try amaranth's repo. It is backported from gutsy so it is more stable. doesn't have all of the plugins yet but not all of them will work on my system anyway so I don't miss them much. Try this: [https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth](https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth)

---

### Post by NilsHG on 2007-09-04
Update broke my compiz fusion too (from trevinos repos) ...
i cannot even use alt + tab to switch application windows anymore. not even in metacity. any ideas? i did uninstall all compiz related stuff but the porblem remains.

*EDIT*
> **amadeus266 said:**
>  Try this: [https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth](https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth)
These repos did work. Everything is back to normal. All hotkeys work. Ubuntu showed system update for compiz core right after install, but for tonight (3:37 am here) i do not dare to update.

*EDIT2*
I cant seem to find the MacOSX Exposé like plugin. :( What is it called in compiz?

---

### Post by praet on 2007-09-05
The endless update could be because of a recent bug in PPA.  You can either wait for the bug to be resolved or ignore the same version update by placing compiz-core on hold.

The plugin you are looking for is called Expo.  Check if it is available by the search in ccsm, also check that it is enabled in ccsm > Preferences > Plugin List.

---

### Post by Inxsible on 2007-09-05
> **rainwalker said:**
> My icon for CCSM disappeared...

Mine too :(

But the Ctrl + Alt + Right still works. I need to be able to rotate my cube with my mouse buttons(without hitting ctrl or alt). Does anyone know how to do this ?

---

### Post by praet on 2007-09-05
There is a plugin to enable cube rotation with the mouse called "Viewport mouse switch"

---

### Post by Inxsible on 2007-09-05
> **praet said:**
> There is a plugin to enable cube rotation with the mouse called "Viewport mouse switch"
I have two plugins called Viewport Switcher and Mouse Switch. I have both enabled. I don't even know what Mouse Switch does, 

In Viewport Switcher, which setting do I have to enable ?

---

### Post by Inxsible on 2007-09-05
Never mind, I got it working now...

---

### Post by NilsHG on 2007-09-05
> **praet said:**
> 
The plugin you are looking for is called Expo.  Check if it is available by the search in ccsm, also check that it is enabled in ccsm > Preferences > Plugin List.

I have Expo. But, for me, it zooms out and shows me all 4 virtual desktops. 
What i am looking for is the following: It shows you all open app windows by minimizing them and arranging them all next to each other. Mouse over one miniature highlights that one. right click brings the window up front for closer look, left click switches to that app window. mouse 3 (pressing my mouse wheel) closes the app window. I cant find it in my current setup, nor in the Expo settings.

Any more ideas?

---

### Post by Inxsible on 2007-09-05
> **NilsHG said:**
> I have Expo. But, for me, it zooms out and shows me all 4 virtual desktops. 
What i am looking for is the following: It shows you all open app windows by minimizing them and arranging them all next to each other. Mouse over one miniature highlights that one. right click brings the window up front for closer look, left click switches to that app window. mouse 3 (pressing my mouse wheel) closes the app window. I cant find it in my current setup, nor in the Expo settings.

Any more ideas?
That's similar to the Scale plugin...except that I don't think you can close the window by mouse 3...But maybe you can ..At least I don't know if you cand :)

---

### Post by NilsHG on 2007-09-05
> **Inxsible said:**
> That's similar to the Scale plugin...except that I don't think you can close the window by mouse 3...But maybe you can ..At least I don't know if you cand :)

SCALE! Thanks! Thats the one. It did have a different default action key than before and no screen corner assigned. 
furthermore i thought scale had something to do with resizing app windows... duh! 
and yes, you can close app windows with mouse 3 when in overview mode. it works for me, just tested it. 

regards

---

### Post by Inxsible on 2007-09-05
> **NilsHG said:**
> SCALE! Thanks! Thats the one. It did have a different default action key than before and no screen corner assigned. 
furthermore i thought scale had something to do with resizing app windows... duh! 
and yes, you can close app windows with mouse 3 when in overview mode. it works for me, just tested it. 

regards
Interesting... I didnt know it could close windows.. Will try that out tonite :)

---

### Post by NilsHG on 2007-09-05
> **Inxsible said:**
> Interesting... I didnt know it could close windows.. Will try that out tonite :)

I find that to be very usefull!

Another question (sorry for asking, will try to find an answere myself tomorrow. for now its almost bedtime ;) )
There was something i could do to prevent compiz from losing window frames... that just happend. no big deal, but it is annoying. there was some line I could add somewhere to prevent that from happening. any ideas?

until tomorrow ;)

---

### Post by phynix on 2007-09-06
Ok so now it is doing it again. I will try out that new repo and see if that helps any. I almost forgot I had post this. Hopefully that will fix it and I will let you guys know. Thanks for the help.

---

### Post by phynix on 2007-09-06
I must have done something wrong because when i updated the whole thing when bad. I lost all window borders and blah blah blah. I found this guide and guess what..... they don't use Trevino's repos. 

[http://ubuntuforums.org/showthread.php?t=533476]("http://ubuntuforums.org/showthread.php?t=533476")

---

