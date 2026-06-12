---
title: "Low sound volume"
date: 2009-04-24
forum: General Help
---

### Post by QueenZ on 2009-04-24
Yesterday I installed Ubuntu and the sound volume was ok but today it's very low.. everything seems to be up but the sound is very low..

---

### Post by Bucky Ball on 2009-04-24
Double click the speaker icon for more options. Make sure master is up and all things ticked appropriately. I am on an Xubuntu box and can't get you exact instructions just now but later. You can also right click the speaker icon and check the properties etc. You might try a different device. Experiment and see what works. Let us know how you went.

---

### Post by QueenZ on 2009-04-24
OK, this is really weird.. i rebooted my computer and the volume is ok again.. and this is not the first time it's happened..

---

### Post by Bucky Ball on 2009-04-24
What version of Ubuntu?

---

### Post by paradigm2 on 2009-04-24
> **QueenZ said:**
> Yesterday I installed Ubuntu and the sound volume was ok but today it's very low.. everything seems to be up but the sound is very low..

If it is 9.04 (Jaunty) and you have tried "gnome-volume-control" making sure PCM and all the others are turned up, you might want to take a look at the advice I gave this gentleman.

[http://ubuntuforums.org/showpost.php?p=7132082&postcount=7](http://ubuntuforums.org/showpost.php?p=7132082&postcount=7)

At least the portion on upgrading alsa and pulseaudio using the ppa.  If that does nto work you may wish to consider the new kernel as well.  I had the same issue and doing the above helped me.

But you should also look for other solutions first.

What hardware are you running?

Go to terminal and:

```

lspci

```

---

