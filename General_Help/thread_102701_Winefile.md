---
title: "Winefile?"
date: 2005-12-12
forum: General Help
---

### Post by Redeyes_Gambit on 2005-12-12
}{i, I'm a pretty fresh Ubuntu user and am trying to get a winblows emulator to work on my system. 

I downloaded Wine via synaptec and on Wine's official site they said that it has a "Explorer-like graphical Wine environment" and then proceded to say that winefile (the GUI) "comes with Wine and can be found with the other Wine programs. It is a useful way to view your drive configuration and locate files, plus you can execute programs directly from Winefile". 

Lol again I'm a pretty new to all this and have no idea where this particular program can be found along with "the other Wine programs". I'd realy like to be able to use the GUI, at least at first.

Can somebody lend me a hand on how to find and run this "winefile" gizmo? Thnx!

---

### Post by BigMurph on 2005-12-13
I would hazard a guess that the version of wine in the repos is not the same as the latest version on the wine site. I do believe the latest wine (0.9.3) was only released yesterday. I use wine 0.9.2 and I have winefile on mine. I suggest you uninstall the repository version and get a newer version on SourceForge. I got the Fedora Core .rpm file and used alien to make a .deb and installed like that, and it seemed to work perfectly.

Go to [http://sourceforge.net/projects/wine](http://sourceforge.net/projects/wine), click download wine, and download the file wine-0.9.2-1fc4winehq.i686.rpm (or whatever platform you need). 

Make sure you have alien installed (sudo apt-get install alien). 
Then sudo alien wine-0.9.2-1fc4winehq.i686.rpm
Then sudo dpkg -i wine_0.9.2.deb (or whatever the created deb file is called)
This should give you the (2nd) latest version of wine.

---

### Post by Redeyes_Gambit on 2005-12-13
I thought Synaptec kept it up to date though? I got a wine update not that long ago (can't remember if it was day before yesterday or a little before, point is not long ago). I just need to know where to go to FIND the winefile gizmo, and how to execute it. Lol, again, n00b here. And even if I don't have the latest wine and follow your advice and get the newest from the site (which of course you might be right and I'll have to do that anyway) how do I find/execute it AFTER I get it?

Thanks for taking the time to reply by the way :D

---

### Post by kaamos on 2005-12-13
If you really have the newest wine, the open a terminal and type: winefile

---

### Post by Redeyes_Gambit on 2005-12-13
*smacks head* I can't believe it was that easy!

---

