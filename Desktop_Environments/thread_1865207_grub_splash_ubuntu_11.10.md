---
title: "grub splash ubuntu 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by boblizar on 2011-10-19
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

first since we are from space grab a picture of a nebula.

alt + f2

gnome-terminal

run

then feed this code to your terminal
```

wget http://img819.imageshack.us/img819/5632/nebulae.jpg
mv $HOME/nebulae.jpg $HOME/nebula.jpg
sudo mv $HOME/nebula.jpg /usr/share/images/grub/nebula.jpg

```

if it says no dir for /usr/share/images/grub/ issue (for older ubuntus)

```

sudo mkdir /usr/share/images/grub

```

(older versions of ubuntu will need gediting of /etc/grub.d/05__debian_theme to point to the /usr/share/images/grub/nebula.jpg image)

enter your root password to place the nebula in your grubs boot images....

now were going to remove the old desktop base script and replace it with a more stellar one....

do this block of code to remove....

```

sudo rm /usr/share/desktop-base/grub_background.sh

```

go god mode

```

sudo su

```

write new script 4 background on boot

```

cat > /usr/share/desktop-base/grub_background.sh << EOF
WALLPAPER=/usr/share/images/grub/nebula.jpg
COLOR_NORMAL=light-green/black
COLOR_HIGHLIGHT=green/light-gray
EOF
update-grub
exit

```

on older ubuntus if you gedited the previous blocks values in 05_debian's file your going to need to issue 

```

sudo update-grub

```

i had to add
GRUB_GFXMODE=1280x1024
to
/etc/default/grub
or else it would just show a black screen.

and press return to exit god mode, reboot to test....  it is a 1280x1024 image, and might require editing a file i already edited to change the menu size to fit the image.  but for the most part this was a nagging hidden system when trying to edit /etc/grub.d/05_debian* only to have a strange variable over ride what you set.

and this is what you get when bob punishes your boot loader settings

[IMG]http://img819.imageshack.us/img819/5632/nebulae.jpg[/IMG]

---

### Post by subehsharma on 2011-11-10
does it work with Xubuntu 11.10 as well?

---

### Post by Mark Phelps on 2011-11-10
> **subehsharma said:**
> does it work with Xubuntu 11.10 as well?

If you're uncomfortable messing with command line entries, especially as root, there is a safer way to do this.  Follow the instructions in the link below to install Grub Customizer and use that to Browse to the folder containing the picture file:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by boblizar on 2011-11-27
this should be xubuntu, kubuntu, edubuntu, and ubuntu compatible....  so yes (and i was running xubuntu at the time i generated this but have moved back to regular ubuntu)

---

### Post by jcoles on 2012-01-07
Will this method display a background image that is visible from power-on to Login screen? 

So far, I have been able to display a background image only if I press Shift to display the grub menu. After making my selection, the background stays in place until the Login screen appears, but no boot-up messages ever display on top of the background. 

If the grub menu remains hidden, the screen is black from the Grub beep until the Ubuntu login screen appears, about 40 seconds later. 

Have I misunderstood what can be done with the Grub splash feature?

---

### Post by boblizar on 2012-01-27
if you have multiple kernels installed grubs splash will show up with selections for it, or if you installed along side of windows this will show up....  default ubuntu only with only 1 kernel, fresh install wont show this until you a get windows, or b get another kernel.  you can turn this feature on somewhere in the hidden settings regardless to show the splash, but most users would want to keep the splash to auto select whats loading and make it load all the quicker, rather than waiting for a user selection/time out.....

this image actually might be broken for bootup, ive never tested this loop.

---

