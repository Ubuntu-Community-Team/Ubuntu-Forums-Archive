---
title: "[SOLVED] Problems with Warcraft 3"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by goffy59 on 2007-09-03
Well, first Id like to thank everyone for their amazing tutorials that have helped me a lot on here. I did look around for help with warcraft 3. I used the help to install warcraft + tft. Its installed and running fine; except for the fact its very slow and choppy(unplayable).
I did enable open gl support with my game, but it still runs slow and choppy. Which leads me to think my 3d acceleration is not enabled or configured properly. I'm not sure if I have the right nvidia driver, I left it alone because last time I tried to update by shutting down x server and then running the .run from nvidia, it kept saying x server was open. Then I tried xorg config(Not sure exactly). Follow the instructions, tried to configure it; eventually I restarted, and then Ubuntu wouldn't start up because the GUI had a config file problem. So I reinstalled. I'm very scared of trying this again(installing the nvidia driver), without having some sort of advice from someone on here. I got ventrilo and diablo 2 working swell. Warcraft 3 + tft runs but it doesnt run pretty. Anyhow I'm not exactly a computer noob, but with Linux; I am. I'm new to it, and I love it very much so far (much better then Vista). I need some advice on what exactly I need to go. Either install the nvidia driver (if so how?), configure open gl(confused about this as well, even after looking in the forum search/Google), or how do I know if I have the Nvidia driver properly working, or is it a universal driver that doesn't have 3d acceleration? Excuse my errors in certain terms, I'm so used to windows. But I'm completely able to follow instruction and learn. I say the more I do it, the more I learn.
Help is must appreciated. I'm now confused as to where this choppy and laggy-ness starts now. Btw, I love Ubuntu!

---

### Post by angryfirelord on 2007-09-03
Post the output of:
```
glxinfo | grep rendering
```

---

### Post by goffy59 on 2007-09-03
I'm very sorry to waste your time. Basically, I searched every topic about  nvidia drivers/ type mismatch and a whole lot of other errors i was having. I Learned it was a problem with the new kernel upgrade. So I used the workaround. It has something to do with the restricted repository's. Sorry I cant be more specific. I was trying to make this work for 5 hours. And finally it works, and I'm happy to know I did not need to reinstall Ubuntu and everything is becoming easier to work with. Its easy for my to learn where the problem origin is. Sorry again, delete this. Now Warcraft 3 works beautifully! I wish I could say exactly what I did, but honestly I tried many things. So it would be much help. I did reinstall the nvidia driver, and re download the kernel. Also reconfigured xorg. Thanks anyway! I love Ubuntu! I hope nvidia adds the new kernel to their repository soon! I'm sure there are others with this problem as well!

---

