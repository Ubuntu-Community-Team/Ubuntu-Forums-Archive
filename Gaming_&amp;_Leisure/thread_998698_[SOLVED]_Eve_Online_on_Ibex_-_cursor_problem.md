---
title: "[SOLVED] Eve Online on Ibex - cursor problem"
date: 2008-12-01
forum: Gaming &amp; Leisure
---

### Post by infinitejones on 2008-12-01
I've installed Eve Online using the Linux .deb installer from the Eve website. 

I'm not running it with the Windows client on Wine or Crossover - however this problem seemed to appear at the same time as I was experimenting with that, so it might be related, but I can't work out why.

Basically, the cursor in the game has been replaced by a grid of red dots forming slanted lines. It still works and luckily most of the GUI elements react when the part of the grid that equates (I assume) to the end of the pointer pass over them, but since a lot of GUI elements are literally only a couple of pixels in size, it's a bit of a pain.

I've completely uninstalled Eve, deleted the .cedega folder in my home folder, and re-installed it from scratch by re-downloading all 800MB of it, but it's still doing it.

I'm running it on a Pavillion dv6000 with NVidia graphics, driver version 177. Eve is installed with all the default settings. It used to work absolutely fine and I can't think of anything else that's changed.

Any ideas? Thanks!

---

### Post by infinitejones on 2008-12-02
Fixed it! I'd installed the NVidia beta driver (180). I thought I'd changed back to 177 using the Hardware Drivers utility but obviously it that doesn't roll back the driver fully. 

So I fixed it by downloading 177 from the NVidia website again and re-installing.

---

