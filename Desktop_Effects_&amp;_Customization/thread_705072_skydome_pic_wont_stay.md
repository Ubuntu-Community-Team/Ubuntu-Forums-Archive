---
title: "skydome pic wont stay"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by gp95ac on 2008-02-23
As the title suggests, I've got compiz-fusion working just peachy, but every time i fire the comp up, the skydome i previously selected is gone, just left with the default blue-grey stuff.  When i check the ccsm settings, the image i selected is still there as it should be being displayed, yet no dice.

any way to fix this?  or maybe an issues with the old hardware and im lucky to have c-f at all?....933mhz, PIII,, nvidia geforce2...64mb(maybe)

btw, everything else, cf-wise is great, wobbly, cubey, fire, ring switcher, etc


just a persistant bother, have to reload the skydome before i wow my windows enslaved friends

lets figure this out so everyone moves to ubuntu (at least everyone i can convince)
thanks
gp

---

### Post by Old_Grey_Wolf on 2008-03-09
I'm having the same problem. 

After getting an image to work, I thought everything was fine except after restarting the computer or a logoff - login caused the problem you are seeing.

---

### Post by alsamman on 2008-03-09
Might be a problem that it can't find the directory. Make sure when you upload the picture, don't delete it or move it to another folder. Try that and see if it works

---

### Post by Old_Grey_Wolf on 2008-03-09
> **alsamman said:**
> Might be a problem that it can't find the directory. Make sure when you upload the picture, don't delete it or move it to another folder. Try that and see if it works

It is not that the .png file has been moved. The same file shows in the CompizConfig Settings Manager. It is that I have to uncheck Skydome or Animate Skydome them check them again to get skydome to work after a computer startup or a logoff - login.

---

### Post by Old_Grey_Wolf on 2008-03-10
Here is the fix:

Open the CompixConfig Settings Manager. In preferences select the Plugin List tab, Uncheck the automatic plugin sorting box. Us the Up/Down buttons to put png, imgjpeg, and svg before cube and cubecaps in the Enabled Plugins list.

---

