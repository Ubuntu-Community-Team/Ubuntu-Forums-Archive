---
title: "Compiz ring switcher"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by Smaf on 2007-10-02
I'm a gutsy user. For some reason, when ever I try enabling ring switcher in compiz fusion, it automatically unselects it.
This also happens with:
Negative
Opacity
Expo
Animations
Window Previews
JPEG
Text
Resize Info
Userspace File System
Put
Window Rules

No messages are output in terminal. Can anyone help please?
Thanks.

---

### Post by Rupertronco on 2007-10-02
I got rid of the default compiz immediately when I installed gutsy, but this isjust a guess. Either the above have shared keybindings with another plugin, or they're unstable and currently not working. 

Like I said I'm not familiar with what version of CF is on gutsy by default, but those would be my guesses. Especially with the ring switcher, it has the same keybindings as the shift switcher plugin (if that's even there). 

I'm suprised animations isn't working, and expo too. They're both pretty stable features, maybe someone who's used the default CF on gutsy can shed some more light on the situation.

---

### Post by supertones on 2007-10-02
I just wanted to let you know that your not alone on this issue as I am also having trouble.

Also how do you disable keyboard shortcuts for a keyboard feature.  I had accidentally disabled my d key for a little bit.

Virtual workspaces just piss me off in compiz on kde as 2 of my desktops now seem useless yet show up in the window preview.  

Compiz needs to get finished as its very frustrating to have something so cool and so close to working, and yet not be able to use it.


-archer

---

### Post by Smaf on 2007-10-03
Interesting. After the latest updates, the above options have been greyed out.

---

### Post by CK0y0TE on 2007-12-14
Linux and CompizFusion are new to me, but I love it.

Same problem here. All mentioned options are turned off once the compiz settings manager is restarted. Also while compiz settings manager is held open and checkbox, for example on ring switcher is checked, the specific feature does not work. 

I'am afraid I messed up myself by installing additional compiz configuration tool in feisty(now upgraded to gutsy). 
Options available are:
 - "System -> Prefferences -> Advanced Desktop Effects Settings". I get "CompizConfig Settings Manager" window
- "System -> Prefferences -> Compiz Settings Manager". I get "Compiz Configuration" window with some options missing and some additional.
- "System -> Prefferences -> Appearance -> tab visual effects -> custom" I get "CompizConfig Settings Manager" window.

My assumption is it was not wise to mess with two settings managers on the same database/config file(whatever the backend is)
.
I remember for sure having, accidentally, once opened them both, made changes, and closed again. (last open-first closed with changes) I do not remember which tool was first opened and last closed as I didn't see any  troubles direct after I noticed this *possible dangerous action ?*

But, could it be the source of it? Or is the compizfusion backend 'smart' enough to prevent corruption?

I will try restting defaults and stick to one settings manager. If that does not work I will reiinstall compiz to see if that works. (unless someone can tell me I don't have to)

cheers

---

