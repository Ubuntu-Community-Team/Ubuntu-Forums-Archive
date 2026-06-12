---
title: "Adjust default window positions to center on screen"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by oldsmobile_mike on 2008-01-22
Hi!

I have several applications (web browser, etc.) that I want to have start, by default, centered on the screen (instead of sticky to the top/left side of the screen), but no matter how many times I correctly adjust the window to where I want it, each time I quit the app and restart it, it comes back stuck to the left edge and top of the screen.  If I even use the "move to another workspace" option, it moves to the other workspace, but again, is stuck to the top of the screen.  I've tried checking in the Windows and Appearance preferences settings, but couldn't find anything about this.  Suggestions?

Thanks!

---

### Post by chewearn on 2008-01-22
You can use this:
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by Xgen on 2008-01-22
If you're using Compiz or Beryl, it's in the  custom settings under Windows Management-->Place WIndows-->Placement Mode...centered is one of the choices.

---

### Post by oldsmobile_mike on 2008-01-22
> **AstalaVista said:**
> You can use this:
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

I was not able to get this to work.  I installed the latest version, and set up the file Opera.ds (for the Opera web browser) in /mike/.devilspie

(if (is (application_name) "opera")
   (begin
   (geometry "1314x914+50+50")
   )
)

But when I ran devilspie, then started Opera, the window showed up in the exact same place - stuck to the top-left edge of the screen.

Any suggestions?

Thanks!

---

### Post by oldsmobile_mike on 2008-01-22
> **Xgen said:**
> If you're using Compiz or Beryl, it's in the  custom settings under Windows Management-->Place WIndows-->Placement Mode...centered is one of the choices.


I downloaded Compiz from here:  [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

...wow, that's a complicated program.  Any idea how to set up fixed window placement?  Other than that, it seems to work okay...  um, where can I find instructions for it?  Haha!  ;-)

Great, thanks!

---

### Post by Xgen on 2008-01-22
Compiz was probably already installed by default...just not enabled. If you're using Gnome, then open Synaptic and install the 'Compiz configuration settings manager' or search for 'Compiz' to see all the packages associated with it. Start Menu-->System-->Preferences-->Appearance-->Visual Effects will give you options and Custom-->Preferences will then overwhelm you with the choices...

---

### Post by oldsmobile_mike on 2008-01-22
> **Xgen said:**
> Compiz was probably already installed by default...just not enabled. If you're using Gnome, then open Synaptic and install the 'Compiz configuration settings manager' or search for 'Compiz' to see all the packages associated with it. Start Menu-->System-->Preferences-->Appearance-->Visual Effects will give you options and Custom-->Preferences will then overwhelm you with the choices...

That is correct - I got it working at about 4:00am, and I was completely overwhelmed with choices!  :-)  Only thing I couldn't figure out was the "cube", which I've seen on various Ubuntu screenshots and youtube videos in the past.  I think it says something like [ctrl] + [alt] + [down] to enable it, but that key combination does nothing, even though I have all the boxes labled as anything to do with "cube effects" marked as enabled.  What key combination do you press to get the cube to appear?

Wohoo, this is almost as much customization as I had on my old Amiga, lol!  :-)

---

### Post by rmcder on 2008-01-22
CNTL-ALT-LEFT MOUSE BUTTON.  Hold down and move mouse to manipulate the cube.

---

