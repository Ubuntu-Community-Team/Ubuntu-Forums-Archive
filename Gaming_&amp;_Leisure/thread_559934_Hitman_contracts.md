---
title: "Hitman: contracts"
date: 2007-09-25
forum: Gaming &amp; Leisure
---

### Post by saltedfish on 2007-09-25
Hey, could use a spot of help here:

I installed Hitman: Contracts just fine, installation went off without a hitch etc etc. I read the Winehq page on the game, to see what had to be done to get it to work. I was told to patch it, use a no-cd crack, and to leave the disk in.

My stumbling block is at the patching. I download the patch, and tell it to run with Wine. The patcher pops up, but then informs me that Hitman: Contracts isn't installed.

I'm wondering if there is some registry that has to be updated somewhere to allow the patcher to find and update the hitman folders.

I'm running Ubuntu 7.04 and Wine 0.9.41

ps: all the other posts on hitman: contracts were concerning the installation itself, not the post installation bumpf.

---

### Post by saltedfish on 2007-09-25
shameless bump

---

### Post by cogadh on 2007-09-26
Try putting the patcher .exe file in Hitman's install directory, then in the terminal, cd to that directory and run it from there. I think that was how I had to get it to work. Also, I believe you are supposed to patch it *before* you apply a cracked .exe, otherwise the patch will fail.

---

### Post by desicratn on 2007-09-26
I had problems with installers(DOW, HL, etc) dropping out or not updating when just run under wine. Try running it in wine desktop and it seems to work great now. I dont remember the right command line input for it. Perhaps someone else knows it off the top of thier head?

---

### Post by cogadh on 2007-09-26
You can use winecfg to configure the Wine virtual desktop settings, on the Graphics tab.

---

### Post by saltedfish on 2007-09-26
thanks all, ill try that. I did put the patcher int he directory, but all I did was rightclick run in wine. Ill try it from the console.

Most of that stuff about the virtual desktop was a little beyond me, but Ill give it a try.

thanks again

---

