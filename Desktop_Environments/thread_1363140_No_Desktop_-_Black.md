---
title: "No Desktop - Black"
date: 2009-12-24
forum: Desktop Environments
---

### Post by TopEnder on 2009-12-24
G'Day All & Thanks in advance,  
Had a problem in closing down the computer normal exit method did not work, so I powered off the computer. Tried to boot-up all appeared normal with Grub2 until where it should display my Desktop.  Instead of the normal Desktop I got a black Desktop with a Terminal window top left corner of the display.

I checked using gksudo nautilus to see what could be displayed also checked to see id the Gnome Desktop packages were installed and still in archives.  Tried sudo restart gdm and Ctrl-Alt-F1 & Ctrl-Alt-F7, but things just keep going around in circles back the the black Desktop with a Terminal window.  I prefer not to go through re-installing 9.10 again as all seems to be in place and working when I can access them.  Any guidance and help will be appreciated.  TopEnder

---

### Post by TopEnder on 2009-12-25
Resolved the problem by what was suggested in the following similar posts:
crisB111 - Re: Broken Karmic System,  and
and
duanedesign - Re: "The GDM user 'gdm' does not exist."
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```
and
```
apt-get dist-upgrade
``` 
The above reinstalled may packages I had previously remove trying to make a more streamline system as many I never used like Firefox & f-spot, maybe I'll just remove the packages until I find a safe way to completely remove them.

---

