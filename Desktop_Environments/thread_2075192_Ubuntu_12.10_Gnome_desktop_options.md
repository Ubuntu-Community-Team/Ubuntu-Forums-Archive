---
title: "Ubuntu 12.10 Gnome desktop options?"
date: 2012-10-23
forum: Desktop Environments
---

### Post by haresear on 2012-10-23
I have an AMD Sempron 2500+ CPU with an nVidia FX5200 graphics card. In Ubuntu 12.04, Unity 2D was usable but a little sluggish. Gnome classic worked pretty well.

Just tried the Ubuntu 12.10 live CD, and Unity desktop finally came up after many minutes, but was unusable -- tens of seconds to respond to each keystroke or mouse click. So what are the other Gnome desktop options for older hardware with 12.10?

---

### Post by zombifier25 on 2012-10-23
Trying out from a LiveCD is not a good evaluation for performance, especially considering that you're using an NVidia card.

If Unity is still too heavy for you after installation, then there is GNOME Shell (which may or may not be lighter than Unity, but generally lighter), and GNOME Classic (pretty light, like old versions of Ubuntu) Also not GNOME-based but also use Gtk+ are Xfce and LXDE, and both is freakishly light.

---

### Post by haresear on 2012-10-23
I tried searching for Gnome Classic in the Software Center, but didn't find anything. I could only find Gnome-shell, and I'm pretty sure I can't run that, since it wouldn't run for me in 12.04.

---

### Post by bogan on 2012-10-23
Hi!, **harasear**,

In Ubuntu Software Center, search for 'gnome-session-fallback', install and Log-out & in selecting 'Gnome Classic' [or Gnome (no effects)], in the drop-down menu;.

Chao!, **bogan**.

---

### Post by kansasnoob on 2012-10-23
In 12.10 they dropped Unity-2D which used the Metacity window manager in favor of using Compiz + llvmpipe ...... so I maintain a lot of 5 to 7 year old boxes with VIA P4M800 graphics and I'm in the same boat.

For the most part I'm sticking with 12.04 using this type of setup:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I mean 12.04 is a 5 year LTS so why upgrade?

OTOH I'm adventurous so I've been using this respin:

[http://ubuntuforums.org/showthread.php?t=2073181](http://ubuntuforums.org/showthread.php?t=2073181)

It provides either Gnome shell or Gnome classic (no effects) by default and it seems quite stable. I'm certainly not crazy about the default artwork though :)

---

### Post by haresear on 2012-10-23
Thanks for the replies. I didn't realize gnome fallback was still available. I thought it was going to be dropped, so I was just curious if the future Ubuntu/Unity/Gnome was going to support older hardware. I guess the answer to that is negative. I've moved on to Mint 13 and Kubuntu 12.04 -- they run fine on my old hardware. I've been using Ubuntu since before 6.06, but I guess it is finally goodbye.

---

