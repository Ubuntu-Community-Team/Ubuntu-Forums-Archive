---
title: "re-configure gdm"
date: 2007-01-19
forum: Desktop Environments
---

### Post by re-entity on 2007-01-19
I have a fresh installation of Edgy which I loaded on my hard drive while at work. I took it home and put the drive back into my box. While booting up, I received an error message saying that GDM is disabled.

I performed the following commands as per this old post of mine: [http://www.ubuntuforums.org/showthread.php?p=933170](http://www.ubuntuforums.org/showthread.php?p=933170) 

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

I selected ATI as my graphics processor type while re-configuring this. After I restarted GDM, the screen is blank. I can't get access to the terminal again. My only option is to shut the system down.

Is there a way I can reset GDM, this time to a generic setting?

My graphics card is an ATI Radeon 9600XT.

Thanks

---

### Post by dobroschi on 2008-04-11
Hi

Try reinstalling your ubuntu-desktop that might work.

[HTML]sudo apt-get install ubuntu-desktop[/HTML]

hope it helps

cheers

---

