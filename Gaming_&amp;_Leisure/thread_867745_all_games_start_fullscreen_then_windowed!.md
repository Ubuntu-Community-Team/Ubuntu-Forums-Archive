---
title: "all games start fullscreen then windowed?!"
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by ELD on 2008-07-23
Hi all no matter what game i play they always seem to go back windowed and half the time i lose the ability to use my house

it is highly frustrating!

---

### Post by Noriv on 2008-07-23
Try turning the screensaver off.

---

### Post by ELD on 2008-07-23
It won't be that, games get windowed straight away :(

---

### Post by king.pest on 2008-07-23
did you try turning compiz off? I remember having some issues with fullscreen games with compiz on.

---

### Post by Lovok on 2008-07-23
> **king.pest said:**
> did you try turning compiz off? I remember having some issues with fullscreen games with compiz on.

Same thing happened to me. There's a code that's like "compiz --replace" or something that turns it off.. or you replace it with metacafe..
Hope that gives you leads ;p

---

### Post by king.pest on 2008-07-23
> **Lovok said:**
> There's a code that's like "compiz --replace" or something that turns it off.. or you replace it with metacafe..

I think it's rather "metacity", and the code is like "metacity --replace". If you're running GNOME/Ubuntu, then just right click on your desktop, go to appearance settings and turn off "effects" in the last tab.

---

### Post by KrazyKain on 2008-07-25
> **ELD said:**
> Hi all no matter what game i play they always seem to go back windowed and half the time i lose the ability to use my house

it is highly frustrating!

I had that problem too, just turn all the special effects off for ubuntu.

---

### Post by ELD on 2008-07-25
Turning off effects fixed it, how annoying, is there a way around it?

---

### Post by Lovok on 2008-07-25
[http://ubuntuforums.org/showthread.php?p=5440138](http://ubuntuforums.org/showthread.php?p=5440138)

This person made a script to automate the process of switching between metacity and compiz.

---

### Post by RIchard James13 on 2008-07-25
I got rid of Compiz all together because of this problem. However I could not just turn the effects off. I had to change my ~/.gnomerc file from
```
export WINDOW_MANAGER=/usr/bin/compiz

```
to
```
export WINDOW_MANAGER=/usr/bin/metacity
```
That makes metcity the default Window Manager when Gnome loads. Plus I removed all the Compiz packages using synaptic.

---

### Post by Primistry on 2008-07-26
just do a search.

---

