---
title: "Compiz Fusion Help"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by j00j07 on 2007-10-22
Well, I recently upgraded to Gutsy and I'm having problems with Compiz, like almost everyone else in the world it seems. Since I have installed Compiz Fusion I no longer have 4 desktops, only two. How do I get 4 again ... PLEASE HELP !:confused:

---

### Post by VictorR on 2007-10-22
See this thread:


What I have done and can recommend:
1. System -> Administration -> Software Sources
  1.1  Third Party Software tab
  1.2. look for "http://download.tuxfamily.org/3v1deb feisty eyecandy" or something similar and deleted them from the list (I had two lines)
  1.3 add a new repository:
```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
```
   1.4. Close Software sources, it should re-read information.
2. System -> Administration -> Synaptic Package Manager
  2.1 search for "compiz" (and may be "emerald") and mark all installed packagres for removal
  2.2 click "Apply" to remove them
  2.3. search for "Compiz" again and install what you have just removed back, but now it will be from another repository

Now you will likely be able to start CompizConfig Settings Manager and re-set some settings, you lost. The utility is brand new and some assignments look quite tricky now.

Emerald-themes were not found, seems they must be in some other repo I don't know about. But I used my own themes which remained in the local folder.

---

### Post by ferrocene on 2007-10-22
I'm in the same boat.  Apparently I don't have Xgl present.  I also have no themes, so therefore no borders for my windows.  I miss beryl. :(

---

### Post by lordgreg on 2007-10-22
yes! this worked. thank you VictoR. just remove all compiz thingies and install it back with emerald. then, put emerald back to session manager (if you want emerald to run at startup with command "emerald --replace"). 

flawlessly! 

thank you:)

---

### Post by j00j07 on 2007-10-22
I got it to work thanks ... i just opened up CCSM went to General Options and then to desktop and changed my Horizontal Virtual Size to 4:)

Also in reply to  ferrocene just open up a new terminal and type
```
metacity --replace
```

---

