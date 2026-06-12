---
title: "Upgraded - now I can't find the nvidia drivers that worked for me (geforce go7200)"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by olavjunior on 2007-05-08
Please se my original thread 
[http://ubuntuforums.org/showthread.php?p=2604119#post2604119]("http://ubuntuforums.org/showthread.php?p=2604119#post2604119")

I got compiz to work under edgy with some restrikted drivers that werent acctually supposed to work for my card (or my card wasn't directly supported) I'm using a geforce go7200 on a hp dv2130. 

After I upgraded, i've tried alot inkl envy, but no matter what I do I can't get the nvidia driver to work. The last thing I tried was this:
sudo aptitude --purge remove nvidia-glx-new nvidia-kernel-common xorg-driver-fglrx
sudo aptitude clean
sudo aptitude update
sudo aptitude install nvidia-glx-new

After that I could actually use the nvidia instead of the nv in xorg, but still I couldn't get compiz to work, (I have all the addrgbglxvisuals, ect... I made the file identical with the old working one)

Any suggestions??

EDIT: Well, I jumped into the unknown and installed Feisty as fresh install. I have my home on a seperate partition, so I wouldn't loose any of my files. Everything worked out fine! I said I wanted to use the restricted nvidia-drivers, rebooted, and I was up and going! Desctop-effekts work fine, so I guess I won't have any troubble installing beryl or compiz... 

I didn't know I had to reinstall all my apps though!... Is that the case, or have I missed out on something? (My system monitor says that compiz is running, but I cannot run compiz-tray icon or anything I could earler. Are the 3d-effects that come with feisty named compiz in system monitor??)

---

