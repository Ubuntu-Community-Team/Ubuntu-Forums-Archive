---
title: "[SOLVED] Why does compiz show window on all desktops?"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by kvonb on 2007-10-31
Fresh install of Gusty, open a window, (any window or app) and it is shown on both desktops!

And I can't get rid of it.

It's usually the first thing that is opened, but is rather random.

Any fixes?

Intel 8255gm video

---

### Post by kvonb on 2007-10-31
hmm, well, it seems that it's a problem with the desktop switcher.

It doesn't change desktops, it pretends to, but stays on the same desktop!

Conclusion:  Compiz blows goats, and they have removed Beryl from the Gutsy repos!

Now to try and disable Compiz, wish me luck :(

---

### Post by kvonb on 2007-11-01
Well, seeing as I'm talking to myself, I might as well continue :).

I seem to have fixed the problem, although I'm not entirely sure how.

Here's what I did:

From the main menu, select: **System->Preferences->Appearances** and select the last tab (**Visual Effects**), then select **Full**.

Now close that and load the gnome configuration editor, it's located on the main menu under **Applications->System Tools**.  If it isn't there (as is the default setting for some obscure reason!), simply right click on the main menu (Ubuntu icon) and select **Edit Menus**, browse down to **System Tools** and select **Configuration Editor**.

Now look for **Compiz** under **Apps**, and there are a multitude of settings you can change.

I removed the rather annoying wobbly windows and the extremely annoying "sticky desktop edges" thingy. 

They are found here:

```
 /apps/compiz/general/allscreens/options/active_plugins
```Simply double click on it and remove **snap** & **wobbly** from the list.

Now to fix the desktop switching problem, go to:

```
 /apps/compiz/general/screen0/options/
```and set **hsize** to 2, and **vsize** to 1.  Make sure **number_of_desktops** is set to 1.

Now one nice feature I like is the ability to select the app you want from a graphical list of apps that are running, so to enable that goto: 

```
 /apps/compiz/plugins/scale/allscreens/options/initiate_all_edge
```and add **BottomLeft** as the initiator.  You can of course assign something different, but I like BottomLeft as I don't go there for any other reason and I won't accidentally activate it which can be rather annoying :).

The only thing I can't get is the zoom out desktop selector, where you see all desktops on a mirrored surface.  It looks rather nice and I would like to get it back, so if anyone knows how to do it please let me know.

So now apart from having no usplash (just a completely blank screen for 2 minutes on boot up!), and Firefox stalling for 60 seconds when I visit these forums, The Flatulent Monkey seems to be running quite nicely now :).

---

### Post by kvonb on 2007-11-01
Even easier solution:

Install "Advanced Desktop Effects Settings (ccsm)" from the Add/Remove tool!

Make sure you enable "All available apps", then search in "All" for **compiz**.

---

