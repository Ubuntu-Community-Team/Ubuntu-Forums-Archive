---
title: "How to change ubuntu logo icon of left application menu"
date: 2011-12-30
forum: Desktop Environments
---

### Post by mylinux2012 on 2011-12-30
Hi Guys 

i use Ubuntu 11.04 Desktop Edition and I have edited grub.cfg but
I would like to change ubuntu logo icon of left application menu with my own one.
Another one is how to customize the gdm and usplash with my own.
Then when I installed remastersys to make own distro, I could not install it properly.

Thanks alot

---

### Post by grahammechanical on 2011-12-30
One way to do this is to search through the folders in FileSystem looking for the icons and images. You then need to replace the default icons and images with ones of your own creation giving them the same names as the original. Some icons come in more than one size. You would need to replicate all the sizes.

For example, if you go to usr/share/icons/unity-icon-theme/places/22 and /24 folders you will see what look like the Ubuntu icon that appears at the top of the Launcher in 11.10. I am not using 11.04. So, you will have to look for yourself. Just as I have just done.

Another way, is to work out what scripts are used to load the icons and images and edit those scripts to point to the icons and images that you have created. 

The responsibility is yours.

Edit: Likewise in 11.10 if you go to etc/lightdm/unity-greeter.conf and open that file in Gedit you will see these lines:

> [greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png

In 11.04 you will have to find something similar for GDM and then either edit the configuration file to point to the background image and logo of your choice or replace the two png images with those you want but giving them the same name as the originals.

I am using 12.04 development branch and I have installed Simple LightDM Manager. That has allowed me to change both the Greeter background image and the logo. It puts copies of your chosen images in its own folder and then edits the unit-greeter.conf to point to the Simple LightDM Manager folder.

Can you see how it is done?

Regards.

---

### Post by NaturistGirl on 2012-03-11
I'm trying to do this as well. I'm using Ubuntu 11.04.

~ Lexi

---

