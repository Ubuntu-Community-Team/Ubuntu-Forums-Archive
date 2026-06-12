---
title: "Windows out of view after screen lock and unlock"
date: 2020-11-23
forum: Desktop Environments
---

### Post by sergiuhlihor on 2020-11-23
I have a dual 4K setup (Dell 2715Q) driven over display port by a system with Geforce 960 graphics card, Ryzen 3970X CPU and 128GB RAM. I am running my displays with 200% scaling, no fractional scaling at all.
From first installation of Ubuntu 18.04, a weird behavior started to appear: occasionally after screen lock and unlock, the file manager did not display all the items from a folder. It looked like somehow it was displaying the items in an invisible yet stretched over two screens version. The workaround for the artefact was always to doubleclick on the filemanager top selection, to make it display everything in a window then maximize again. 

Recently (cannot say exactly if one or two months), after some update, the issue started to also manifest in Firefox. Here again behaved like the rendered image is only half of the screen and again the workaround is the same, minimize and maximize the browser. I have therefore assumed an update went wrong and decided to take the opportunity to reinstall a clean Ubuntu 20.04. However to my surprise, the issue manifests on a clean installation and even worse, this is now affecting also the terminal, workaround being the same. And now the issue is consistently reproducible after every screen lock. 

The issue disappears if I use the screens at their native resolution with no scaling. With fractional scaling enabled, even weirder things happened (to an extend where it looks completely broken) and with half resolution, the visualization is horrible. 

Anyone has any idea of what I could try (other that complete different Desktop environments) ? 

Also, any suggestions for making the system feel snappier are welcome.  The environment feels slower than a standard Windows XP running on Thinkpad T60 laptop and this feels wrong when looking at the amount of resources available.  I have disabled animations and this helps to some extend but not the same feeling of speed as on Ubuntu 18.04. I am using Nvidia driver and when it comes to CPU, it runs with CPU governor on performance all the time.

---

