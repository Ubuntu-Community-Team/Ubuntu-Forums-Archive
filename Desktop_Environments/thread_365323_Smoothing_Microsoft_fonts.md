---
title: "Smoothing Microsoft fonts"
date: 2007-02-19
forum: Desktop Environments
---

### Post by B. W. on 2007-02-19
I installed the extra Microsoft fonts in Ubuntu, but they look horrible on my LCD. Is there any way to smooth Microsoft TrueType fonts in Linux? There are font rending options in Ubuntu, but they don't seem to apply to them (I tried replacing .fonts.conf too, which seems to do the same thing anyway).

---

### Post by Jeremy23 on 2007-02-21
A few things I do:

[LIST]
[*]First, I use this guide to install improved subpixel rendering packages: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)
[*]Then, I type ```
sudo fontconfig-config
``` and select 'autohinter'.
[/LIST]

Then, I just tweak the hinting in the Font control panel.

---

### Post by Haegin on 2007-07-23
> **Jeremy23 said:**
> A few things I do:

[LIST]
[*]First, I use this guide to install improved subpixel rendering packages: [http://www.ubuntuforums.org/showthread.php?t=235526](http://www.ubuntuforums.org/showthread.php?t=235526)
[*]Then, I type ```
sudo fontconfig-config
``` and select 'autohinter'.
[/LIST]

Then, I just tweak the hinting in the Font control panel.


I think the command you meant was
```

sudo dpkg-reconfigure fontconfig-config

```

Also if you have trouble getting the GPG key when using the guide Jeremy23 mentions then download [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) and save it somewhere and then import it using the repositories configuration dialog in synaptic.

Finally that guide is slightly out of date now and mentions an edgy repository. You can safely change the word "edgy" to "feisty" or "gutsy" and get the correct packages for your distribution.

Hope this helps

---

