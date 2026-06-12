---
title: "Two questions concerning KDE/Kubuntu setup"
date: 2010-01-27
forum: Desktop Environments
---

### Post by djmoore85 on 2010-01-27
Hey yall. I have a sort of fresh install of 9.10, had Xfce for the environment at first. Didn't like the complications with gettin Compiz working, so I downloaded the kubuntu-desktop package. I do like the KDE, but would like to make sure that my installation is cleaned up, i.e. unnecessary packages removed and such, also where I would go for in-depth customization. I have Compiz setup for desktop effects and Emerald for my window theming/management. However, I am wanting to go more in-depth by changing panel color, making kwins involvement go on the backburner, and basically let Emerald handle windows and Compiz handle effects. I also would like to get all the plazmoid coloring and such to match window theming and I suppose in a nutshell I want to get everything matched and customized to "fit" better. Thank you all for the help and sorry for the rambling

---

### Post by nerdy_kid on 2010-01-27
you will need to look into plasma themes on kde-look.org.  Some of the themes will automaticly adjust to the current color scheme (not sure though).  If you are going to mix compiz and emerald into the mix, the color matching will be harder because they dont take kdes color scheme into account.  Kwin has a window decorator called aurorae that is very similar to emerald that you might want to check out, also if you decide in the end to go with compiz, just set compiz as the default window manager in systemsettings/Default Applications (then logout/back in) and kwin should be off entirly.  I hope this helps :)

---

### Post by djmoore85 on 2010-01-27
Thank you very much for the tip. Got Compiz/Emerald handling everything now beautifully. I'll start peruzing some themes to see if I can get any that are more green based vs blue based. Anyone have suggestions for cleaning up installed but unused packages?

---

### Post by Zorael on 2010-01-29
You can install the **gtkorphan** package to get the graphical frontend to the **deborphan** tool. It will list "orphaned" packages; individually installed packages that don't belong to any metapackages. It will only list libraries by default, but I believe there's a box you can check to make it include applications as well.

Other than that, I don't know of any easy way outside of opening Synaptic and browsing what's actually installed, removing stuff you find you don't need anymore.

---

### Post by djmoore85 on 2010-01-29
Thanks man. Seems to have cleaned up a bunch of xfce4 stuff I didn't require anymore. I don't want to delve too far into removing GNOME items though, I know there area few used in Kubuntu. Unless I am mistaken. I just don't want to go all out removing packages and then end up breaking my install.

---

