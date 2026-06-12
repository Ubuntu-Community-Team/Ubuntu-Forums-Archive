---
title: "Videos are not playing in bottom portion of screen (LXDE)"
date: 2013-12-08
forum: Desktop Environments
---

### Post by zkr300 on 2013-12-08
Videos only play in the top 60% approximately of  the screen. I tried this with gnome-mplayer as well as with VLC. I suspect it's a GUI problem.


Also the files located on the bottom of the screen are not completely visible, part of the file name is cut off until I move my mouse over it.


I now use the GUI LXDE Lubuntu after being with Ubuntu (Gnome) for some time. In Gnome, I did not have this problem but a slightly different one -  video's were extremely slow and non responsive.

I have a 1.5 GHz Intel Celeron M with 1 GB RAM, 40 GB hard disk, and nvidea GeForce 5200 video card. As far as I know all drivers are updated - used sudo apt-get update.
My hardware is outdated and slow, but it works so I can't understand this.


Please help!

---

### Post by Confused Computer User on 2013-12-08
> **zkr300 said:**
> 
I have a 1.5 GHz Intel Celeron M with 1 GB RAM, 40 GB hard disk, and nvidea GeForce 5200 video card. As far as I know all drivers are updated - used sudo apt-get update.
My hardware is outdated and slow, but it works so I can't understand this.


Now that is some serious legacy hardware. I have a slightly newer Intel Celeron M with 2.2 GHz in an old Dell Bimensions box that still runs KDE using the onboard graphics. But that's a whole 'nother story

That being said I know from various trials and erorrs that when it comes to old systems and video cards, you're better off using a light distro with few to no expectations of doing anything even slightly graphicaly intensive.

According to this Askubuntu page: [How to install drivers for NVIDIA GeForce FX 5200 on Precise]("http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise")
there have been some issues with the propietery driver. In essence old cards such as yourselfs no longer recives regular support. While sad, you have to realize that Hardware manufacturers would run out of buisness if you kept using the same machine for more than a decade. So, if it doesn't break then they stop or reduce driver support in order to get you to upgrade your machine.

On a side note, I have given up on using linux with any type of video card other than Intel.

---

