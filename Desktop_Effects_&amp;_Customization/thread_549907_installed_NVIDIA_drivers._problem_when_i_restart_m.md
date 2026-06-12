---
title: "installed NVIDIA drivers. problem when i restart my computer.failed to start X Server"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by srikanth40 on 2007-09-13
I have NVIDIA graphic card ( GeForce 7300 GT). intel core2 Duo processor.
Have feisty fawn ( 64-bit) on my system.

I downloaded NVIDIA drivers from the nvidia website ( .run file).
I stopped X Server. I installed the drivers. Started X server. Desktop effects were enabled.

but when i restarted my system. i have an error saying
"Failed to start X Server (your graphical interface)..."

I logged-in  in the text mode.
Replaced the 'xorg.conf' file with 'xorg.conf.backup' (cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf)
now if i restart my system i could get GUI, but NVIDIA drivers are not detected.

again i have to install them.
i dont no why it is showing an error saying "Failed to start X Server (your graphical interface)..."

---

### Post by dreadlord_chris on 2007-09-13
yeah... I used to install my NVIDIA drivers by hand - till I got tired of dealing with niggling little issues like you're having...
I now use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install my drivers - haven't had a problem since then...

---

### Post by Happy_Man on 2007-09-13
Uh.... there are drivers for your card in the Ubuntu repos, you know. Uninstall the drivers from the Nvidia website, and then enter in a terminal: ```
sudo apt-get install nvidia-glx-new
```

---

