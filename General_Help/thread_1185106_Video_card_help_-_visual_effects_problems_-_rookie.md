---
title: "Video card help - visual effects problems - rookie"
date: 2009-06-11
forum: General Help
---

### Post by sneekING on 2009-06-11
Ok, so I installed 9.04 and got a few things up to date, but cannot get the 3d cube to work - all I have is 2 square in the lower right that I can toggle between and when I drag a window from one side to the other it goes haywire (graphics wise) and flutters all over the place for a second then smooths out. Just gets buggy when making the transition between sides. That bothered me enough to buy a video card. Before that I was just using onboard nvidia 6150se. So I got this nvidia 9400 gt and thought it HAS to help smooth things out and maybe then the desktop cube will work. Nope. Still buggy and won't go to CUBE even when I check the box to allow it. 

So I've tried installing correct drivers for the card and believe i have, but I sense no improvement. What is missing that is not allowing the cool desktop effects to take place and cause my screen to freak out when switching over sides like that??? Thanks anyone who can help

---

### Post by spcwingo on 2009-06-11
I think what you're looking for (at least getting the compiz cube going) is:

```
sudo apt-get install compizconfig-settings-manager
```

Then run it from system>preferences>compizconfig-settings-manager.

---

### Post by synapsys on 2009-06-11
Also make sure you have at least 4 (cube) virtual desktops.

---

### Post by colau on 2009-06-11
> **synapsys said:**
> Also make sure you have at least 4 (cube) virtual desktops.
Sorry for this post.
Why do I have two virtual desktop?

---

### Post by sneekING on 2009-06-12
Ok, so I found out that I needed to right-click on the 2 panels in the lower right hand corner of the screen and select 'properties' and tell it to show 4 panels so the "cube" would work. I selected the option that smooths out the corners of the cube when it's rotating so the choppy/distortion is basically fixed. Although I still feel like the video card isn't working to the fullest. 
Is there a way to check to see how well the video card is performing? Can someone walk me thru how to install and select the proper video card settings for a nvidia 9400gt in ubuntu 9.04 x86-64 with an AMD 64 processor? I did download the drivers, but not sure if I did it right. I would need my hand held since I just type the commands I see on the internet. I don't understand exactly what I'm doing yet. Thanks

---

