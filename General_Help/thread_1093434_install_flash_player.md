---
title: "install flash player"
date: 2009-03-11
forum: General Help
---

### Post by denis poisson on 2009-03-11
hello i m a new ubuntu user. i ve download flashplayer but idon t know how to install it

---

### Post by aktiwers on 2009-03-11
Open synaptics package manager (in System = Administration = Synaptics package manager)

and search for:
flashplugin-

and install it the "flashplugin-nonfree".

then restart Firefox

---

### Post by Therion on 2009-03-11
There's an easier way...  Go to System/Accessories/Terminal

Copy and Paste the following:```
sudo apt-get install ubuntu-restricted-extras
```

Enter your password when asked, follow the prompts and, *voila,* you're done.  

This will also install additional codecs you'll most likely need (for things like .mp3 playback and Java).

---

