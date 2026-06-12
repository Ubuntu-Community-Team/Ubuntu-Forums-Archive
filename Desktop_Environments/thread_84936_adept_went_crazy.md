---
title: "adept went crazy"
date: 2005-11-01
forum: Desktop Environments
---

### Post by stoeptegel on 2005-11-01
I was trying to install rtorrent package with dpkg which didn't succeed. So i removed the broken package with adept, but while doing this adept went crazy and remove like 90% of my apps and stuff.

So what i want to do now is backup my /home stuff and reinstall breezy. But ionqueror, konsole all is gone...  What other therminals are there for x, cause i want to reinstall konqueror to backup my stuff.

Any advice?

---

### Post by beefsprocket on 2005-11-01
Have you tried installing kubuntu-base? It will reinstall the exact same packages that the Breezy CD comes with -- your system will be almost exactly the way it was before your dpkg madness. Give it a shot before you reformat.

---

### Post by stoeptegel on 2005-11-01
Ehm, where should i do that? I lost konsole adept and maybe apt too.(?)

---

### Post by GeneralZod on 2005-11-01
[QUOTE=stoeptegel]Ehm, where should i do that? I lost konsole adept and maybe apt too.(?)[/QUOTE]

You can always switch to a virtual terminal with CTRL+ALT+F1 (CTRL+ALT+F7 will get you back to the GUI).

---

### Post by stoeptegel on 2005-11-01
Okey i didn't knew that, thanks.
Will apps like i.e. bittornado remain running when i do this?

---

### Post by Staesys on 2005-11-01
This is one case where the "Preview Changes" button would have saved you. I've learned from experience to always click it to make sure Adept isn't going to 'rip me a new one' so to speak.

---

### Post by stoeptegel on 2005-11-01
I know and you know what, the preview showed me to remove libtorrent and one dependency package(libstdc++6), but instead it removed almost my whole system. :(

---

### Post by beefsprocket on 2005-11-01
Any results? I doubt that you've removed apt-get so you can just use it to get the meta package (kubuntu-desktop).

---

### Post by stoeptegel on 2005-11-02
Yes even apt-get is gone. :( I am booting the live-cd now, and looking for a way to get write access so i can backup my stuff. 

PS. If it helps somebody: all 3 packages came from packages.debian.org 

EDit After some irc talking i came to the conclusion that i might be guilty myself here when i installed libstdc++6 from packages.debian.org and removing it afterwards. So don't try that at home ;) 

Sorry for the negativity towards adept.

---

### Post by stoeptegel on 2005-11-02
This one is solved. I backuped my data with a live session and installed a fresh kubuntu, this was needed anyways.

---

