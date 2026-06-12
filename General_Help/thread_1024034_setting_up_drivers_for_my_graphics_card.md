---
title: "setting up drivers for my graphics card"
date: 2008-12-28
forum: General Help
---

### Post by ekolimits on 2008-12-28
how do i set up the drivers for my graphics card in ubuntu... i installed nvidia driver 71 because it has my graphics card listed but i dont know how to configure it now.

---

### Post by MartyBuntu on 2008-12-28
In a terminal:

**nvidia-settings**

---

### Post by ekolimits on 2008-12-28
tells me: you do not appear to be using a nvidia x driver.... but i installed it...

---

### Post by MartyBuntu on 2008-12-28
You installed Nvidia drivers and then restarted your machine?

---

### Post by jyaan on 2008-12-28
I've had this problem before. Annoyed me half to death.....

Anyways, try going to 'System->Administration->Hardware Drivers', and enable the driver. Then you should be able to go into nvidia-settings and get everything set up. You'll probably want to save the xorg.conf, too. nividia-settings can generate it for you, but you'll have to run the program with sudo from the command line.

---

