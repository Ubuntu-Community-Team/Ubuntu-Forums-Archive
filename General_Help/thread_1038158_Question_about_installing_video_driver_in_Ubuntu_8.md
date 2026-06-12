---
title: "Question about installing video driver in Ubuntu 8.10"
date: 2009-01-12
forum: General Help
---

### Post by jacatone on 2009-01-12
After installing Ubuntu 8.10 on an old AMD Duron white box, I'm confused about how to install the video driver. In Synaptic it lists "nvidia-glx-71" as the correct driver for the old video card, but once installed it doesn't work. When I try configuring it, I get "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig'as root)and restart the X server". Did that, and it still doesn't work. If I update Ubuntu a "NVIDIA accelerated graphics driver (version 96) [Recommended]" appears in Hardware Device, but installing that screws up the Ubuntu install. What should I do here? Thanks.

---

### Post by oldos2er on 2009-01-12
"When I try configuring it, I get "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file and restart the X server"

 You might see this error if you're not running as root when trying to configure the drivers.

---

### Post by jacatone on 2009-01-12
Did run as root.

---

