---
title: "Precision M6300 screen not detected"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by mysticman on 2007-10-24
I just bought a Precision M6300 and installed Feisty (32 bit Xubuntu).  I'm dual booting with Vista Ultimate.  When Xubuntu boots it goes to a text login & says that it cannot detect the screen so can't run xorg.  I've no idea what to do... Please help.  I've tried the dpkg-reconfigure and asked it to detect the screen but this still doesn't work.

---

### Post by sakisg on 2007-11-22
have any news about ? I am facing the same issue

Thanks 
Sakis

---

### Post by leub on 2007-12-01
I have a DELL precision with NVIDIA Quadro FX1600M (i Think the ID is 040D )

I can launch Ubuntu Live, but i've no sound and i can't install NVIDIA linux driver....
I tried this one:
NVIDIA-Linux-x86-100.14.19-pkg1.run

But there was an error....
even if in the supported products list there is:

Quadro FX 1600M 	0x040D

I don't know how to resolv this problem.....I can't wait more with VISTA!!!:(

Please Help!!!

If someone has the solution to install Gusty Gibons on a DELL precision 6300 with sound and Compiz, please contact!! :)


PS: I already test the proprietary NVIDIA  pilot from Ubuntu but i did not work.....
I think there are some module to activate...
after seing pcimodules, i tried to add them to my Xorg conf, the result was better, but my Precision 6300 were working anormal slow....
...and when I run compiz- (the windows did not display entirely)....


If some one has an Xorg.conf ...and an idea...

---

### Post by undolaure on 2007-12-16
Hello,

I'm going to buy a Dell Precision 6300 and want to know if you have solved your troubles about hardware detection with this laptop. If you have done some research and you can share some useful links, this will be great.

Thank you,
Raimon

---

### Post by mopo on 2007-12-17
Hi,
   Just went through this.  To get the screen detected I needed to edit the grub boot options and remove the "quiet" and "splash" options then the screen got detected properly.

  For the sound, you need to enable that backport modules, as shown here:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I used Method G, just install the package, no need to edit any files for this machine.

Finally, I kept getting crashes with the nvidia modules and OpenGL applications.  I had to install the latest Beta driver from the nvidia site:

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

At this time thats 169.04.

Follow the instructions there on removing the Ubuntu version.

Then you need to do this to get the new driver to work:

[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2907](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2907)

Hope that helps.

Only issue I have is stability with the bluetooth mouse.

---

### Post by luckyluca on 2008-01-28
Hi Mopo,

Could you please write done a brief step-by-step guide on how to upgrade the nvidia drivers ? 
(I'm a linux newbye and not sure on what to do even after having had a look at the pages you pointed to)

Thanks a lot!
another fellow m6300 user
Luca

> **mopo said:**
> Hi,
   Just went through this.  To get the screen detected I needed to edit the grub boot options and remove the "quiet" and "splash" options then the screen got detected properly.

  For the sound, you need to enable that backport modules, as shown here:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I used Method G, just install the package, no need to edit any files for this machine.

Finally, I kept getting crashes with the nvidia modules and OpenGL applications.  I had to install the latest Beta driver from the nvidia site:

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

At this time thats 169.04.

Follow the instructions there on removing the Ubuntu version.

Then you need to do this to get the new driver to work:

[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2907](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/#comment-2907)

Hope that helps.

Only issue I have is stability with the bluetooth mouse.

---

### Post by luckyluca on 2008-01-31
never mind, sorted.
Luca

---

