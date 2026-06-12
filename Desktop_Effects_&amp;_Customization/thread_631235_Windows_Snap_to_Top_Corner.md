---
title: "Windows Snap to Top Corner"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by Torgas Prim on 2007-12-04
I cannot seem to find any other threads on this other than a poster using Compiz.
I just have Ubuntu 7.10 installed, no frills. So I guess I am using default Gnome for the desktop environment.
When I open a window, say Firefox, it always snaps to the top-left corner. When I attempt to move it to the center(I don't like full screen apps) it snaps to the middle-top or middle-bottom. there is no in between.
If I close the window and reopen it it snaps back to the top-left corner.

I looked everywhere but cannot find where to change this behavior. Anyone run into this annoying issue too? Have you found a solution or workaround for it?

Any help is most appreciated. Thanks

---

### Post by raul_ on 2007-12-04
I can't really help you because I don't use gnome, but have you tried fiddling with gconf-editor?

---

### Post by pjones0404 on 2007-12-04
this is more than likely a setting in compiz? Do u have desktop effects installed?

try this - go to advanced desktop settings and choose the place windows plugin. there is a drop down there to select how you would like to have the windows placed. i chose centered. 

to fix the windows sticking to the sides - select the wobbly windows plugin and unselect snap inverted.

if you do not have the advanced desktop effects settings you will need to install that first.

---

### Post by Torgas Prim on 2007-12-04
I have desktop effects I noticed, so when I get home will look for advanced settings.
If I do not have the advanced settings option, how do I install it?

Also, I have not looked at the gconf editer, but will give that a try also.

Thank you all

---

### Post by Torgas Prim on 2007-12-04
I don't have Compiz, but I did finally figure it out. I just turned off the desktop effects ;-)

---

### Post by raul_ on 2007-12-04
> **Torgas Prim said:**
> I don't have Compiz, but I did finally figure it out. I just turned off the desktop effects ;-)

Desktop Effects and Compiz are pretty much the same thing :popcorn:

---

### Post by Torgas Prim on 2007-12-05
I did not know...but I am learning.
Still a n00b here

---

### Post by tehwa on 2007-12-06
[quote="Torgas Prim"]If I do not have the advanced settings option, how do I install it?[/quote]
With [Universe enabled]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories"):```
sudo apt-get install compizconfig-settings-manager
```
It can be then found in Menu > System > Preferences > Advanced Desktop Effects Settings

---

### Post by jperez on 2007-12-06
> **pjones0404 said:**
> try this - go to advanced desktop settings and choose the place windows plugin. there is a drop down there to select how you would like to have the windows placed. i chose centered.

That worked for me in KDE seeing as I already had the Advanced Settings installed.  Thanks!

Jesse~

---

