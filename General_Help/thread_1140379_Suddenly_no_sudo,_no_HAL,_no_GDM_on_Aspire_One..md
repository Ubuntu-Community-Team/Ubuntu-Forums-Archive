---
title: "Suddenly no sudo, no HAL, no GDM on Aspire One."
date: 2009-04-27
forum: General Help
---

### Post by stevejesus on 2009-04-27
Hi guys,

So I bought a netbook for my wife (Acer Aspire One) and install Juanty for her.  It's been great until today.  I added myself as a user and then went to reboot the machine.  When the machine came back to life, there was a GDM error.  So I went to reconfigure the package but my wife's username was no longer on the sudoers list!  

I dropped into single-user mode and reconfigured the gdm package from the shell, so now I am able to get into X, but HAL won't start!

I checked out /etc/goup to find that her username doesn't belong to any groups.  So I added her to a few while carefully comparing those groups against the ones that I belong to on my machine.  

Still can't start HAL, still can't do anything...  Suggestions?

---

