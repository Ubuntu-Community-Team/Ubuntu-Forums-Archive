---
title: "&quot;dpkg-reconfigure linux-image-xxx&quot; damaged my grub config"
date: 2006-08-02
forum: Desktop Environments
---

### Post by mycelo on 2006-08-02
I was trying to fix my usplash boot screen which was still showing up as "kubuntu" after KDE removal and one of the threads that I found suggested to run:

```

sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so

sudo dpkg-reconfigure linux-image-$(uname -r)
```
But the latter command rendered my distro unbootable, always getting stuck with the message "Waiting for root file system".

After booting from live CD I figured out that the **/boot/grub/menu.lst** was pointing to the wrong partition, where I had to fix manually both hd(x,x) and /dev/hdxx references.

[EDIT] Now, whenever I install kernels, services or anything related, I have to fix grub again, becase it defaults to the partition where the distro was originally installed. Where else do I have to change, so my box completely forgets about its previous drive/partition?

mycelo

---

### Post by Ramses de Norre on 2006-08-02
Have you ever changed the device and partition numbers yourself? Because if that's true you probably didn't change grub's default options.

---

### Post by mycelo on 2006-08-02
Indeed, I moved this partition to another hard-drive, following directions that I found in this very forum.

Could you please tell how can I change the mentioned default options?

mycelo

---

### Post by mycelo on 2006-08-03
Bump?

---

### Post by Lunar_Lamp on 2006-08-03
I have had the same problem - it is annoying that upgrading my kernel headers today caused my system to become unbootable until I edited my grub to point to the new locations.

---

### Post by Sciamano on 2006-08-03
Same here...

---

### Post by mycelo on 2006-08-04
bump?

---

### Post by mycelo on 2006-08-07
Nobody knows, I guess... :-k

---

### Post by mycelo on 2006-08-09
Oh well, bump.

---

### Post by Tomosaur on 2006-08-09
Could you paste your menu.lst up here, and the results of the following command:
sudo fdisk -lu

---

### Post by Ramses de Norre on 2006-08-09
Find this lines: ```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

```
And change the last of them to point to the right device and partition for your ubuntu install.
Then run ```
sudo update-grub
```

---

### Post by mycelo on 2006-08-09
Thank you.

Should I remove the "#" from this line?
```
# groot=(hd1,0)
```

---

### Post by Ramses de Norre on 2006-08-09
No, it will break grub if you do, all the default options start with a #. And as you can notice the lines that are effectively commented out start with ## ;)

---

### Post by mycelo on 2006-08-09
Oh, good to know, thank you. Yeah I noticed the double "#" but I though it was some kind of indented comment, or something... :-P

I'm gonna test in my lunch time.

---

### Post by mycelo on 2006-08-10
Way to go, Ramses, you rock. I'd never realize that those comments weren't mere comments. But I also had to change the default root partition in the command just above that (/dev/hdxx). Also I'd like to thank Tomosaur too.

mycelo

---

