---
title: "3D Cube Desktop Not working"
date: 2015-04-20
forum: Desktop Environments
---

### Post by William_Miller on 2015-04-20
Hi. I am an average user of Ubuntu, and have successfully gotten the Compiz 3D cube effect to work on previous desktops of mine. It used to be easy. It doesn't work on my new computer. 
Asus M4N75TD motherboard, AMD Phenom II x6 1055T processor, 6GB Memory, Nvidia GTX750Ti, running 2 Asus 19" LCD monitors on DVI outputs, and 1 37" LCD TV on HDMI output. 
I am running Kubuntu 14.04, KDE Plasma desktop. Nvidia drivers are version 346.59. 
I have even tried going down to only one monitor, and I still couldn't get it to initialize the 3d Desktop. 
Any ideas? 
(I have been in and out of the Compiz settings manager for days. Unchecking and checking things based on other posts in other forums, to no avail.)

---

### Post by deadflowr on 2015-04-20
[s]3d cube[/s] 3d windows on Ubuntu/compiz has been busted for a long time.
And no one sees it being fixed anytime soon.

But if you're running Kubuntu, why are you trying to use compiz?
kwin has a functional 3d cube/3d windows already...

Just go to system settings > desktop effects.

Edit: I meant 3d windows has been busted.

In terms of setting cube, sans 3d windows, how are you trying to set it up?
Could you give a rundown of how you are setting it.
And is compiz even running?

---

### Post by William_Miller on 2015-04-26
I figured it out. Had to go to system settings and enable Open GL for compositing. All desktop effects work fine now. Thanks for the help guys.

---

