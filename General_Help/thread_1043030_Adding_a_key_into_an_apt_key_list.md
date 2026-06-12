---
title: "Adding a key into an apt key list?"
date: 2009-01-18
forum: General Help
---

### Post by asheq on 2009-01-18
Please refrain from laughing, I'm a complete newbie.
Alright, so, I'm trying to install a webcam driver for my built-in webcam and in this tutorial it's asking me to add a key into an apt key list.
Eugh.
I don't know how. Tried googling it, nothing helpful came up.

Explain, and please put it in simple terms. I'm a fast learner when it comes to computers, but you have to explain. 

Any help is much appreciated.

---

### Post by hikaricore on 2009-01-18
Hi again, could you please link the tutorial so I can see what you're dealing with?

**Also here's something related on how to deal with repositories like the one you're probably working with: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by asheq on 2009-01-18
[http://www.arakhne.org/download.html](http://www.arakhne.org/download.html)


I think I did the package source thing right, maybe not. I'm not sure.
Hmph. :|

---

### Post by hikaricore on 2009-01-18
Eww i see they made a mess of their instructions.

> wget -q [http://download.tuxfamily.org/arakhne/public.key](http://download.tuxfamily.org/arakhne/public.key) -O- | sudo apt-key add -

Should do the trick, they just gave you like 3 different ways to do this.
AFter that you should be able to download from their repos without getting annoying message about signed keys :p

---

### Post by x33a on 2009-01-18
if you are adding a new repository, then even if you don't add the apt (gpg) key, you can still add the repository.

The key basically verifies, that your source is trusted.

you can try something like this if you know the url of the key:

wget -q "url" -O- | sudo apt-key add - && sudo apt-get update

don't include the quotes.

---

### Post by asheq on 2009-01-18
hmmm.
I give up for the night. It's 7 AM.
I'll give this another try tomorrow :p
thanks everyone.

---

