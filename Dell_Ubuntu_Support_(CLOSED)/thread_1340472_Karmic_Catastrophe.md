---
title: "Karmic Catastrophe"
date: 2009-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by laurence91 on 2009-11-28
Hi there,

I updated form jaunty and have not been able to boot the system, i assumed it was an xorg.conf issue but iv rolled back to the last working version and still the problem exists. It wont boot past the splash screen and is unresponsive, it gives a white screen which fades to black.

I noticed the grub menu has not been updated and it is still selecting 8.10, there is no 9.10 option. Can anyone help as to how i can repair the grub menu? I have run the 'repair grub menu option' in the recovery startup to no avail.

Cheers

Laurence


#######SOLVED#########

must have not selecyed update grub when i installed!!! feel a little stupid but this guide explains what to do if anyone else has the same issue

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

 

dell xps m1530 nvidia 8600m gt

---

### Post by laurence91 on 2009-11-28
Secondly - after running #sudo update-grub

it finds two -

/found kernel /boot vmlinuz-2.6.31.15-generic
/found kernel /boot vmlinuz-2.6.27.7 - generic

but if i bring up my grub/menu.lst     I only see

ubuntu 8.10, kernel 2.6.27-7-generic

I cant understand why it hasnt updated and wonder if this is the root of the problem, ie im trying to boot a system which has been replaced?

cheers, any help most appreciated - naturally this happens whilst im trying to write up my phd thesis.... typical

---

