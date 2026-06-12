---
title: "Open programs in the center of the screen."
date: 2010-08-31
forum: Desktop Environments
---

### Post by EgoGratis on 2010-08-31
In KDE i can set how i want to open programs. So they "pop-up" in the center of the screen when i start them.

Can i set the same behaviour in Gnome? Now programs open in top left edge.

Ubuntu 10.04.

[LEFT]Thanks for the answers!
[/LEFT]

---

### Post by EgoGratis on 2010-08-31
No answer. Then probably  gnome does not support this feature at thih moment?

---

### Post by hhh on 2010-08-31
If you are using Compiz (meaning you have "desktop effects" enabled) then this is pretty easy. Install the CompizConfig Settings Manager. In a terminal...
```
sudo apt-get install compizconfig-settings-manager
```

Then navigate to System>Preferences>CompizConfig Settings Manager>Window Management>Place Windows, enable the plugin and under General set the placement from Smart to Centered. There will still be the odd window that will not open centered, these can be tamed by Window Matching...
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)
..so, for example, in Force Placement Windows I added... 
```
dialog | title=Vagalume
```
... so that Vagalume (a last.fm client) and the Weather dialog (part of the Gnome panel clock) would open centered.

If you aren't using Compiz it means you're using Metacity. There is a patch for that which I can't help you with as I've never used it, I've never applied a patch and it looks out of date...
[http://chad.glendenin.com/metacity/patch.html](http://chad.glendenin.com/metacity/patch.html)

HTH

---

### Post by EgoGratis on 2010-09-01
OK so this is the deal:
[B]
Metacity NO[/B]

[B]Compiz YES
[/B]
Thanks for answer. I will mark this thread as solved.

---

### Post by Jose Catre-Vandis on 2010-09-01
If you don't want to use compiz, try **[COLOR="DarkOrange"]devilspie[/COLOR]**, in the repos

Useful howto: [http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)

---

### Post by EgoGratis on 2010-09-01
The problem is with nouveau drivers i can only use metacity for now. For compiz i would have to use binary drivers.

So i will wait and maybe in the future. I will be able to use compiz with nouveau. Or if i use PC when binary drivers are installed. I will try suggested solution from user named hhh.

So the problems is not compiz. But the nouveau drivers are just not there yet. :)

But still thanks for the alternative answer. I will look in to it!

---

### Post by wojox on 2010-09-01
> **hhh said:**
> If you are using Compiz (meaning you have "desktop effects" enabled) then this is pretty easy. Install the CompizConfig Settings Manager. In a terminal...
```
sudo apt-get install compizconfig-settings-manager
```

Then navigate to System>Preferences>CompizConfig Settings Manager>Window Management>Place Windows, enable the plugin and under General set the placement from Smart to Centered. There will still be the odd window that will not open centered, these can be tamed by Window Matching...
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)
..so, for example, in Force Placement Windows I added... 
```
dialog | title=Vagalume
```
... so that Vagalume (a last.fm client) and the Weather dialog (part of the Gnome panel clock) would open centered.

If you aren't using Compiz it means you're using Metacity. There is a patch for that which I can't help you with as I've never used it, I've never applied a patch and it looks out of date...
[http://chad.glendenin.com/metacity/patch.html](http://chad.glendenin.com/metacity/patch.html)

HTH

Thank you. Those few odd windows (weather report) drove me crazy.

---

### Post by AmpersUK on 2011-03-04
*> **hhh said:**
> Then navigate to System>Preferences>CompizConfig Settings  Manager>Window Management>Place Windows, enable the plugin and  under General set the placement from Smart to Centered.*

Re:*Then navigate to System>Preferences>CompizConfig Settings  Manager>Window Management>Place Windows, enable the plugin.*

**I have managed to do this.**

*...and  under General set the placement from Smart to Centered.*

[B]Not too sure what you mean here.

I clicked on "General" and then "General Options" And couldn't find what you meant. I couldn't find any other "General" I am in Ubuntu 10.10.[/B] 

Ampers.

---

### Post by Krytarik on 2011-03-04
@AmpersUK: You have to navigate to the "Place Windows" plugin, at the bottom of CCSM, and follow the instructions from there.
> **hhh said:**
> Then navigate to  System>Preferences>CompizConfig Settings Manager>**Window  Management>Place Windows**, enable the plugin and under General set the  placement from Smart to Centered.
Greetings.

---

### Post by AmpersUK on 2011-03-05
> **Krytarik said:**
> @AmpersUK: You have to navigate to the "Place Windows" plugin, at the bottom of CCSM, and follow the instructions from there..

Ah! After a while I realised you have to click on it. All is now working and my programs are opening in the centre of the screen (or center if you are the other side of the pond) :-)

Thanks.

---

