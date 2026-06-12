---
title: "Reverting kubuntu usplash theme from ubuntu 10.04"
date: 2010-04-25
forum: Desktop Environments
---

### Post by MGMorden on 2010-04-25
Hey guys.  Got a quick question.  A while back had installed the kubuntu-desktop package onto my normal Ubuntu 9.10 install in order to use several KDE apps (mostly KGet).  It changed my bootsplash to the Kubuntu one at that point which I found mildly annoying (as I still use the standard Gnome interface - I just wanted the KDE libs/apps installed). 

Anyways, I've updated to version 10.04 RC and the Kubuntu splash persisted (I thought the upgrade would replace it), and now the colors on it are corrupted.

I found some instructions on how to revert it (*sudo update-alternatives --config usplash-artwork.so*), but that command doesn't seem to work in 10.04 anymore.

Anybody know how to do this in this release?  Thanks.

PS  Not sure if this is normal, but I'm also having a problem where when logged into Gnome, when inside of a KDE app my cursor theme reverts to default until I leave that windows.  Pretty strange.  I thought it was picking up the cursor theme from KDE for a while but after logging in there I noticed that KDE is not using the same default theme.  Not sure if this is a normal problem or if it's just a side affect of me upgrading rather than doing a clean install of 10.04 (my 9.10 install itself was an upgrade from 9.04).  

I appreciate any assistance offered.

---

### Post by tommyboy808 on 2010-05-07
for the mouse icon i did this
open terminal, $sudo gedit /usr/share/icons/default/index.theme
and just change to DMZ-White or whatever u want it to be
not sure what u reallly meant, but when i installed kde, it changed my mouse icon so this is how i fixed it

so far i havent been able to find a solution to the splash screen being replaced, but i dont find it too be too annoying since the new usplash screen is so plain so at least the blue looks pleasant

---

### Post by Ginsu on 2010-05-08
Just figured this out,

Install galternatives
sudo apt-get install galternatives

run with sudo galternatives or from menu Applications/System Tools/Alternatives Configurator

Find default.plymouth and select /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth

Mouse pointer can also be changed from x-cursor-theme

---

