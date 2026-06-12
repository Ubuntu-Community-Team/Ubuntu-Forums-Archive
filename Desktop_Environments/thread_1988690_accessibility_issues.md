---
title: "accessibility issues"
date: 2012-05-28
forum: Desktop Environments
---

### Post by forestlake on 2012-05-28
just a thought with the scroll bars in Ubuntu 12.04... have people's accessibility issues/needs been taken into account?

these scroll bars can be small to focus the mouse on, and once focussed need to be dragged to scroll down the page... previously you could position your mouse in the scroll bar and simply click to scroll a page at a time... dragging is especially painful when looking at a 250 page document for example while dragging as you sometimes are unable to maintain a constant speed while dragging, especially if you motor skills are not as good as the rest of the population... even using the scroll wheel can be problematic for some users...

hope this can be looked at and given some consideration

cheers,
Forest

---

### Post by wilee-nilee on 2012-05-28
You can disable the new scrollbar setup take a look on the web if you would like to do this or someone will probably get you a link. ;)

Here is one lok carefully.
[http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars)

---

### Post by vasa1 on 2012-05-28
> **forestlake said:**
> just a thought with the scroll bars in Ubuntu 12.04... have people's accessibility issues/needs been taken into account?

these scroll bars can be small to focus the mouse on, and once focussed need to be dragged to scroll down the page... previously you could position your mouse in the scroll bar and simply click to scroll a page at a time... dragging is especially painful when looking at a 250 page document for example while dragging as you sometimes are unable to maintain a constant speed while dragging, especially if you motor skills are not as good as the rest of the population... even using the scroll wheel can be problematic for some users...

hope this can be looked at and given some consideration

cheers,
Forest
I think if you spend some time with the overlay scrollbars, you'll find them quite nice. It's a pity there's not a nice video on how to use them but you don't have to drag at all. Once the little box appears, just keep your mouse pointer over the up or down arrow and click for a page up/down.

---

### Post by forestlake on 2012-05-28
> **wilee-nilee said:**
> You can disable the new scrollbar setup take a look on the web if you would like to do this or someone will probably get you a link. ;)

Here is one lok carefully.
[http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars)

hey thanks Wilee-Nilee, i didn't know you could disbale them :} i shall check it out! thanks ):P

---

### Post by forestlake on 2012-05-28
> **vasa1 said:**
> I think if you spend some time with the overlay scrollbars, you'll find them quite nice. It's a pity there's not a nice video on how to use them but you don't have to drag at all. Once the little box appears, just keep your mouse pointer over the up or down arrow and click for a page up/down.

personally they aren't that much of an issue **until** i had to read a pdf with over 250 pages, then it was a real drag! 

i had no clue about clicking the arrows on the scroll "box", that is a neat tip ;) thanks for replying hey!

i did notice just before when using the super key to bring up the launcher there is no scroll box/button there and it did take me a few goes to get the mouse to select the scroll bar... i shall try to disable it and see how i go

thanks again

---

### Post by forestlake on 2012-05-28
ok, now that i am aware you can actually disable the overlay scroll bars i have actually found this, which is dead basic :D

"For disabling Overlay Scrollbars in Ubuntu Precise, get to a Terminal and run:

gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false

You would need to re-login for the change to take effect.

Later, if you want to revert to using the Overlay Scrollbars, run:

gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars true

Again, you would need to re-login for the change to take effect."

this was taken from the Tux Garage site - [http://www.tuxgarage.com/2012/05/disable-overlay-scrollbars-in-precise.html](http://www.tuxgarage.com/2012/05/disable-overlay-scrollbars-in-precise.html)

---

### Post by vasa1 on 2012-05-28
> **forestlake said:**
> personally they aren't that much of an issue **until** i had to read a pdf with over 250 pages, then it was a real drag! 

i had no clue about clicking the arrows on the scroll "box", that is a neat tip ;) thanks for replying hey!

i did notice just before when using the super key to bring up the launcher there is no scroll box/button there and it did take me a few goes to get the mouse to select the scroll bar... i shall try to disable it and see how i go

thanks again
You're welcome! It's just that I too got swept away by the negativity and didn't give it a fair chance in 11.04 and 11.10.

To be fair, some improvements have been made but I didn't follow things closely. Anyway, come 12.04 and I forced myself to try and found it quite convenient, not just for long files but even in the file manager and elsewhere.

---

### Post by forestlake on 2012-05-28
> **vasa1 said:**
> You're welcome! It's just that I too got swept away by the negativity and didn't give it a fair chance in 11.04 and 11.10.

To be fair, some improvements have been made but I didn't follow things closely. Anyway, come 12.04 and I forced myself to try and found it quite convenient, not just for long files but even in the file manager and elsewhere.

i am like you and have been using it since 11.04 also, it just never really annoyed me until the big pdf file i had to read ;p 

now i know you can click the arrows on the scroll button that should help also ;)

---

### Post by vasa1 on 2012-05-28
Talking of accessibility, if you want to enhance the contrast between thumb and background in the conventional scrollbars, the Gnome Color Chooser should still work for gtk-2.0 apps. If you want to do the same for gtk-3.0 apps, do mention. I have to dig out the link.

Got it:
The fix for that was pointed out by [ked]("http://ubuntuforums.org/showthread.php?t=1868005").

---

### Post by forestlake on 2012-05-28
> **vasa1 said:**
> Talking of accessibility, if you want to enhance the contrast between thumb and background in the conventional scrollbars, the Gnome Color Chooser should still work for gtk-2.0 apps. If you want to do the same for gtk-3.0 apps, do mention. I have to dig out the link.

Got it:
The fix for that was pointed out by [ked]("http://ubuntuforums.org/showthread.php?t=1868005").

i'll take a look, not really an issue for me but worth knowing all the same ;)

---

### Post by MarjaE on 2012-06-22
I don't think these issues have been addressed.

For example, the mouse-over scrollbars, the dock, and mouse-over features in general create ergonomic trouble, and given the latency, can be ergonomic nightmares. Even after disabling the mouse-over scrollbars, the normal width of the scrollbars is too narrow. I think the reasoning was that people can use trackpad scroll and/or scrollwheels, but trackpad scrolling requires really good hand-eye coordination, and scrollwheels cause tendon issues.

For another example, Unity is supposed to use an alt-tab key combination to switch between windows. Gnome 2 made it easy to use the bottom panel to switch between windows. alt-tab is convenient if you can type two-handed or can type left-handed, but it's really awkward if you can only type right-handed. I have coordination issues and can't type two-handed. A few years ago I was hit while crossing the street and had my good arm in a sling.

You know what? Making Ubuntu *usable* for people with injuries and/or disabilities will tend to make it easier to use for those who don't. I'm surprised, and angry, that this has not been a priority. And those design decisions show that it hasn't been a priority.

---

### Post by forestlake on 2012-06-23
i personally don't think this has been addressed either... these things should be built in to the system as standard!

the whole problem with Ubuntu is that it is full of geeks who think the command line is the be all and end all of computing... problem is the world is much larger and if Ubuntu wants to be used world wide it needs to take these things into account...

i truely believe these things need to be built into the GUI and not force people into using the terminal...

MarjaE, i do know how you feel as i have had shoulder surgery on one shoulder and waiting for it on the second shoulder, so i also find it hard at times as a lot of Ubuntu is about keyboard shortcuts or a combination between the mouse and keyboard WHICH I REALLY DONT LIKE !

---

### Post by vasa1 on 2012-06-23
> **MarjaE said:**
> ... Even after disabling the mouse-over scrollbars, the normal width of the scrollbars is too narrow. ...
Do you want to know how to increase "the normal width of the scrollbars"?

---

### Post by forestlake on 2012-06-23
> **vasa1 said:**
> Do you want to know how to increase "the normal width of the scrollbars"?

the problems isn't necessarily the width, the problem for a lot of people IS the scroll bars

i would like to see an option **in the GUI** to enable the old style scroll bars, that way people with poor motor skills do not HAVE to hit a certain spot in the scroll bar to then be able to drag it around, they can click anywhere in the scroll bar to then move up or down one page at a time

---

### Post by vasa1 on 2012-06-23
> **forestlake said:**
> the problems isn't necessarily the width, the problem for a lot of people IS the scroll bars
...
Well, I was asking about the other poster's issue based on my understanding of "Even after disabling the mouse-over scrollbars, the normal width of the scrollbars is too narrow."

---

### Post by forestlake on 2012-06-23
> **vasa1 said:**
> Well, I was asking about the other poster's issue based on my understanding of "Even after disabling the mouse-over scrollbars, the normal width of the scrollbars is too narrow."

yep, totally understand what both of you are saying about them being narrow, i agree also (and have trouble with them to)... i just believe the option for the old style should have been put in/left in the UI ;)

---

### Post by forestlake on 2012-06-23
lol, just ran into trouble then....

went into Dash Home using the super key, then to Applications, then selected "installed applications" to bring up the expanded list of installed apps... i can either scroll down to see them all or click on the "scroll bar" then drag it, which i did... it took me **four attempts before i could do it** !!! i even had the very point of the mouse over the scroll bar and it would not recognised the mouse properly so what chance to people with motor skill problems have ?!?!

---

### Post by vasa1 on 2012-06-23
For gtk-2.0 programs, the conventional scrollbar width can be increased via GUI using GNOME Color Chooser (from USC).

---

### Post by MarjaE on 2012-06-23
> **vasa1 said:**
> Do you want to know how to increase "the normal width of the scrollbars"?

I already found a fix. I should probably mention that I'm using 11.04 and this reflects my experiences with the switch from 10.10 to 11.04 rather than anything specific to 12.04. I actually reinstalled 10.10 at one point, but 11.04 supports a patch for the touchpad so it doesn't go haywire any more.

---

### Post by Linuxratty on 2012-07-07
> **vasa1 said:**
> I think if you spend some time with the overlay scrollbars, you'll find them quite nice. 

Not if you have poor vision,which could be op's problem.

---

### Post by vasa1 on 2012-07-07
> **Linuxratty said:**
> Not if you have poor vision,which could be op's problem.
In that case the exact nature of requirement should be clearly stated :) . I'm not sure it was.

Edit: to be fair, the OP did mention "motor skills".

---

### Post by vasa1 on 2012-07-07
Anyway, I'm out of this thread since there's nothing positive I can offer.

---

### Post by forestlake on 2012-07-07
yeah it's a motor skill issue ;p

---

### Post by MarjaE on 2012-07-15
I also have motor skill issues, in addition to arm injuries. I can't use a touchpad or touchscreen for anything fancy like 'tapping,' can't use a stylus because most are too small for the kind of grips I can form, can't type two-handed, etc. It's frustrating and I'd like to see people take our needs into consideration.

---

