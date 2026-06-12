---
title: "Cant run any game on Steam"
date: 2015-05-10
forum: Gaming &amp; Leisure
---

### Post by marek16 on 2015-05-10
I am using Ubuntu 14.04, installed bumblebee and steam. Everything worked fine, but now, suddently, I can not run any game.
  
Here is a copy of terminal output: [http://pastebin.com/kpbEXR0y](http://pastebin.com/kpbEXR0y)

     

What can be the problem ?

Thanks

---

### Post by efflandt on 2015-05-10
You don't say what graphics you have. If it is hybrid Intel/Nvidia you no longer need bumblebee (or optirun). The regular nvidia graphics packages (I would recommend at least nvidia-331-updates, unless you have newer graphics that need nvidia-349 from xorg-edgers ppa) use nvidia prime which can switch everything to either Nvidia or Intel from **NVIDIA X Server Settings**. Switching from Nvidia to Intel requires restarting X, I think switching from Intel to Nvidia requires rebooting. When I ran 13.10 with optirun I did not use it for launching steam, just in launch options for steam games, which required some other parameters too. But I would have to boot my laptop to see what those were. It now has 14.04 on mSATA SSD (using nvidia-331-updates), but still has 13.10 on hd partition. Although, **nomodeset** boot parameter is typically needed for desktop graphics, I specifically did NOT use that for my laptop, per another post I had read, and my laptop worked fine without that.

If you have AMD hybrid graphics, I know nothing about that.

So what graphics do you have and/or what do either or both of following report:```
lspci | grep VGA
lspci | grep 3D
```

---

