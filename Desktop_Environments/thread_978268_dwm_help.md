---
title: "dwm help"
date: 2008-11-10
forum: Desktop Environments
---

### Post by elmer_42 on 2008-11-10
Alright, I'm trying to use dwm, but I've run into a hitch: I can't resize windows and keep them tiled. If I resize with Alt+Mouse2, it toggles it over to floating. What can I do to prevent this? I know I can use Alt+H and Alt+L, but what can I do for vertical resizing?

---

### Post by cardinals_fan on 2008-11-11
Sorry it took so long - the forum was down and I took a bike ride (on a stationary).

I'm not sure if you can resize vertically in tiling mode - I haven't tried.  I'll take a look at it tonight and reply tomorrow :)

EDIT: Might [this]("http://bbs.archlinux.org/viewtopic.php?id=50961") be helpful?

---

### Post by hessiess on 2008-11-11
As far as im awere, It isnt possable to resize individual tiles in the stack.

---

### Post by elmer_42 on 2008-11-11
At the end of that thread, cardinals_fan, the original poster says that "no change was made." If I can't resize vertically, I'm going back to wmii.

---

### Post by cardinals_fan on 2008-11-11
Got it!  Check out [http://www.suckless.org/dwm/patches/bottom_stack.html](http://www.suckless.org/dwm/patches/bottom_stack.html)

---

### Post by elmer_42 on 2008-11-11
I'll try it out, but I don't know how to apply the patch. I've never done so before.

**e:**Just realized a "fundamental truth" of dwm: there is a main window (on the left) that ONLY contains one window. Then, on the right there are windows that share an even amount of space. What I *don't* get is why new windows open up in the space for the main window, it messes me up. Usually I open up Firefox, then open terminals as I need them. When I try to do this, Firefox gets pushed to the side, annoying me greatly. Is there a way to define which window is the main window?

---

### Post by cardinals_fan on 2008-11-11
I have to go out for 1-2 hours, but I'll edit this post with a reply when I get back.  If you don't have anything else to do, it'd be nice to have my PM (assuming it worked) in this thread.  Otherwise, I'll copy it over when I get back.

---

### Post by elmer_42 on 2008-11-11
I actually did not try it, as I read a little about it and I don't think it is what I want. There may have been some miscommunication between us, sorry about that. However, I will post the code for patching it, just in case anybody would like to try:
```
wget http://code.suckless.org/dl/dwm/dwm-5.2.tar.gz
tar xvzf dwm-5.2.tar.gz
rm dwm-5.2.tar.gz
cd dwm-5.2
wget http://bsdgroup.org/files/dwm-5.2-bstack.diff
patch < dwm-5.2-bstack.diff
```
This starts from the beginning, because it may go wrong if the patch has been applied unsuccessfully before.

---

### Post by cardinals_fan on 2008-11-12
> **elmer_42 said:**
> 
**e:**Just realized a "fundamental truth" of dwm: there is a main window (on the left) that ONLY contains one window. Then, on the right there are windows that share an even amount of space. What I *don't* get is why new windows open up in the space for the main window, it messes me up. Usually I open up Firefox, then open terminals as I need them. When I try to do this, Firefox gets pushed to the side, annoying me greatly. Is there a way to define which window is the main window?
I don't have time tonight to fiddle much, but there's some interesting doorways opened here: [http://lists.suckless.org/dwm/0802/4916.html](http://lists.suckless.org/dwm/0802/4916.html)

---

### Post by elmer_42 on 2008-11-12
Well, I just realized that you can hit Alt+Enter to set the focused window as the main window. Now that that is settled, dwm is my new wm. Thanks for all the help!

---

### Post by cardinals_fan on 2008-11-12
> **elmer_42 said:**
> Well, I just realized that you can hit Alt+Enter to set the focused window as the main window. Now that that is settled, dwm is my new wm. Thanks for all the help!
Good to hear you've solved everything.  I have Alt+Enter set to open a terminal, so I never knew that :)

---

### Post by chucky chuckaluck on 2008-11-14
> **cardinals_fan said:**
> I have Alt+Enter set to open a terminal

i do too. i switched alt+shift+enter to zoom the selected window. 

elmer, do you know about the monicle option? alt+m will maximize the selected window. then, you can use alt+j to go through all the windows you have open in that tag, with each one being maximized.

---

