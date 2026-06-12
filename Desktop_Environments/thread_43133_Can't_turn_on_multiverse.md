---
title: "Can't turn on multiverse"
date: 2005-06-20
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-20
Yeah... Synaptic wont turn on universe or multiverse. Or at least acknowledge that they are en. Universe is enabled. Multiverse isn't. It says neither is (where the check boxes are). How can i fix this? Synaptic just wnt remember that i've ticked the boxes. Can I write something in terminal?

Thanks

---

### Post by SGC on 2005-06-20
You need to have the following lines in **/etc/apt/sources.list**

```

deb http://us.archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse

```

After saving the file, do **sudo apt-get update** in the terminal

---

### Post by Dave_is_sexy on 2005-06-20
Done. But no change :(

Neither Azureus nor Java are listed anywhere - and no methods i've seen on the web can actually install java with it's dependencies.

Can anyone fix this?
Cheers

---

### Post by Xian on 2005-06-20
[QUOTE=Dave_is_sexy]Neither Azureus nor Java are listed anywhere - and no methods i've seen on the web can actually install java with it's dependencies.
[/QUOTE]
You need to add the backport repos to your /etc/apt/sources.list
Then do your 'sudo apt-get update'.

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Dave_is_sexy on 2005-06-20
Brilliant! That's downloading stuff ^_^

I wonder why they're not acknowledged as part of multiverse. Isn't that the whole point of multiverse? Maybe mine's just broken (I'm pretty sure it is)

Thanks

---

