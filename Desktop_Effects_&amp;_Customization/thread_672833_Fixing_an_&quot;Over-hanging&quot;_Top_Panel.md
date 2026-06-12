---
title: "Fixing an &quot;Over-hanging&quot; Top Panel?"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by jslmg on 2008-01-20
It's a minor point, but a slight visual nuisance, ntl:

I have a top panel that hangs out and over the app windows below it. I'd like to have the app windows at the same 3D level as the top panel, the way they look in Mac OS X. I've tried, well, not quite every setting in emerald, but as many as seemed likely to work.

I'm using Emerald, with iMetal theme installed and the Pixmap engine. I've attached a screenshot. Any simple adjustments I could make?

---

### Post by Ub1476 on 2008-01-20
If you haven installed CCSM (advanced desktop effects) do so first:

```
sudo apt-get install compizconfig-settings-manager

ccsm
```

Now go to Window Management>Check Window Rules, open it>Add **name=gnome-panel** to whatever settings you think will suit your best. I think the "below" section is what you need:)

EDIT: Or maybe "snap windows" is for you. I'm not quite sure, you would have to experience a little.

---

### Post by chrisccoulson on 2008-01-20
What you want to do I think, is disable shadows for the panel. To do this, open up CompizConfig Settings Manager (System -> Preferences -> Advanced Desktop Effects Settings). Navigate to 'Window Decorations'.

In the 'Decoration windows' box, type 'any' (without the quotes)
In the 'Shadow windows' box, type '!type=dock|any'

That will get rid of the shadows on the panel.

---

### Post by jslmg on 2008-01-20
> **Ub1476 said:**
> If you haven installed CCSM (advanced desktop effects) do so first:

```
sudo apt-get install compizconfig-settings-manager

ccsm
```

Now go to Window Management>Check Window Rules, open it>Add **name=gnome-panel** to whatever settings you think will suit your best. I think the "below" section is what you need:)

EDIT: Or maybe "snap windows" is for you. I'm not quite sure, you would have to experience a little.

Yep, I have ccsm installed (would've thought that would be necessary to have emerald, no?)

I've never liked snap windows--I prefer my windows more freely "draggable".

The Window Rules change did something, though. It's not quite what I'm looking for, but close. After entering that setting you recommended, the app windows now seem slightly higher--"hanging over"--the top panel. It does look better than the over-hanging panel, but not as integrated as Mac--yet. Some further adjustments in some other setting might get it right.

---

### Post by jslmg on 2008-01-20
> **chrisccoulson said:**
> What you want to do I think, is disable shadows for the panel. To do this, open up CompizConfig Settings Manager (System -> Preferences -> Advanced Desktop Effects Settings). Navigate to 'Window Decorations'.

In the 'Decoration windows' box, type 'any' (without the quotes)
In the 'Shadow windows' box, type '!type=dock|any'

That will get rid of the shadows on the panel.

Thanks to both of you. Either one of these changes--in "Window Rules" or in "Window Decoration"--get us close to what I'm looking for, and it'll do for now. With a little further tweaking in Emerald, I may be able to get it.

---

### Post by Ub1476 on 2008-01-20
Please tell use if you manage to do it! Would be great for those Mac4Lin guides:)

---

### Post by mannheim on 2008-01-28
A further tweak (a cheat, really). I also did not want the top panel to cast its shadow on other windows. But I **did** want the top panel to cast a shadow on the desktop. So, in addition to the above suggestions, I simply added the shadow permanently to my desktop background using the GIMP. Of course, this cheat isn't going to work if you do things like resize your screen or panel. But it gave me the look I wanted (below).

Another thing I wanted was to make the bottom panel cast a shadow on other windows, even while the top panel does not. As long as the regex plugin is loaded in compiz, you can achieve this with a rule like:
```
!(type=dock & title=Top)
```

---

### Post by Square on 2008-07-18
Hi,

I've only recently switched to Linux (from Windows ;-)), and hence am only reading this post now. I was wondering if you've managed to solve this problem 'correctly' yet, i.e. as it is in Mac OS?

---

