---
title: "Best way to transition from fglrx to nvidia?"
date: 2009-06-19
forum: General Help
---

### Post by Yashiro on 2009-06-19
I'm soon to be removing my Radeon 4850 (fglrx) which is to be replaced by a GTX260 (nvidia).

While I'm sure I could muddle through and get it all sorted I would appreciate any tips from people who have done this before. A brief step by step process would save me alot of time and would be helpful to more than just myself I imagine.

---

### Post by Yashiro on 2009-06-23
Just some quick notes should anyone find this via a search.

Check xserver-xorg-dev should is installed, along with the linux-headers package for your current kernel.

Then:
> Problem: Need to fully remove -fglrx and reinstall -ati from scratch

Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter:

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  dpkg-reconfigure xserver-xorg

Then reboot (or fix up the kernel modules and restart gdm) 
You should now be relatively cleaned up and able to remove the old card and pop in the new one.

When installing from the nvidia.run package make sure you have root access, stop gdm and drop to init 3 (telinit 3).

Don't download the kernel files from nvidia's ftp when asked.

---

