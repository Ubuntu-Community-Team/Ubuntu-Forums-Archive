---
title: "FVWM95 in ubuntu 11.10"
date: 2011-12-26
forum: Desktop Environments
---

### Post by Fxy on 2011-12-26
Ok so i'm trying to install [FVWM95]("http://fvwm95.sourceforge.net/") on a ubuntu 11.10 installation, running the gnome fallback-classic environment.  I have compiled all the necessary files, but i seem to have got stuck at the last part !!  I'm told that i now need to modify my ".xinitrc" or ".xsession" in order to start [FVWM95]("http://fvwm95.sourceforge.net/").  I have tried using google to try find out how to edit either of these files, but i cant seem to find them on my system :?  Any help would be much appreciated :)



Fxy...

---

### Post by Tomrade on 2011-12-26
the .xsession file is in your home dirctory you may have to create it as its normally used for the default x session for example with XDM not sure what you need to do with GDM or LightDM but for my openbox only machines I have 'exec openbox-session' in my .xession file (with XDM)

---

### Post by Fxy on 2011-12-26
> **Tomrade said:**
> the .xsession file is in your home dirctory you may have to create it as its normally used for the default x session for example with XDM not sure what you need to do with GDM or LightDM but for my openbox only machines I have 'exec openbox-session' in my .xession file (with XDM)

So do i just create a new document and save it as .xsession or would i already have one saved as a hidden file :?  The help file i have been going by tells me the single line i need to add to the file, so if i add it & save should that be it once i reboot :?


Thanks for the reply btw...

...Fxy

---

### Post by Tomrade on 2011-12-26
Yes you need to make a new one so for example running 'nano .xsession' in your home directory would open it or create a new one if you don't have one yet then add the line and save it. you can use whatever text editor you like. However I think it is designed for systems either using startx or XDM from back in the day so thats why it said add as normally then you had other stuff in there but less now.

 if you are using GDM , LightDM or KDM to start your session then you might need to do something else as well to get it to start but it may just work . 

Ar your trying to have a fvwm desktop? or replace metacity in gnome fallback?

---

### Post by Myrddin Emrys on 2011-12-26
Just curious - why fvwm95? It's an old unmaintained hack of an ancient  version of fvwm. More recent versions of fvwm can be made to look much  the same way using themes. Or fvwm-crystal (packaged for Ubuntu) can easily be  configured in a similar fashion (try the 'Nebulae' recipe under preferences,  the 'MS Windows' button model under window decorations, and the  'Industrial' colorset).

---

### Post by Fxy on 2011-12-27
Ok so now even though i compiled "fvwm85" i just dud "sudo apt-get install fvwm" & it has worked a treat :)  Only question i have remaining now is how do i get it to load the taskbar at the bottom upon every login & how do i remove the borders around it :?

Yes the computer has to look like windows classic/2000/98/95 & thats whay i went for fvwm95 !!

Thanks for all the reply, have been much help ;)



Fxy...

---

