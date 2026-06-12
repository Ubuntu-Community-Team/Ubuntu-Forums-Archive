---
title: "Debian 8 - Which Desktop Environment I Should Choose ?"
date: 2016-03-07
forum: Debian
---

### Post by KaraBuzab on 2016-03-07
Hello fellow Linux Redditors,
  I want to install Debian 8 aka Jessie but I'm wondering which Desktop  Environment I should choose. Previously I have used Openbox to be  precise Crunchbang because, it's simple and it doesn't need so much  configuration and there are only basic programs which comes with it. I  just install it, change few things and I'm basically ready to roll.  However, Debian 8 "Jessie" comes only with: 


  GNOME (Doesn't like it that much)

  XFCE (Haven't tried it yet)

  KDE (I have tried it and in my opinion too many options and a lot of not needed stuff/garbage comes with it)

  Cinnamon (Haven't tried it yet)

  MATE (Haven't tried it yet)

  LXDE (Haven't tried it yet)


  When it comes to specs my computer is the beast (6 core CPU and 16 GB of Ram) and I can run any Desktop Environment.

  So, can someone give me advice here please ?

  Thank You.

---

### Post by howefield on 2016-03-07
Thread moved to the "*Debian*" forum.

---

### Post by v3.xx on 2016-03-07
LXDE should come with the least amount of stuff and garbage.

---

### Post by arochester on 2016-03-07
Perhaps not the answer you are looking for...

The "best" Desktop Environment is the one YOU like and which suits YOUR computer. OK you have told us the basic specs of your computer, but how can we advise you about what YOU like or don't like?

Openbox, as used by Crunchbang, is not a Desktop Environment it is a Windows Manager. Have you tried and dismissed Bunsenlabs Linux [https://www.bunsenlabs.org/](https://www.bunsenlabs.org/) and Crunchbangplusplus [https://crunchbangplusplus.org/](https://crunchbangplusplus.org/) ?

With some of the Desktop Environments you do not need to install a lot of unnecessary applications that you will never use. If you install lxde-core, instead of lxde you will get less. Similarly lxqt-core instead of lxqt.

Similarly you can stop "recommends" being installed. See e.g. [https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends](https://superuser.com/questions/615565/can-i-make-apt-get-always-use-no-install-recommends)

---

### Post by v3.xx on 2016-03-07
Good point arochester :)

Perhaps the OP would like to take a closer look.

[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

---

### Post by KaraBuzab on 2016-03-07
I also want to create my own distro, I know a lot about Linux but what bothers me is that after I finish polishing it in my Virtual Machine, how do I make a live bootable ISO with the install menu ? It would be good to install it on multiple computers in the future. Any recommendations ? I know that OpenBox is an Windows Manager but I still like it since it's not that bloated and you don't need to spend hours on every settings which are in the distro and the only main one's like Wallpaper, Icons etc, that's why I love OpenBox.

---

### Post by goofprog on 2016-03-07
For low overhead, XFCE, LXE, MATE, or Cinnamon.

---

### Post by v3.xx on 2016-03-07
I think I would start with LXDE.  To do this you would need to use the mini iso and build your desktop.  You can even do this with less packages by not installing the recommended packages.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://packages.ubuntu.com/wily/lxde](http://packages.ubuntu.com/wily/lxde)

[https://wiki.archlinux.org/index.php/LXDE](https://wiki.archlinux.org/index.php/LXDE)

---

### Post by arochester on 2016-03-07
Or to stay with Debian follow this: [https://www.maketecheasier.com/build-lightweight-linux-for-low-end-laptop](https://www.maketecheasier.com/build-lightweight-linux-for-low-end-laptop)

Load lxde-core instead of lxde.

Choose carefully the other apps you need.

Stop recommends as I said above.

---

