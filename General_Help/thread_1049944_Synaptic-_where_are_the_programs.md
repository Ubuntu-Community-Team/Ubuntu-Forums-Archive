---
title: "Synaptic- where are the programs?"
date: 2009-01-25
forum: General Help
---

### Post by DJRhubarb on 2009-01-25
I am having trouble with the Synaptic Package Manager, I have installed programs, i.e. the audio mixing program TerminatorX, and I don't know where the program is. 

It tells me i has installed successfully but I can not find it, it is not where all the other programs are, and I have searched through them.

If someone can tell me where they go or are once they are installed it would be great.
Thanks

---

### Post by ibutho on 2009-01-25
Some programs maybe command line only, so if they don't show up in the menu, go to Applications -> Accessories -> Terminal and enter the name of the program and see if it runs.

---

### Post by DJRhubarb on 2009-01-25
Thanks, one program works now, just did a quick restart. But another still isn't working, and the terminal doesn't work either. This one is not installed by Synaptic, just a .deb file and it says it's installed but it's now where to be found.

---

### Post by Copernicus1234 on 2009-01-25
The deb file probably installed the program somewhere that isnt in your path. If you double click on the deb file again, you should see where it wants to install the program. Then you know where yours is.

---

### Post by mb_webguy on 2009-01-25
Double-click the deb file, then look at the included files.  (You can also find the package in Synaptic, right-click and select Properties, and click on the Installed Files tab.)  Look for a file located in /usr/bin or /usr/local/bin.  That will be the command you need to enter to start the application.

---

### Post by DJRhubarb on 2009-01-25
OK, thanks for that guys- it's working now. :D

---

