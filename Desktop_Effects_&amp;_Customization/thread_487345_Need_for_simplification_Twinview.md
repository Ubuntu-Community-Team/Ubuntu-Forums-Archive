---
title: "Need for simplification: Twinview"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by Ragnar0k on 2007-06-29
Oh you have no idea how infuriating this was, setting it all up right.

I have 1 CRT, on the left of my main LCD monitor. What I wanted was, simply, the LCD as the main, workspace to stretch across both halves, the ubuntu panel not to run off to the left, and for windows to only maximise onto one display. Essentially I wanted [this.]("http://i144.photobucket.com/albums/r200/Ragnarohk/twinviewright.png")

Now, I had achieved this before, so I reinstall Ubuntu confident that it can't be "that hard", in fact it should be easier now with the progression of linux. No, it wasn't. Twinview was easy enough to set up, but only to set up wrong. The panel ran across both monitors, windows maximised across both screens, everything was borked. I fiddled with nvidia-settings, at some point, I enabled xinerama, save, rebooted X, disabled xinerama, rebooted, enabled twinview again, rebooted, and now everything's EXACTLY HOW IT SHOULD BE. However I achieved this purely via mystic infuriating voodoo. 

Essentially, somehow in some setting you need to be able to:
1. Define primary display.
2. Define entrenchment of panel.
3. Technical term for maximising to one monitor only.

If anyone's working on an OSS solution, I'd happily help out. This is my first post on the forums (which I have found over time to be a source of much help) because linux has done nothing this bad to infuriate me in years!  It's horrid because in windows, it's much easier. I hate to admit it, but it is:
*Click* 
*Drag* 
*Select resolution* 
*Check the "extend desktop here" box* 
*Check "primary monitor box*" *Hit Apply*.

Now, I'm cradling my Xorg.conf file like it's my baby in case I ever reinstall again...

Hopeful for some opinions and insight,
-Rag

---

### Post by bake7221 on 2007-06-29
If you are using a newer Nvidia card and installed the drivers from their website, than you can type ```
 sudo nvidia-settings 
``` and that will put you in a position to edit it like windows. You need to be more specific, what card are you using, what driver do you have installed, whats your xorg.conf file look like? There are alot of people that know a whole lot more than I ... that can use that stuff ... but I hope what I suggested helps.

---

### Post by lazzers on 2007-07-12
> **bake7221 said:**
> If you are using a newer Nvidia card and installed the drivers from their website, than you can type ```
 sudo nvidia-settings 
``` and that will put you in a position to edit it like windows. You need to be more specific, what card are you using, what driver do you have installed, whats your xorg.conf file look like? There are alot of people that know a whole lot more than I ... that can use that stuff ... but I hope what I suggested helps.
  It's to laugh! I've spent most of the day trying to do this (I had it working once in another Ubuntu life)--I've got the Nvidia settings GUI, please explain where the settings are to do this.

---

### Post by Shed on 2007-07-12
KDE handles two monitors way better than Gnome :) . Seperate taskbars, seperate (or one) desktop background, Send to Next Screen keyboard shortcuts and so on. That's once you've used NVidia's drivers to get both on and recognised, of course.

---

### Post by Underpants on 2007-07-18
So, does anyone have an answer for how to configure this? I want the exact same setup (except i want the "extra" screen on the right) 

Where's the love?

---

### Post by Underpants on 2007-07-18
> **Ragnar0k said:**
> Oh you have no idea how infuriating this was, setting it all up right.

I have 1 CRT, on the left of my main LCD monitor. What I wanted was, simply, the LCD as the main, workspace to stretch across both halves, the ubuntu panel not to run off to the left, and for windows to only maximise onto one display. Essentially I wanted [this.]("http://i144.photobucket.com/albums/r200/Ragnarohk/twinviewright.png")

Now, I had achieved this before, so I reinstall Ubuntu confident that it can't be "that hard", in fact it should be easier now with the progression of linux. No, it wasn't. Twinview was easy enough to set up, but only to set up wrong. The panel ran across both monitors, windows maximised across both screens, everything was borked. I fiddled with nvidia-settings, at some point, I enabled xinerama, save, rebooted X, disabled xinerama, rebooted, enabled twinview again, rebooted, and now everything's EXACTLY HOW IT SHOULD BE. However I achieved this purely via mystic infuriating voodoo. 

Essentially, somehow in some setting you need to be able to:
1. Define primary display.
2. Define entrenchment of panel.
3. Technical term for maximising to one monitor only.

If anyone's working on an OSS solution, I'd happily help out. This is my first post on the forums (which I have found over time to be a source of much help) because linux has done nothing this bad to infuriate me in years!  It's horrid because in windows, it's much easier. I hate to admit it, but it is:
*Click* 
*Drag* 
*Select resolution* 
*Check the "extend desktop here" box* 
*Check "primary monitor box*" *Hit Apply*.

Now, I'm cradling my Xorg.conf file like it's my baby in case I ever reinstall again...

Hopeful for some opinions and insight,
-Rag

I've found the magical command that makes TwinView do what we want it to. I noticed that by default, even using nvidias gui, it never put the words "twinview" in the xorg.conf file. I googled around and came across this command 

```
sudo nvidia-xconfig --twinview

```

As soon as I restarted X, windows snapped to their respective monitor and all of the toolbars and things were on one screen just as you show in your screen shot.

---

### Post by mattalexx on 2007-11-09
> **Underpants said:**
> ```
sudo nvidia-xconfig --twinview

```

Thanks much for this. Worked for me.

---

