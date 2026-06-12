---
title: "How I installed flashplugin-nonfree"
date: 2009-03-17
forum: General Help
---

### Post by BobbyS on 2009-03-17
I have seen this thread a lot about installing flashplugin and it not working. I too went through this frustrating procedure myself.

What I did was go back into Synaptic on an old installation of K 8.04 that worked fine with FireFox to see what was installed that I might need. I found out that I needed the *VERY* important Ubuntu Restricted Extras. So I installed the Restricted Extras *then *installed the flashplugin-nonfree and it works just fine. 

I am not sure about this, but I think maybe 8.10 does not load that package at install like my K 8.04 did. Who knows? All I know is this is what finally got my flash going.

Hope this helps another noob!   :lolflag:


Thanks,
BobbyS

---

### Post by LegendofTom on 2009-03-17
That is weird.  I have never used the Ubuntu extras, mostly because it seems like it would only make things muddy.

---

### Post by taurus on 2009-03-17
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubunt-restricted-extras
```
If you get stuck at java licensing screen, just press the Tab key to highlight the <OK> and Return to accept it.  

Then, restart firefox.

---

