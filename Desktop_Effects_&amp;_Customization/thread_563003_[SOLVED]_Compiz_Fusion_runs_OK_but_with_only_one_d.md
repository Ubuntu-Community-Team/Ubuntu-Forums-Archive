---
title: "[SOLVED] Compiz Fusion runs OK but with only one desktop"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by staib on 2007-09-29
Hi Guys,

I've had Compiz Fusion working fine on 7.04 (and Beryl before that) but after one of the recent updates it seems to now have only one desktop - you can see Expo doing its thing but with only one desktop its a bit pointless!  Trying to recover the other three desktops I installed 'GL Desktop' but when I run this, although it opens, it does so with an error message: "An error occurred while loading or saving configuration information for gnome-compiz-preferences. Some of your config settings may not work properly...."  Under Details it then says: "Type mismatch: Expected list, got string" (x3 times).  Any suggestions? - I'm not sure what to do...

---

### Post by Forlong on 2007-09-29
You shouldn't use gnome-compiz-manager (GL Desktop) with Compiz Fusion.
Install **compizconfig-settings-manager** and then have a look at the section *Getting the cube* [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by staib on 2007-09-29
OK thanks - I have tried Compizconfig Settings Manager and in the General Options bit I can see that the Number of Desktops is already at 4.  Is there another control somewhere for the number of desktops?

---

### Post by Forlong on 2007-09-29
> **staib said:**
> I can see that the Number of Desktops is already at 4.
Yeah, and that is what's wrong. Follow the link to see how to set it correctly.

---

### Post by staib on 2007-09-29
I appreciate your guidance - and that blog guide you built - but I've read it from top to bottom, and most of the comments as well, and am either being thicker than usual or need a bit more help!

I've followed and done all this:
[B]
Getting the cube[/B]

Firstly, enable the following plugins (by checking the box next to them):

    * Desktop Cube - to actually use it, we might have to disable some other plugins (just follow the popup)

    * Rotate Cube - that is necessary to spin the cube

    * Viewport mouse switch (optional) - if you want to change desktops with the mousewheel

    * Cube Caps (optional) - lets you use an images on top and bottom of the cube

Secondly, we have to increase the number of the virtual desktops to 4
at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size
(the other two options have to be left at 1)

------

I can see the 4 'desktops' in the bottom right hand of the screen - and can click on them to go to a new desktop....

But when I launch expo (mouse top left) I only see the one desktop - rather than the four side by side I would have expected.  I suspect for the same reason the cube doesn't display or rotate either.

Watcha think?

---

### Post by Forlong on 2007-09-29
> **staib said:**
> Secondly, we have to increase the number of the virtual desktops to **4** at General **Options &#8594; Desktop Size &#8594; _Horizontal Virtual Size_**
(_the other two options_ have to be left at **1**)
Are you sure it's set like this?

---

### Post by staib on 2007-09-30
:oops::oops::oops:

OK - thanks very much Furlong!  All is now well.

I can see now that I was checking that the "Number of Desktops" was 4 and all other settings were 1.

Your instructions say:

"We have to increase the number of the virtual desktops to 4 at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size"

I would like to suggest that it might help others (who like me can't always tell the difference between a virtual PC desktop, and a virtual, virtual desktop!) to tweak the instructions slightly so they read:

"We have to increase the Horizontal Virtual Size to 4 at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size"

Thanks again for your patient help!

Nick

---

