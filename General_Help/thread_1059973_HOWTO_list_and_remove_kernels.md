---
title: "HOWTO list and remove kernels?"
date: 2009-02-04
forum: General Help
---

### Post by bliffle on 2009-02-04
I must have a dozen kernels, how can I list them and how can I delete old unused kernels to free up their space?

I tried 'apropos kernel' without much success.

---

### Post by damis648 on 2009-02-04
```
sudo apt-get remove linux-image-kernel-version-andwhatnot
```

---

### Post by sisco311 on 2009-02-04
Search for linux-image in Synaptic an uninstall the old kernels.

```
uname -r
```should print your current kernel version.

It is advised to keep at least 2 working kernels.

---

### Post by ibutho on 2009-02-04
You can use Synaptic or the Add/Remove program to search for linux-image and uninstall the versions you do not need. An alterative would be to use apt-cache e.g.
```
apt-cache search linux-image
```
You can then use "apt-get remove" to uninstall the kernels you do not need.

---

### Post by Slim Odds on 2009-02-15
well... if you're going to remove the linux-image files, you should probably also remove linux-headers and linux-modules

I was looking for something to simplify this process.....

Looks like I might have to write my own script.....

---

### Post by fragos on 2009-02-15
I find using Synaptics the easiest way for me. I search on the version, i.e. 2.6.27, and can see what kernel elements are available and installed. I mark the older ones for Complete Removal, click Apply and I'm done. This method also updates GRUB's memu.lst for you.

---

### Post by mb_webguy on 2009-02-15
HOWEVER, kernels don't take up much space, and most people who ask about removing kernels do so because they don't want them to show up in the GRUB menu.  It's generally better (and safer) to edit the GRUB menu so older kernels aren't displayed than to mess around with removing kernels.

---

### Post by Slim Odds on 2009-02-15
> **mb_webguy said:**
> HOWEVER, kernels don't take up much space, and most people who ask about removing kernels do so because they don't want them to show up in the GRUB menu.  It's generally better (and safer) to edit the GRUB menu so older kernels aren't displayed than to mess around with removing kernels.

Easy for you to say (I guess).

I have an older system that's been up for a long, long time. The old kernels where taking up a large percentage of my disk space.

---

### Post by mb_webguy on 2009-02-16
> **Slim Odds said:**
> Easy for you to say (I guess).

I have an older system that's been up for a long, long time. The old kernels where taking up a large percentage of my disk space.

Well, I did say *most* people.  Considering the size of the typical hard drive these days, a 100MB kernel is practically nothing...

---

