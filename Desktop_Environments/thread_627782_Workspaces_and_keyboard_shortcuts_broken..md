---
title: "Workspaces and keyboard shortcuts broken."
date: 2007-11-30
forum: Desktop Environments
---

### Post by PinkFloyd102489 on 2007-11-30
Ive been playing around with Compiz for a few days and somethings have recently broken. I enabled the Trevino repo earlier and it installed some upgrades to Compiz. First of all, the Advanced Desktop Effects Settings refused to load. Then I noticed that my Ctrl+Alt+Shift+T to launch a terminal stopped working. THEN I saw that I now only have 2 workspaces instead of 4. The Workspaces Preference window reports that 4 are enabled but only 2 show and the Desktop Cube Rotation reflects this.

Any chance for a quick fix?

---

### Post by PinkFloyd102489 on 2007-12-01
Ok I got the keyboard shortcut working. I had to add the shortcut into Compiz itself. Yet my workspaces are still broken.

I did a "metacity --replace", which fixed my workspaces but it also disabled Compiz entirely. When I re-enabled Compiz, my workspaces broke again.


I dont know how relevant it is to my current problem, but I had Emerald installed also. I didnt like how it handled my windows, especially the lack of pleasing themes for it. I removed emerald and it defaulted back to Metacity, so I assume.


Maybe this is part of my problem?

---

### Post by erginemr on 2007-12-01
Hello,

Apparently there occurred a conflict in different parts of the compiz system after you have enabled Trevino's repositories. If I were you, I would remove all compiz related packages from synaptic, disble any third party repositories for compiz, remove the config directory in my home drive (~/.config/compiz -> be careful though, you should delete just the compiz directory inside the ~/.config directory, other files and directories therein are essential) and reinstall compiz from synaptic.

To give you an idea on what to install, I have attached the list of installed compiz related packages on my system. Do not pay attention to the libraries, they should install by themselves as part of the dependency tree.

You may also consider reading the following thread:

[http://ubuntuforums.org/showthread.php?t=628461](http://ubuntuforums.org/showthread.php?t=628461)

Good Luck...

---

