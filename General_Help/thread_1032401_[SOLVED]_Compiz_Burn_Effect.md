---
title: "[SOLVED] Compiz Burn Effect"
date: 2009-01-06
forum: General Help
---

### Post by Vladislav Mkrtychev on 2009-01-06
OK, I have looked in a lot of places for explanation, but still looking for one that will help.
I have ccsm installed as well as Simple ccsm. All I want to do is enable burn effect on window close.
I could do it before on 8.04, but no matter what I do now on 8.10 no special effects or animations on window close, minimize or open...
Thanks you for replies!

---

### Post by tuxxy on 2009-01-06
> **Vladislav Mkrtychev said:**
> OK, I have looked in a lot of places for explanation, but still looking for one that will help.
I have ccsm installed as well as Simple ccsm. All I want to do is enable burn effect on window close.
I could do it before on 8.04, but no matter what I do now on 8.10 no special effects or animations on window close, minimize or open...
Thanks you for replies!

8.10 makes use of the new animations add-on plugin whihc may be preventing yours from working correctly.  Open compiz and navigate to effects > animations and make sure thats enabled then navigate to effects > animations add-on and enable these.  Also make sure you have selected just the fire effect and not random ones.

---

### Post by Vladislav Mkrtychev on 2009-01-06
> **tuxxy said:**
> 8.10 makes use of the new animations add-on plugin whihc may be preventing yours from working correctly.  Open compiz and navigate to effects > animations and make sure thats enabled then navigate to effects > animations add-on and enable these.  Also make sure you have selected just the fire effect and not random ones.

Hi,

I had Animations and Animations Add-On already enabled. 

In Effects > Animations, under Animation Selections I have "Burn" and under Random Effects I checked only "Burn" option.
I have the same settings for "Open Animation", "Close Animation", and "Minimize Animation".
Under Effect Settings I have "random Animations for all Effects" unchecked.

In Effects > Animations Add-On I left everything as it is.

Still no result...

---

### Post by sendblink23 on 2009-01-06
Yeah, the same thing with me . ..  :(



> **Vladislav Mkrtychev said:**
> Hi,

I had Animations and Animations Add-On already enabled. 

In Effects > Animations, under Animation Selections I have "Burn" and under Random Effects I checked only "Burn" option.
I have the same settings for "Open Animation", "Close Animation", and "Minimize Animation".
Under Effect Settings I have "random Animations for all Effects" unchecked.

In Effects > Animations Add-On I left everything as it is.

Still no result...

---

### Post by Vladislav Mkrtychev on 2009-01-06
I got it to work!

Go to Simple ccsm

Under profiles choose "Ultimate" and click the check mark.
Click on Animations tab.
Check both checkboxes.
Then select Burn effect under each desired actions (Open Window, etc.)
And that's it!

---

### Post by prcjac on 2009-02-25
Just throwing this out there for what its worth.
To fix this I completely removed compiz
```
sudo apt-get remove simple-ccsm
sudo apt-get update
sudo apt-get install simple-ccsm
```
This gives the entire compiz an overhaul with the newest version, then enable the additional effects as suggested above, Animation Add-ons

---

### Post by MoshutZu on 2009-10-07
This helped me too! Simple ccsm rocks!

---

### Post by randysilverwolf on 2009-10-13
guys...ive been at it for a while with all of the above mentioned, but then i realized something...apparantly the defualt values for the animations kinda just changed my themself, so all i did was click the button that reverted the vaules back to default (little square icon over to the right of the animation options) for each, and voila, simple 2 second fix

---

### Post by gabak on 2010-06-27
do this and u will have all the extra effects
sudo apt-get install compiz-fusion-plugins-extra

---

### Post by reborn7778 on 2011-04-05
> **gabak said:**
> do this and u will have all the extra effects
sudo apt-get install compiz-fusion-plugins-extra

you are a genius, i am so happy!

---

