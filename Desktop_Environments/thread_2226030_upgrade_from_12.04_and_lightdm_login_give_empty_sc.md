---
title: "upgrade from 12.04 and lightdm login give empty screen"
date: 2014-05-24
forum: Desktop Environments
---

### Post by manitou2 on 2014-05-24
I upgraded to 13.04 from 12.04.  I run lightdm.  When I login now, i just get a color splash screen and an arrow moves with the mouse but i don't have any of my desktop icons and such. I tried switching to gdm, but I get nothing from gdm.  (I just added fvwm-crystal as an optional  lightdm desktop, and that lets me login to an fvwm desktop).  how do i get the lightdm/gnome desktop working again.  I've looked at several posts with similar problems, but have found nothing that fixes the problem.

in /var/log/lightdm
 x-0.log:modprobe: ERROR: could not insert 'nvidia_304': No such device

what other error logs do i need to investigate?  

everything was working with 12.04

---

### Post by dannyboy79 on 2014-05-24
can you go to tty1 and remove all traces of the nvidia driver? it's always critical to disable any propritary drivers prior to upgrading your distro (at least that's how i do it always) once you've completely removed all traces of the nvidia driver, then restart your system and hope that it uses neouveu and you can at least get to a GUI desktop

---

### Post by manitou2 on 2014-05-24
Can you be more specific about how I  "remove all traces" ?
is there a command to show if system is uing neouveu?

thanks

---

### Post by dannyboy79 on 2014-05-24
google how to remove the nvidia driver. should be something along the lines of this
```
sudo apt-get remove --purge nvidia-*
```
if you can't even boot into your desktop environment than you aren't using neouveu.

UPDATE: i found a good guide [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by manitou2 on 2014-05-25
OK,  I've made some progress.  just for the record, I upgraded further to 14.04, but that didn't help my desktop problem.  I did the 
 apt-get remove --purge nvidia-*
and added nouveau to /etc/modules.
  The following managers still failed: Ubuntu, GNOME, GNOME compiz.  black screen. and in some cases had to cycle power!

However, gnome metacity seems to be working, though i got some pop-ups wanting to report system problems ...

thanks for the help, hopefully, things will continue to run... and there is always FVWM (which I used in an earlier life)

PS -- lspci shows i have a NVIDIA Corporation NV37GL on dell precision 370.  Any recommendation for a graphics board that is supported by Ubuntu (I don't need anything fancy, e.g., no gaming)

---

