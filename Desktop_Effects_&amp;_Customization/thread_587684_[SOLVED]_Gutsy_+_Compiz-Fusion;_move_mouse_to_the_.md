---
title: "[SOLVED] Gutsy + Compiz-Fusion; move mouse to the top right corner and see all the wi"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by tak1150 on 2007-10-23
This issue may have been addressed somewhere else, but I don't know exactly how to search for the information.

In Compiz-Fusion in Feisty, I could move my mouse to the top right corner and all the windows would reorganize themselves so that I can see all of them at the same time. I hope you can figure out what I am talking about :)

This feature is not turned on by default in Gutsy. How do I turn it on? I do have the CCSM installed already. Thanks!

---

### Post by spec-chum on 2007-10-23
The option you need to enable for that is Scale in the Window Management section in ccsm.

Then under Actions->General check that Initiate Window Picker For All Windows is set to  the TopRight screen edge.

---

### Post by CaptMorgan on 2007-10-23
hey that was working for me the first restart after update but I have since restarted and no luck? Whats the ccsm?

---

### Post by tak1150 on 2007-10-23
It works! Thank you!

---

### Post by spec-chum on 2007-10-23
> **CaptMorgan said:**
> hey that was working for me the first restart after update but I have since restarted and no luck? Whats the ccsm?

ccsm is the compizconfig settings manager.  It's not installed by default.  The package you need to install via synaptic is called compizconfig-settings-manager.  If you install that you'll then have an Advanced Desktop Effects Settings entry in your System->Preferences menu where you can set all sorts of lovely things. :)

---

### Post by CaptMorgan on 2007-10-23
> **spec-chum said:**
> ccsm is the compizconfig settings manager.  It's not installed by default.  The package you need to install via synaptic is called compizconfig-settings-manager.  If you install that you'll then have an Advanced Desktop Effects Settings entry in your System->Preferences menu where you can set all sorts of lovely things. :)

awesome thanks. Got that installed now :) but I dont see the Initiate Window Picker For All Windows option anywhere?

---

### Post by nholling on 2007-10-24
1. Click on System->Preferences->"Advanced Desktop Effects Settings"
2. On the right hand side of the window scroll down till you see "Scale". Its in the Window Management section. Make sure its checked and click on the the word Scale. This will show you the settings for the Scale plugin.
3. Click the Action tab at the top.
4. Open up the "General" drop down.
5. Double click on "Initiate Window Picker"
6. Click the "Top Right" checkbox. Click Ok. Close all the windows.

You should have it now.  Thanks to spec-chum for pointing it out for me.  I was missing it too :-).

-Nate

---

### Post by dennis.groome on 2007-10-24
Does anyone know how to do this for all windows, including minimized ones?

---

### Post by Onyros on 2007-10-24
I was just wondering the same, the option was there for Beryl, but I don't see it anywhere in Compiz Fusion.

---

### Post by CaptMorgan on 2007-10-25
thanks nholling and spec-chum, I wasn't getting the Action Part so I didnt get the rest.

By chance does anyone know how to make the desktops appear when I move the cursor to the upper-left corner? It was working like that until I restarted for the first time after updating to 7.10. It was pretty cool the were side by side with  reflection going. I was bummed when it wasn't working anymore and all I did was restart



dennis.groome - I didnt realize that it didnt open things that were minimzed, hmm that would be nice to know..

---

### Post by melojo on 2007-11-04
I upgraded to Gutsy and was getting ready to make a post about this option.  Thanks for the post worked for me!!!

---

