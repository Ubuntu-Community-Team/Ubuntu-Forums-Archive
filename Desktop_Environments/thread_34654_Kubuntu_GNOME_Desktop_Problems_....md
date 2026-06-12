---
title: "Kubuntu GNOME Desktop Problems ..."
date: 2005-05-15
forum: Desktop Environments
---

### Post by giosico on 2005-05-15
I am new to all of this and went with kubuntu but wanted to check out GNOME as well.  So after the kubuntu install I installed GNOME.  When I log with GNOME the desktop has nothing on it except a blank "panel".  I can not even figure out how to logout.  The only way to get back to KDE that I can figure is to get a terminal up (available via right click) and sudo reboot.

In short the GNOME desktop does not come preconfigured to look like the screen shots ...

Can anyone help with this?

I am thinking I should uninstall GNOME and then reinstall?
Or install ubuntu then install KDE instead of vice versa like I did

any help is much appreciate ...
as I am new please provide command line instructions for any advice

cheers

John

---

### Post by giosico on 2005-05-15
I tried a

sudo apt-get remove ubuntu-desktop
reboot
sudo apt-get install ubuntu-desktop

and not only is the problem still there ... all my little panel tweaks trying to get gnome to work are still there too ...

any help would be much appreciated

thanks

---

### Post by britbrian on 2005-05-15
giosico

Ubuntu is much more stable than Kubuntu, therefore its probably better to install Ubuntu first & Kubuntu on top if you can. Its worked well for me. The clearlooks theme makes GNOME look very attractive.

---

### Post by giosico on 2005-05-15
Thank you for taking the time to reply.  I imagine that the KDE people would make a KDE install on Kubuntu work well and that is always an option for me.  I was just trying to avoid having to download another 500megs to try it out. 

As for one being more stable than the other.  I believe they are both the same with just different desktop environments installed.

What I need is someone who has successfully installed GNOME on Kubuntu to give me some advice.

Thank you,

John

---

### Post by Terracotta on 2005-05-16
[QUOTE=giosico]I tried a

sudo apt-get remove ubuntu-desktop
reboot
sudo apt-get install ubuntu-desktop

and not only is the problem still there ... all my little panel tweaks trying to get gnome to work are still there too ...

any help would be much appreciated

thanks[/QUOTE]

If you remove the meta-pakcage ubuntu-desktop you don't remove the applications used by the ubuntu-desktop, you just remove a layer. So everything else that was install during ubuntu-desktop install, remains. To remove ubuntu, you'ld have to remove all the apps and libs that were installed.

---

### Post by giosico on 2005-05-16
Thanks for the reply.

I am confused ...

I got the ubuntu desktop with an install command ... shouldnt a remove command then remove everything that was initially installed?

But that is not what I need help with ... What I need help with is that the GNOME desktop does not have any default panels ... like the windows xp start menu or kde start menu and there is no clock ...

The screen shots show all this to be present I think ...

Thank you

---

### Post by Ray Hamilton on 2005-05-16
Hi 

I have done what you are trying, ie downloaded Kubuntu, then installed Gnome. I am away from my home computer at the moment but try clicking on the foot/logo.  This should give access to a menu.  Also try right click for adding things to the panel. 
Let me know if you get a similar problem to the one I have: sudo password works from a terminal, but not from the menus.

---

### Post by ddocta on 2005-05-16
I have actually done both, installed Kubuntu on Ubuntu and installed Ubuntu(GNOME) on Kubuntu(KDE) and I must say that Ubuntu is much more stable.  I got many hardware and other related errors when I started with Kubuntu.

I know this doesn't exactly answer your question, but if you have the time and haven't done too much configuration with the current install, it may be worth a shot.

---

### Post by britbrian on 2005-05-16
giosico
If your Gnome panel is still blank, right clicking it should allow you to first add the Gnome menu then everything else & do panel preferences. IMHO this doesn't bode well & you could have more configuring than expected to catch up with the quality of an Ubuntu based install.

I had same problem when I recently installed Gnome 2.8 in the PCLinuxOS KDE based distro. Worse, that Gnome install still has problems like an empty Panel->App-Launcher list so I can only put apps in the panel by dragging them from the App menu. So I came to Ubuntu for a Gnome that works.

---

### Post by giosico on 2005-05-16
Thanks for all of your replies guys ... but I could not put more time into this so have decided to give up and stick with KDE ... I might try creating a new user which will probably fix this problem as it did with a slightly similiar KDE problem

---

