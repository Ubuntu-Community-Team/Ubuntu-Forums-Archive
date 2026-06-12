---
title: "From Kubuntu back to Ubuntu"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Phreaker on 2006-06-01
Hello,

I installed Dapper Today and I installed kubuntu-desktop just to see what it is.Unfortunately I didn't like it and now wish to revert back to Ubuntu.
Can you offer some advice? Kubuntu-desktop changed the splash and I want the ubuntu one back ....

---

### Post by Ramses de Norre on 2006-06-01
ubuntu-desktop is still installed? (If not sudo aptitude install ubuntu-desktop), there's a howto in the howto section (logic ;)) about uninstalling kubuntu packages.
For setting gdm instead of kdm (if that's necessary): ```
echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-manager
```

For the splash: ```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by Phreaker on 2006-06-01
Yes it is still installed .
And thanks for the splash

---

### Post by derrick1985 on 2006-06-01
last that I heard to get rid of all the kde packages, you have to do them one by one.

Now, I could be wrong, and I hope I am. You could also try to go into synaptic and search for kubuntu-desktop and choose complete removal.

---

