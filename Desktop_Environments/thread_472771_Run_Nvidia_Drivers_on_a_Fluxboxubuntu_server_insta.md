---
title: "Run Nvidia Drivers on a Fluxbox/ubuntu server install?"
date: 2007-06-13
forum: Desktop Environments
---

### Post by jseiser on 2007-06-13
I tried to download nvidia-glx and then change my driver to nvidia by reconfiguring xorg, this reults in myself being unable to "startx" at all, it gives me an error.  When i run a ful ubuntu system, i can just download glx, then use the restricted driver manager and it works fine.  How can one accomlish loading the drivers with out a full ubuntu install?

i did, 
server install
apt-get fluxbox

and i start fluxbox with "startx"

---

### Post by yabbadabbadont on 2007-06-13
What is the exact error message?

What are the contents of your ".xinitrc" file in your home directory.  Mine is ```
/home/daffy $ cat .xinitrc 
startfluxbox
```

---

### Post by jseiser on 2007-06-13
eval `cat ~/.fehbg`

i hit startx it starts to load flux, shows for a second then goes back to the terminal and says something about error no screens found or something.  I cant re-produce it without ruining my installation for the 3rd time this week lol.  everything works fine except for when i try and use the nvidia drivers.  If i just install ubuntu or any other full distro it just works.

---

