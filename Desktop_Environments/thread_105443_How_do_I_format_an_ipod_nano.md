---
title: "How do I format an ipod nano?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Pedricko on 2005-12-18
Hey guys (and girls),

I need to format my ipod nano without using windows.

With all the music off it, it registers as having 836MB of free space so this cant be right, how can I format to a clean slate like how it came out of the box (I think my messing around added crap to it).

---

### Post by aysiu on 2005-12-18
The best way to reformat it so that it's still functional is to reload the iPod software that came with it on to it. You'll be warned that it'll totally erase the iPod's data--that's fine.

Unfortunately, that iPod software is made for either Windows or Mac, not Linux. The Windows version may run under Wine. You can try it. Do you have Wine installed?

---

### Post by Pedricko on 2005-12-18
Hmm... I'll have a looksee about installing WINE, any other options?

---

### Post by aysiu on 2005-12-18
Well, the thing is, you can wipe the hard drive clean by deleting songs. If you reformat, it won't have the software needed to play the songs. If you want to install Wine, follow the instructions in the first link of my sig. Then open up a terminal and ```
sudo apt-get update
sudo apt-get install wine
``` Then double-click the .exe for installing the iPod Nano firmware... it may or may not work with Wine.

---

