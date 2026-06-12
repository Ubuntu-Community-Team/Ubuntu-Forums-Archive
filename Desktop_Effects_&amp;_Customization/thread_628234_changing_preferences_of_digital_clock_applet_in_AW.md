---
title: "changing preferences of digital clock applet in AWN?"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by alwiap on 2007-12-01
I have AWN, and I added the applet 'Digital Clock Applet'.  When I right-click the applet because the font color is black and I can't see it with a dark background, and go to Preferences, nothing happens.  I would like to change the color and keep the digital time in the dock, does anyone else have this problem, or have any workarounds?

---

### Post by unabatedshagie on 2007-12-01
Which digital clock do you have and what version of awn are you running?

---

### Post by alwiap on 2007-12-01
ah, forgot to mention.

I'm running the latest edition of AWN, on 7.10 GG, and I'm just using the applet that can be found in AWN manager > Applets > Digital Clock Applet.

---

### Post by unabatedshagie on 2007-12-01
Do you have awn-extras installed?

---

### Post by alwiap on 2007-12-01
> **unabatedshagie said:**
> Do you have awn-extras installed?

um, no, not that I can think of.

If you have AWN, can you access the preferences to the digital clock?  just wondering.

---

### Post by pedro.solorzano on 2007-12-14
I have exactly the same problem and cannot access either, any thoughts about that? do you know where are the configuration files stored in order to try to modify them manually? 

Thanks in advance.

---

### Post by mattchess on 2007-12-14
Same issue here.  Clicking on preferences for the digital clock does not allow you to change the preferences, which is defaulted to black text.

---

### Post by pedro.solorzano on 2007-12-14
I found some files under /usr/lib/awn/applets/digitalClock/ but I dont know which of them can help. Theres one xml file, prefs.glade and has some color properties:

                  <widget class="GtkColorButton" id="shadowcolor">
                    <property name="color">#000000000000</property>
                  </widget>

                  <widget class="GtkColorButton" id="fontcolor">
                    <property name="color">#000000000000</property>
                  </widget>

But I think it refers to some button, tried to change to FFFFFFFFFFFF but nothing happens after reboot. In the py code you can find the launch instruction for preferences, but I dont know phyton, there is also a function to parse colors that we can force to return always white, but still... There should be a more easy way!!!

Any thoughts?

---

### Post by pedro.solorzano on 2007-12-14
Little googling about it and I found this solution that worked fine for me:

[https://bugs.launchpad.net/awn-extras/+bug/174827](https://bugs.launchpad.net/awn-extras/+bug/174827)

thanks to the authors.

Hope it helps.

---

### Post by mattchess on 2007-12-14
That did the trick for me

---

### Post by binnaeus on 2007-12-31
For me too, thank you very much :)

---

### Post by oni5115 on 2008-02-20
thanks, was also wondering how to make this work since it was the only digital clock applet and I use a dark theme.

---

