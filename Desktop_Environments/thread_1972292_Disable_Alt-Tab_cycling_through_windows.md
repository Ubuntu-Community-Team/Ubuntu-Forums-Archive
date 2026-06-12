---
title: "Disable Alt-Tab cycling through windows"
date: 2012-05-03
forum: Desktop Environments
---

### Post by Lupius on 2012-05-03
Just got a new Ubuntu machine set up at work, running 10.04 LTS with Gnome 2.30 and Compiz 0.8.4.

I really hate the way how Compiz does the app switching. It used to be that in Windows and all other old and new versions of Ubuntu I used, Alt-tabbing gives you a list of icons that you can cycle through and choose the window you want. On top of this simple functionality, Compiz would cycle through the actual windows, which is really distracting.

Is there some way to set it so that the window is brought to the foreground only after I release my alt-tab? I went through all the options in CCSM and couldn't find anything that works.

---

### Post by Lupius on 2012-05-04
Daily bump

---

### Post by 3Miro on 2012-05-04
I only have 12.04, so I am using different Compiz, but here is what I can do.

In CompizConfig-Settings-Manager, there is Windows Management section with several possible switchers. I use the basic Application Switcher that gives you preview of all the windows (I disable the zoom, I like it better that way). However, there is another option inside, in General "Only Show Icon".

Hope this works for you.

---

### Post by Lupius on 2012-05-07
Thanks for the reply. The option that worked for me was Appearance -> Selected Window Highlight -> Highlight Mode. The menu was collapsed by default so I didn't see it the first 10 times.

---

