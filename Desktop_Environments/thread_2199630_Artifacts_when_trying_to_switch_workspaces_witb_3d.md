---
title: "Artifacts when trying to switch workspaces witb 3d cube and window is open"
date: 2014-01-14
forum: Desktop Environments
---

### Post by woohoomoo2u on 2014-01-14
Long title... P.S witb=with
I'm on ubuntu 13.10, nvida gt650M/standered bumblebee...
When I have a window open, or windows, and try to do the 3d switch with my mouse, it leaves lots of artifacts over the place or blacks out everything but I small square.
Like so ( [http://www.youtube.com/watch?v=3GkUv6TqP0U](http://www.youtube.com/watch?v=3GkUv6TqP0U) ) and the screenshoot where I could...
[ATTACH=CONFIG]249510[/ATTACH]  [ATTACH=CONFIG]249511[/ATTACH]

---

### Post by woohoomoo2u on 2014-01-17
Okay, i figured this out on my own... I felt like posting it ou there.  I used Nvidia Prime. Ubuntu 13.10
This is basiclly how to setup a nvidia 650m (or other optirun) and intel 4000 (or other suppported)
1. Purge everytihng you did or Resinstall the system (easyist if home is seprate partition)
1a.sudo apt-get purge bumblebee*
1b. sudo apt-get purge libvdpau-va-gl1
2. Add ppa [https://launchpad.net/~joern-schoenyan/+archive/nvidia-prime-backport](https://launchpad.net/~joern-schoenyan/+archive/nvidia-prime-backport)  (sudo add-apt-repository ppa:joern-schoenyan/nvidia-prime-backport)
3. sudo apt-get update
4.Install lightdm (modifided), nvidia-settings, screen-resolution-extra, xserver-xorg-video-intel, and nvidia-prime.
5. sudo apt-get install nvidia-319 nvidia-settings-319
6. sudo update-grub (not neccisary but just incase)
7. Restart or sudo reboot
Opitional
Use 
/usr/bin/enable-nvidia
to make a .desktop to switch to nvidia and

/usr/bin/enable-intel
to use intel
Done!

---

