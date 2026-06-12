---
title: "loading saa7134 with options?"
date: 2005-12-15
forum: General Help
---

### Post by nik on 2005-12-15
Hi all

Have been watching the forums carefully for a while, and have my breezy up and running nicely now :) Thanks to all great howto's and help from this forum.
Now I have a problem. Finally got my flytv platinum mini tv card to work, with the saa7134 module (kernel 2.6.14). The module is loaded at boot, but to get the card working I need to give it the option 'card=39'. Any way to set this? Now I have to rmmod the module after boot, and then 'modprobe saa7134 card=39' Would be nice to have it automagic :)

---

### Post by Domie on 2005-12-15
Did you test it?

Because I bought two cards with the SAA7134 module and none of it worked and nobody knew the solution.

---

### Post by nik on 2005-12-15
Yes, it works great. It's a FlyTv Platinum 33 mini. I don't know the exact tuner (Philips of some kind). However, I have to use the 2.6.14 kernel, didn't work with any previous ones.

---

### Post by Domie on 2005-12-17
[QUOTE=nik]Yes, it works great. It's a FlyTv Platinum 33 mini. I don't know the exact tuner (Philips of some kind). However, I have to use the 2.6.14 kernel, didn't work with any previous ones.[/QUOTE]

Well, you have to add a line:

options saa7134 card=39

But I'm not sure to which file any more in /etc.

It's something like modprobe.conf or modules.conf. I'm typing on a win computer right now at work (ssssjt!!!!)

---

### Post by egodust on 2006-01-31
To do that you need to create a file inside /etc/modprobe.d/, e.g.:
```

sudo gedit /etc/modprobe.d/saa7134

```

then insert the ```
options saa7134 ....
```

---

### Post by nik on 2006-01-31
I only added 

saa7134 card=39

to /etc/modules ...

Works fine here :)

---

