---
title: "Gnome-dock, please help installing cairo!!"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by olavjunior on 2007-05-08
I followed this thread : [HTML]http://ubuntuforums.org/showthread.php?t=302570&page=1&highlight=cairo+dock+feisty[/HTML]

I get this error when I try to configure cairo :

[I]configure: error: Cairo requires at least one font backend.
Please install freetype and fontconfig, then try again:
[http://freetype.org/](http://freetype.org/) [http://fontconfig.org/](http://fontconfig.org/)[/I]

I'm using feisty, and didn't have any problems configureing it under edgy. I installed the freetype trough synaptics, didn't help. Isn't it posible to get cairo trough synaptics??

(I used synaptics, didn't help. Compiled succsessfully from source, but still the same error)

EDIT: I got to install cairo-1.2.6 by installing the developement-files for libcairo2 in Synaptic. 
But still, when I try to make cairo-dock I get ALOT of errors!  

Anyone got an idea why?

---

### Post by FuturePilot on 2007-05-08
Have you tried ```
sudo apt-get install cairo-clock
```

---

### Post by olavjunior on 2007-05-08
Yes, I've got the cair-clock working perfectly. But it's the Cairo-DOCK I can't get to work. Maby that wasn't clear, I'm sorry..

---

