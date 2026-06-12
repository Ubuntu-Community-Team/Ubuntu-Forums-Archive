---
title: "Odd window problem"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by Traldan on 2007-07-25
Alright, well I'm using Feisty and Compiz Fusion.  I have a problem where sometimes (not all the time) new windows appear as black.  It's especially noticeable in firefox - if I click a link that opens in a new window, the window appears,the title bar is there, and if I right click in the window itself it behaves as it should (I'll see the proper right-click items for whatever I would normally be right-clicking) but there's nothing in the window.  No amount of resizing, minimizing, moving from one desktop or another, or anythign else will get it to show.  It has cropped up some in other applications as well; one time the System menu even appeared black.

---

### Post by Happy_Man on 2007-07-25
That's due to the fact that if you run out of Video RAM, it isn't able to load the window and so draws it blank. Either close and reopen the window/tab, or wait a few seconds, and it should be OK.

---

### Post by Traldan on 2007-07-25
Hmm, okay.  Thanks! :)

---

### Post by pjones0404 on 2007-07-25
this is a bug in the nvidia driver as well. is that what type of video card u have?

i did the following and it is happening a lot less now. i have copied this from a different thread. 

[I]Then, launch Compiz Fusion with Alt-F2:
Code:

compiz --replace --indirect-rendering -c emerald &

The indirect-rendering option helps with the infamous Nvidia black windows when you have too many things open. On the recommendation of a post on the opencompositing forums ( [http://forums.opencompositing.org/vi...blac](http://forums.opencompositing.org/vi...blac) k+window ) I also added the following lines to my xorg.conf under the Screen section (be sure to make a backup first!):
Code:

        Option          "DamageEvents"  "True"
        Option          "UseEvents"     "True"
        Option          "TripleBuffer"  "True"

I am not sure whether the xorg.conf modifications or the indirect-rendering option alone would work; I made both changes at the same time, and restarted the GUI with Ctrl-Alt-Backspace. I haven't gotten a black window since![/I]

---

### Post by lawr_rawr on 2007-07-25
The settings pjones referenced worked well for me -- for about a day (he's quoting from my post in the Averatec 2300-series thread). 

After about a day, I started getting occasional freezing -- maybe every ten minutes or so. Sound and mouse would behave normally, but my screen would freeze for 2-3 seconds before resuming normal activity. 

After removing the three lines from xorg.conf,
```
Option "DamageEvents" "True"
Option "UseEvents" "True"
Option "TripleBuffer" "True"
```
I have only had a couple of frozen moments. Try the command for launching Compiz first, then try adding the above if you still have problems.

---

### Post by Traldan on 2007-07-25
I am indeed on nvidia.

Launching compiz with that setting just kills the window borders.  Unsure why, they normally work when I launch compiz-fusion with the command compiz-manager.

---

