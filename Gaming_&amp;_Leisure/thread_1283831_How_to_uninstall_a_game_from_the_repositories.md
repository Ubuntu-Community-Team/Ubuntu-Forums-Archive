---
title: "How to uninstall a game from the repositories?"
date: 2009-10-05
forum: Gaming &amp; Leisure
---

### Post by ErikEhlert on 2009-10-05
I currently went through KPackageKit and installed a couple of games I thought I would be interested in, not to my surprise, they are horrible games (poorly constructed at that too). How exactly do I uninstall them? They only appear when I go to applications > games. If I right click on their icons there is no option to delete. Are they saved in a certain folder? They just spam up my games section :l

---

### Post by beastrace91 on 2009-10-06
If you open your kpackage kit you should be able to find the packages you installed and remove them from there.

Or if you know their exact package names remove them via terminal by running ```
sudo apt-get remove packagename
```

~Jeff

---

### Post by oldrocker99 on 2009-10-06
Or, you can use Synaptic, search for the program, and select "Completely Remove," and it'll do the rest.

:guitar:

---

### Post by ErikEhlert on 2009-10-06
Nah, KPackage did it for me. It helped a lot. Okay, well.. [solved]

---

