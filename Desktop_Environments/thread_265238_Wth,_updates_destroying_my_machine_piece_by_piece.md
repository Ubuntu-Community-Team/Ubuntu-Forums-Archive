---
title: "Wth, updates destroying my machine piece by piece"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Rippy on 2006-09-25
About a week ago, I installed the latest updates to my Ubuntu machine, seeing the notification icon. I restart, then go to play Tremulous immediately after. The screen flickers, then my resolution is drastically increased and the game exits without an error message. Nexuiz does the same thing but without the resolution change, same goes for Enemy Territory. All my non-standard games I have installed don't work (Gnometris, etc work fine). The thread I started about it received no replies, and no update has come to fix this.

Just ten minute ago, I download the recent updates again, then firefox wants me to restart. I go to bookmark the thread I'd just created (sound issue), the button did nothing, and so I figured I'd just copy the url, and paste it in my restarted and hopefully fixed up firefox. No luck, the bookmark button does nothing and most every other icon gives me this error:

```
XML Parsing Error: not well-formed
Location: chrome://browser/content/bookmarks/bookmarksManager.xul
Line Number 1, Column 8:" src="chrome://global/content/nsTransferable.js"/>
-------^
```
The last line differs depending on the toolbar button clicked. So now I'm gonna have to hope I can track these threads to get the answers out of them.

All in all, I'm frustrated. Maybe I'm one of the only people to which this has happened, but that's no less annoying. I've slaved for hours and hours getting ATI drivers working, getting sound working, and fixing other hardware and software issues, all in the name of a linux machine I could use for games too. But as soon as I've overcome one obstacle, the next one slaps me in the face. I'm just extremely happy I backed up this install a couple weeks ago, I'm gonna have to save this image just in case then revert to the other one in order to play my linux games again.

Sorry for venting, I'm just pretty frustrated at the moment. If there's any forseeable fix to any of those issues, other than staying with the old image and never updating, my frustration will subside and I will be quite happy.

Any help is appreciated,

-Rippy

---

### Post by avtolle on 2006-09-25
When one updates the kernel, as has occurred more than once lately, one must recompile the drivers for his video card. Have no suggestion about the bookmark problem.

---

### Post by jdong on 2006-09-25
Well, the Firefox error typically means that your firefox did not actually restart (there's a window open still, or it's hanging on exit). Have you tried restarting?

And with each kernel update that "breaks the ABI" (i.e. any of the version numbers in the package name change), you will have to recompile all custom drivers, including potentially your video and sound drivers.

---

### Post by Rippy on 2006-09-27
Well, after leaving Ubuntu alone for several days, I'm ready for a fresh, non-angry start. I'm sure I just have to recompile the graphics drivers, although it'd be handy for the updater to tell you when the kernel is updated so that you can recompile. As for firefox, I'll have to see. Noone else seems to be complaining about it, so it can't be a faulty update, but I haven't tried it lately to see if it works well again.

Anyway, it's late here so I'll try things out tomorrow and post here again if I still have issues. Thanks for the help! :)

---

