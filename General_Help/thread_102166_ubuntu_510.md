---
title: "ubuntu 510"
date: 2005-12-11
forum: General Help
---

### Post by richard willacy on 2005-12-11
got this ubuntu 510 installed but every time i come of windows and go into ubuntu i get this message this what it says, could not look up internet address for ubuntu breezy,this will prevent gnome from operating correctly,
it may be possable to correct the problem by adding ubuntu breezy to the file/ect/host, so jow do i sort this out because nothing is working right :confused:

---

### Post by taurus on 2005-12-11
I don't know what the thumnail supposed to be but can't see a thing since it's so tiny!!!  Your /etc/hosts should look something like this,

127.0.0.1       localhost.localdomain   localhost       Ubuntu

---

### Post by richard willacy on 2005-12-11
thanks for the thread but how do i get my gnome working ok, i have been trying to sort this thing out but im still at it it seems that every time i go into ubuntu this message comes up and i cant go any more into the ubuntu is there a thing which i can do to sort this thing out,and also i would like to know how to install firefox if sombody knows:confused:

---

### Post by taurus on 2005-12-11
Wait for it to finish booting up, then hold down <Ctrl><Alt>F2.  Log in and edit your /etc/hosts as

sudo pico /etc/hosts

Then, add the following line to it.  Save it and reboot...

127.0.0.1 localhost.localdomain localhost Ubuntu

---

### Post by Rackerz on 2005-12-11
I think the thumbnail is some sort of signature, 

Can you show us a screen shot of the error if possible? It would help us to better see exactly what the problem is.

---

