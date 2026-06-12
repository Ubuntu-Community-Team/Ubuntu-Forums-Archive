---
title: "Switch from Ubuntu to Kubuntu on Feisty"
date: 2007-04-25
forum: Desktop Environments
---

### Post by Kazade on 2007-04-25
I meant to install Kubuntu for a friend but accidentally downloaded the wrong ISO. As I noticed my mistake after I downloaded I just figured I'd install Ubuntu, then install Kubuntu-desktop then remove Ubuntu-desktop.

Unfortunately, it doesnt work like that, I have installed Kubuntu-desktop and KDM is now the default. But removing ubuntu-desktop just removes the meta-package.

How can I remove all of the ubuntu programs to leave a clean Kubuntu install?

---

### Post by jimbren on 2007-04-25
Try 
```
sudo aptitude remove ubuntu-desktop
```

Although, you may want to consider leaving it as it is.  I've found that the Ubuntu apps run just fine in a Kubuntu session, and your friend might like the expanded choices.  I use Kubuntu exclusively, but I like having Ubuntu installed for the range of programs. 

jimbo

---

### Post by Kazade on 2007-04-25
Thanks, but I already tried that, only the ubuntu-desktop meta package is removed :(

---

