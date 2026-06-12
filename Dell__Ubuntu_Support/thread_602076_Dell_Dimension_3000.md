---
title: "Dell Dimension 3000"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by Frostshocker on 2007-11-03
Couldnt find anything exactly the same as this so here it goes:

I have a Dell Dimension 3000 (bought this a while ago) and i seem to be having some trouble with the live CD.

I insert it, it loads up all the way boots up GNOME etc. then my screen goes blank after about 10 seconds a little box comes up saying something like "Your monitor and video card could not be detected correctly please select your drivers" (something like this).

Anyway i chose the drivers and click ok and then my screen returns to the lines of code where it boots up gnome i left it there for a while and it does nothing.

Since it said something about graphics i restarted and loaded it up in "safe graphics mode" (again the exact spelling might be wrong) so i let it load up it, seems to load up perfectly fine until GNOME boots up and shows the login screen asking for a username and password (i 
have no idea why)

After all of this i kinda guessed what the problem was (dell has a internal graphics chip and i installed a PCI nvidia FX5200, the problem is in my dells bios for the intergrated stuff theres only the options "Internal" or "Auto" and as such i cant turn it completely off but it works in windows)

but instead of having to open the computer im looking for a workaround maybe and also a little advice so here it goes


Is there a way i can use the live CD without opening up the computer and removing the card so test it out? and if not when i install it to my hardrive using the alternative CD will it work?


Sorry for this wall of text and the poor spelling within this wall but i really hope you can help :)

:grin: Peace Frosty :grin:

Edit:Forgot to mention im a first time linux user the only other linux i used was a knoppix live CD which worked perfectly fine with this card

---

### Post by Frostshocker on 2007-11-04
Anyone? :<

---

### Post by Frostshocker on 2007-11-05
Bumping this for the last time in hope of a answer :)


:-({|= :-({|= :-({|=

---

### Post by Nzer24 on 2007-12-12
Can you get to a command line of some sort? (doesn't need to be in GNOME) That might let you change the graphics drivers to something generic so you can get some basic output.

Just in case I don't get back, here's what to do:

(as root)

cd /etc/X11
nano xorg.conf

change the thing in quotes after the tag "driver" somewhere in the document within the graphics card section to "vesa". (make sure it's in the right section)

startx

That might do it... hope it helps!

---

