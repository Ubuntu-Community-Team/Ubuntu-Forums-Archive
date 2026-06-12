---
title: "Compiz's Visual Effects don't do anything"
date: 2009-02-20
forum: General Help
---

### Post by haciendadad on 2009-02-20
I am new to Ubuntu, I just installed 8.10 on my laptop (Acer Aspire 6920) and the installation went very smooth.

I wanted to show off Ubuntu's cool visual effects like the "Burn" effect/animation so I installed Compiz and did the steps shown below but once I close Compiz and I try to test the effects, nothing different happens.  Am I missing something?

These are the steps I use to enable the "Burn" animation.

o) System > Preferences > CompizConfig Settings Manager
o) Click Effects category from the left navigation
o) Click to enable Animations
o) Click Animations
o) Click to enable Burn
o) Click the Enable Animations checkbox on the left side
o) Click the Close Animations Tab
o) Select the Glide option in the Animations selection window pane
o) Click the Back button on the lower left
o) Click the Close button on the lower left
o) Open the Calculator app, then close the app.
o) No Burn effect seen

Is there a button that I missed or something to do with the profiles?

---

### Post by Therion on 2009-02-20
Compiz sees different windows as different events.  For instance, an application (Calculator) is different than say, minimizing a window; and it's controls are very, VERY granular.  Meaning you can control things down to a verrry minor degree.

If you want to show off some cool effects, try this...

Go back to the Animations plugin and open it.

You should be on the "Open Animation" tab (there should be a row of tabs across the top of your menu at this point).

Make sure all the little tic-boxes down below in the "Random Effects Pool" are ticked "On".

Click on the first animation item in the list of three that you have.  It'll say "Fade" or some such (I've changed mine and I don't recall what the defaults are).

A new "Edit" dialog box will open.

From the "Open Effect" drop-down menu, select "Random".

From the "Duration" drop-down menu in the "Edit" dialog box, change the setting from 150 to 600 using the slider or by typing in the numbers.

Go back to the top row of tabs and open the "Close Animation" tab.

Repeat the steps above for this tab...  Go to the "Open Effect" drop-down menu, select "Random" etc.
Repeat the steps above for the "Minimize Animation" tab just like you did with the first two tabs (same thing, all three tabs).

Noooow start opening, closing and minimizing and maximizing some windows and see what happens.  

If the effects are too slow for your taste's, you can decrease the effect duration (I told you to use 600) and speed up the animation.  A duration setting of 300, for example, will make them "go" twice as fast.

If you want the same animation every time you close a window or maximize a window or something, you can choose one particular animation for that action from the drop-down menu instead of using "Random" like we do here. You could choose to have the "Glide" animation display EVERY time you minimize a window for example. 

Getting the idea now?

---

### Post by haciendadad on 2009-02-20
THANKS!  My son thinks this is sooooooo coool!

---

### Post by Therion on 2009-02-20
That's because it IS cool.  ;)

Here are some bonus links to help you along:

[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

---

### Post by Derek_ on 2009-02-28
I have used Compiz for quite a while, but at some point the window animations simply didn't happen anymore, even though everything was enabled, and I experimented with various fixes to the installation and settings.

Here is what worked for me:
1. Exported my preferences profile (using the flat-file backend).
2. Made a copy of that file.
3. Reset to defaults (sets ALL Compiz preferences to defaults).
4. Exported those default preferences to another file.
5. Copied the [animation] section from the default file to replace that section in the copy of my own settings.
6. Imported the edited file.
7. Changed my animation preferences the usual way.

I know this means that my Animation preferences were botched with some unworkable settings somehow.  It would be nice if each plug-in had its own reset button.

---

