---
title: "Compiz Window effects issue"
date: 2010-12-10
forum: Desktop Environments
---

### Post by Fudgcicle on 2010-12-10
I've been running Ubuntu on my laptop for a couple months now and I've been using compiz settings manager. For some reason I can't seem to get the window effects for minimizing, closing, etc. to work. I have followed a few tutorials and nothing seems to make any difference. As far as I can tell, that is the only thing in compiz that is not working. I am running Ubuntu 10.10, any ideas and help would be greatly appreciated.

---

### Post by coffeecat on 2010-12-10
I presume you mean windows on fire and beam up and similar effects? It's not at all intuitive, but this is what you do.

Open compiz config settings manager. Under Effects, go to Animations. I'll show you how to do a close animation and you can take it from there. Select the close animation tab. Select the topmost animation which is probably 'Fade'. Click on 'Edit'. A small edit window pops up. Highlight all the code in 'Window Match' and press ctrl-C to copy it to the clipboard. Close the edit window without changing anything. Now click on 'New'. Choose your effect from the drop down list and paste the code in the clipboard into the Windows Match field. Increase duration to about 200 - 50 is far too short. Close the edit window and you'll see your new effect at the bottom of the list. Highlight it and repeatedly click on 'Up' until it's at the top. The new close effect will now work.

You can repeat similarly for any other animations. Simply copy the window match code from another pre-defined effect.

By the way, you'll need to install the package compiz-fusion-plugins-extra to get some of the [s]sillier[/s] more fun effects. :)

---

### Post by Fudgcicle on 2010-12-10
Thank you! That's exactly what I needed. I appreciate the help.

---

### Post by WlaadDyaab on 2010-12-22
Thanks for the easy-to-understand reply

I've installed "compiz-fusion-plugins-extra" using Synaptic Package Manager (System - Administration - Synaptic Package Manager) the ticked the box (and chose "Mark for installation") then clicked on "Apply"...etc

Then:

Applications - System Tools - Compiz Fusion icon

Then I right-clicked it on control panel and chose "Settings Manager"

Then I chose "Animations" (not ticking the box)

Then I chose the "Close Animation"

...

That's where I got stuck :(

I can't choose/click on "Edit" because it's been grayed out

Could you help me after that please?

---

### Post by coffeecat on 2010-12-22
> **WlaadDyaab said:**
> Then I chose "Animations" (not ticking the box)

Tick it, otherwise it will not work.

> **WlaadDyaab said:**
> I can't choose/click on "Edit" because it's been grayed out

> **coffeecat said:**
> Select the close animation tab. **Select the topmost animation which is probably 'Fade'.** Click on 'Edit'.

Select = Highlight.

---

