---
title: "[SOLVED] Installing/Removing Ubuntu Studio (w/ ubuntu installed)"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by iheartubuntu on 2007-09-29
I already have Ubuntu working nice. Came across Ubuntu Studio and would like to install it on top of my Ubuntu. Tips? Also, If I dont like it, can I easily remove it or revert back to my 7.04 Ubuntu? Thanks:)

---

### Post by Rupertronco on 2007-09-29
Ubuntu Studio is not a different OS. It's just software. Just download the Ubuntu Studio Video, Audio, and Graphics packages via synaptic. The only differences are some themes, and you can apply those too. 

There's no need to reinstall the OS.

---

### Post by iheartubuntu on 2007-09-29
Thanks... downloading now.So if I get tired of the look and want to keep certain programs, how do I change the "look"?

---

### Post by Forlong on 2007-09-30
Ubuntu Studio's look isn't in the Ubuntu repos anyway.
You would have to add the repository:
```
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
```
Here's how you get the key:
```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add -
```
Then install **ubuntustudio-artwork**

---

### Post by walsh416 on 2008-03-10
When I try installing the key in teminal it always comes up with:

gpg: no valid OpenPGP data found.

Is there anything I can do about this?

---

