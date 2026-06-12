---
title: "Green Fire"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by domat00 on 2007-09-06
Hi all.  I recently got my computer back, reloaded Feisty and have been digging around looking for some cool effects, and came up with something called Green Fire.  I'm not 100% if it's Compiz, Compiz Fusion, Beryl or a combination of all three, so I was wondering if anyone could help me get it set up or point me to a wiki/thread.  It looks awesome and would further deter my migration towards Vista.

Rock on.  :guitar:

---

### Post by Lord Illidan on 2007-09-06
When you say green fire, do you mean something like this : [http://www.youtube.com/watch?v=iAdp30Stz5Q](http://www.youtube.com/watch?v=iAdp30Stz5Q)

If so, then it can be done with Beryl/Compiz-Fusion. I recommend using Compiz Fusion as it is new (a merger between Beryl and Compiz).

First, you have to get Compiz-Fusion or Beryl up and running. Try this howto : [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by domat00 on 2007-09-06
Ok, I can run through that how-to.  What should I be looking for package-wise?  If I choose to use emerald, will I be locked out of any of those effects?

---

### Post by Lord Illidan on 2007-09-06
No, emerald is just the window decoration.

---

### Post by domat00 on 2007-09-06
Ok, compiz is installed and running.  How exactly might I set up Green Fire?

---

### Post by Lord Illidan on 2007-09-06
System -> Preferences -> CompizConfig Settings Manager.

Then scroll to animations. Go to the Effect Settings Tab and select Fire. Change the color to green. Then, see if you want it as a close or minimise animation (or both). Either way, select the relevant tab, select one of the animations and turn it to Burn.

---

### Post by funpop on 2007-09-06
install compiz config settings manager, theres a plugin "paint fire on screen", you can choose the color there..you can also make your windows burn when closing -> check animations for that effect

---

### Post by domat00 on 2007-09-06
Having some trouble with Emerald themes.  I can view them, know which one I want, but when I double-click, nothing happens.  Do I need to consult the blog you suggested?

Right now I'm only getting a 2-D cube with 2 surfaces, instead of a 3-D with 6 surfaces.  How can I rectify this?

---

### Post by hyperair on 2007-09-06
In CompizConfig Settings Manager, go to General Options, and then head over to the Desktop Size tab. Then use these settings:
Number Of Desktops: 1
Horizontal Virtual Size: 4
Vertical Virtual Size: 1

---

### Post by [Alsharifi] on 2007-09-06
After u choose which theme u want,just keep i highlighted and then run (alt+f2)  this

```
emerald --replace
```


and if u want emerald theme to run at start up

system>>preferences>>sessions.

then new.

name=emerald
command=emerald --replace.




u can also do the same to compiz if u havent already

just replace name and command with 

name=compiz
command=compiz --replace


good luck!

---

### Post by hyperair on 2007-09-06
Oh if you're still looking for a gree fire, you can look under Animations. You choose fire as your animation for the desired event, and then go to the Animation Settings tab or something of that sort, and you change the colour of the fire to green. You can have multicoloured fire too =P

---

### Post by domat00 on 2007-09-06
Thanks a lot guys, your instructions were indispensable!  :lolflag:  I've jimmied with it and have it working just like I want it.  :)

---

### Post by hyperair on 2007-09-06
Good for you! =P

---

