---
title: "Weather screenlet in Gutsy?"
date: 2007-12-10
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-12-10
I had used screenlets in Feisty (Ubuntu 7.04) for quite some time. Now I`ve upgraded (actually a clean install) to Gutsy (Ubuntu 7.10) and have a problem getting all of my preferred screenlets, in particular, the Weather screenlet doesn`t show up in the widget layer.

What I`ve done so far is:

1) Install screenlets in the Compiz-Fusion widget layer using this [guide]("http://ubuntuforums.org/showthread.php?t=589403").
2) System>Preferences>Screenlets to add Clock and CPUMeter screenlets to my widget layer. Toggling with F9 shows these have been added perfectly
3) Download Weather screenlet tar.gz from [here]("http://hendrik.kaju.pri.ee/screenlets/?q=node/9").
4) Unzip it and add resulting folder to /usr/local/share/screenlets/ 
5) Back into System>Preferences>Screenlets and the Weather screenlet is there as a weather-looking icon (so that looks good)
6) However, using exactly the same clicks to add it to the widget layer that I already had used for the Clock and CPUMeter, no Weather screenlet shows up in the widget layer.

Can anybody point out what I might be overlooking?
Thanks
Paul

---

### Post by santiagoward2000 on 2007-12-10
> **PaulFXH said:**
> I had used screenlets in Feisty (Ubuntu 7.04) for quite some time. Now I`ve upgraded (actually a clean install) to Gutsy (Ubuntu 7.10) and have a problem getting all of my preferred screenlets, in particular, the Weather screenlet doesn`t show up in the widget layer.

What I`ve done so far is:

1) Install screenlets in the Compiz-Fusion widget layer using this [guide]("http://ubuntuforums.org/showthread.php?t=589403").
2) System>Preferences>Screenlets to add Clock and CPUMeter screenlets to my widget layer. Toggling with F9 shows these have been added perfectly
3) Download Weather screenlet tar.gz from [here]("http://hendrik.kaju.pri.ee/screenlets/?q=node/9").
4) Unzip it and add resulting folder to /usr/local/share/screenlets/ 
5) Back into System>Preferences>Screenlets and the Weather screenlet is there as a weather-looking icon (so that looks good)
6) However, using exactly the same clicks to add it to the widget layer that I already had used for the Clock and CPUMeter, no Weather screenlet shows up in the widget layer.

Can anybody point out what I might be overlooking?
Thanks
Paul

The way I added my Screenlets to the widget layer was simply by making a right-click on the Screenlet I wanted, and checking **Window/Widget**, and adding nothing to the **Widget Window** box in Compiz settings...

---

### Post by PaulFXH on 2007-12-10
Thanks for this suggestion.
However, I can`t seem to reproduce what you`re talking about.
So, if I open Screenlets Manager (System>Preferences>Screenlets) and right-click on any screenlet, absolutely nothing happens and no dialog box appears.
If I right-click on the Weather screenlet folder on my desktop (it`s there bcause that`s where I unzipped the original tar.gz file), I just get the normal right-click options (Open, Cut, Copy, Rename etc).
If I open either /usr/local/share/screenlets/ or /~/.config/screenlets/ and right-click on any screenlet folder, again I just get the same thing  -- absolutely no option with regard to window/widget.
Can you please tell me where you saw these checkboxes?
Thanks
Paul

---

### Post by PaulFXH on 2007-12-10
Seems I may have been using a Weather screenlet that was passed its sell-by date because the Clear Weather screenlet from [here]("http://hendrik.kaju.pri.ee/screenlets/") works perfectly in the CF widget layer.

---

### Post by santiagoward2000 on 2007-12-10
> **PaulFXH said:**
> Seems I may have been using a Weather screenlet that was passed its sell-by date because the Clear Weather screenlet from [here]("http://hendrik.kaju.pri.ee/screenlets/") works perfectly in the CF widget layer.

Well, that's good to hear! :)

---

