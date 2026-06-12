---
title: "geforce2 go"
date: 2005-12-12
forum: General Help
---

### Post by actronx on 2005-12-12
hello again ,
is there any drivers for NVIDIA gerforce2 go ??? ive tried to install nvidia-glx but it didnt work ?actually it destroied my x server ...so i had to reconfigure it again to be able to use gnome interface .


Thanks in advance

---

### Post by schilcha on 2005-12-12
I have a geforce2go on my acer travelmate. I installed the nvidia-glx-legacy package via synaptic -- "legacy", because it mentions geforce2go explicitly in the package description. 

I also needed to enable it using
```
sudo nvidia-glx-config enable
```

Works for me. 

btw, have you managed to enable the vga-conntector? -- I'd like to connect a beamer. Up to now, I miserably failed, although I tried virtually any howto.

Good Luck

---

### Post by actronx on 2005-12-12
well ... i cant find this package called "nvidia-glx-legacy" i just found nvidia-glx ...:( ?

---

### Post by schilcha on 2005-12-12
hm, what can I say... I found it in synaptic, searching for "nvidia legacy". It has an ubuntu-icon next to it, so I guess it's officially supported. 
For the sake of completeness: I've activated all components (officially supported, universe, multiverse and restricted copyright) wherever possible. Just to make sure: I'm running on i368/i686, so no AMD64/PPC/whatever stuff in my installation.

---

