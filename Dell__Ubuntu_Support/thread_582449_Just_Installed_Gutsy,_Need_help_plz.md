---
title: "Just Installed Gutsy, Need help plz"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by Khuezy on 2007-10-19
Hi, I can't update my Nvidia driver for some reason. I also can't find Compiz Fusion

Thanks

---

### Post by Dellfan on 2007-10-19
Compiz is part of Gutsy... likely just not enabled until you get your graphics card sorted out.

What are you trying to do to update the driver? It "just worked" on my 1505 with an Nvidia card. Did you have a tweaked xorg.conf prior to updating? Could you list your Device and Monitor section of /etc/X11/xorg.conf.

---

### Post by Khuezy on 2007-10-19
I'm trying to update the graphics card in the Restricted Driver Manager but it won't work. How do I tweak the xorg.conf?

---

### Post by Dellfan on 2007-10-19
Please list the contents of /etc/X11/xorg.conf

---

### Post by scapalexis888 on 2007-10-19
If the drive dont show up in the restricted drivers manager, that just means you have the most updated one. If it works now then i dont see why you want to upate it. If you insist, you might want to look up a program called Envy.

---

### Post by Dellfan on 2007-10-19
Goto System -> Administration -> Software Sources.

Make sure main/universe/restricted are selected (you can select multiverse too if you really want).

Open a terminal, then ->

```

sudo aptitude update
sudo aptitude install nvidia-glx-new

```

---

