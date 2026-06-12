---
title: "Icon Issues in new Jaunty Install with Twinview"
date: 2009-04-25
forum: General Help
---

### Post by MellowVids on 2009-04-25
I have everything almost perfect with my installation.  Twinview is working fine.  

The only problem is that both screens' desktops are set to "folder view," and they are both showing the same icons.  I want the icons to show up just **once** over both screens.  Meaning I would like to be able to have half of my desktop icons on one screen and half on the other screen.  

How might I be able to do that?

---

### Post by dtoronto on 2009-04-25
What video drivers you are using?

---

### Post by Peter09 on 2009-04-25
If you have an nvidia card then install nvidia-settings. (due to a bug you will need to run it with sudo).

There are two options one allows you to have two desktops, one for each terminal (which I think is the one you have) the other allows you to have one desktop spread across both terminals (which I think is the one you want).

Sorry, as I am not at my dual monitor machine at the moment I cannot give you more detail.

---

### Post by MellowVids on 2009-04-25
I have a nvidia Quadro NVS with the version 180 driver.  I already have nvidia-settings, that is how I configured Twinview.

---

### Post by Peter09 on 2009-04-25
OK, from your comments twinview is not what you want. Just unset twin view and you should then get a big desktop which will occupy both screens. Your Gnome panels should just use the Primary screen.

---

### Post by MellowVids on 2009-04-25
Well, I can't get both screens to work how I want them without Twinview.  I want to be able to move windows from one screen to the other, and to be able to move icons from one screen to the other.  It seems like Twinview should do that (as long as they aren't set to be clones).  

I tried using separate x screens with xinerama, but that does the same thing as twinview.

Let me restate the problem to be clear.  I have both screens set up, and I want them both to be in "folder view," as opposed to the "Default Desktop Containment."  Both screens' Folder View settings are configured to display the desktop folder.  The problem is that they both are displaying all items in the desktop folder.  

I had Hardy set up with Twinview, almost exactly like my current setup except that Hardy does not have the different options of Folder View vs. Desktop Containment.

Oh, and bump...

---

