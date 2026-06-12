---
title: "nvclock problems"
date: 2009-03-17
forum: General Help
---

### Post by or1on on 2009-03-17
i'm having trouble getting nvclock to compile on ubuntu 8.10, i had this program installed a week ago but then went os hopping and have come back to where i started :P but any way when i try to compile this now i get an error on ./configure it always ends with this

checking for gtk+-2.0 >= 2.4.0... checking for x11... configure: error: "X11 required for nvcontrol support"

this is nvclock version 0.8b4 and ive had it wrking b4 so im not sure what im missing now that i had b4...ive also tried using synaptic to install the version in the repos...they just never seem to install correctly
any help is appreciated

---

### Post by ruel- on 2009-03-17
Try this:
```
./configure --disable-nvcontrol
```

---

### Post by or1on on 2009-03-17
well that does get it thru configure but disables the gui :/
thanx though....any idea why it would think i dont have x11 installed or how can i tell it where to look?

---

### Post by or1on on 2009-03-17
a friend told me to install these 2 files and there dependencies and it worked like a charm

sudo apt-get install xorg-dev


sudo apt-get install libgtk2.0-dev

then nvclock will compile and install with the gui

---

### Post by fostytou on 2009-11-07
> **or1on said:**
> a friend told me to install these 2 files and there dependencies and it worked like a charm

sudo apt-get install xorg-dev


sudo apt-get install libgtk2.0-dev

then nvclock will compile and install with the gui


Thanks for the fix!  Worked in 9.10

---

