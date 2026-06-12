---
title: "Messed up themes completely"
date: 2013-01-17
forum: Desktop Environments
---

### Post by -AB- on 2013-01-17
Hi folks,

long time no see, but now I need your help again.

I use Ubuntu 12.04 for a while now and managed to make it work decently for me.

Three hours ago, I showed a friend the path to the themes selection screen, opened it myself and - bam - my theme was reset and I can't reconfigure it anymore.

I've added some pictures of how it looks now and how I remember it was before.

browser.png - before, the menu bar definitely was gray, as the menu below. Also, the address bar was white background (orange when https) with black text.

full.jpg - nautilus address bar was gray, not kind-of-black. The left tab's background was white. Also, on this picture you can see that the gnome-panels are kind of messed up. They have an assigned, semi-transparent background image, which they don't show. Highlights in the workspace selector used to be blue-ish. Also, selected folders appear now orange instead of blue. The window is maximized, before, I had a close-button that extended right up into the corner, so you could move the cursor into the corner and click. Right now, I have to move it into the corner, and then aim for the tiny close button to close the window.

menu.png - the menu was light gray before, with black text and blue highlights.

textselection.png - selected text should be highlighted blue, not orange. Plus, also here, the menu bar is black and used to be gray.


One thing I forgot: before, I had "oldschool" scrollbars, these are too narrow, plus the contrast (light gray/very light gray) is too low.



What theme do I need to install to revert everything back to normal? When I opened the System Settings tab, no theme was available in the dropdown (grayed out) - since then I reinstalled light-themes and different other themes, but I have no clue of how to get my old beloved desktop back. Though it is all buggy and ugly in Gnome3, I still don't want to lose 6 months of effort and revert back to my old Gnome2 installation.

Plese? Help? Somebody?

---

### Post by Frogs Hair on 2013-01-18
Have you installed the Gnome Tweak Tool and checked under themes and do you have any ambiance variants installed ?

Nautilus is partially used when drawing the desktop so you may want to restart with the following. ```
nautilus -q
```

---

