---
title: "Flashblock is not installing nor unistalling."
date: 2009-03-26
forum: General Help
---

### Post by dragos240 on 2009-03-26
Hello, i just received an update that told me i should update to the latest version of flashblock, i did and now flash doesn't work, AND when i try to cancel it, it tells me to restart firefox, i did, and it's still there saying to restart firefox, even though i did 5 times. Help?

---

### Post by Rallg on 2009-03-26
I have 8.10 and just updated Flashblock. No problem.

I believe that Firefox has a configuration file that tells it which add-ons are installed. If an add-on is not actually installed (or updated properly) the configuration file may nevertheless claim that the add-on is there.

How did you originally install Flashblock? Via Synaptic Package Manager, or via Firefox add-ons window? First, open Synaptic, and see if it thinks Adblock is installed. I installed from within Firefox, so my own Synaptic does not think that Adblock is installed.

If you cannuse use Firefox at all due to an endless loop, you might try using Synaptic to fix the problem, since FF does not need to be open while Synaptic works.

Since you evidently have Internet access, you can also try to find out where Firefox is storing the info that it has Adblock. Alas, FF uses a rather odd file system to store its stuff, and I imagine that it is worse in Linux than in Windows.

---

