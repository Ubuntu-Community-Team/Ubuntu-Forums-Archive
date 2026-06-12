---
title: "Problems with screen resolution"
date: 2005-03-29
forum: Desktop Environments
---

### Post by Diego F. on 2005-03-29
Hello. This is my first post and this is the first Debian based distro I install. I'm trying it in my Centrino Laptop. The installation was OK, but I have a problem with the screen resolution.

My screen is 15.4" and the best resolution is 1280x800, but if I select that one in Ubuntu, the letters are dotted and very difficult to read. I have to select 1152x768. 1024x768 is also 'readable', but the aspect is better with 1152.

Do you know how can I select 1280 resolutions?

I'm downloading KDE rigth now just to see if it works.

--

Regards,

Diego F.

---

### Post by erkki70 on 2005-03-29
Have you tried to reconfigure your X server and see if the 1280x800 resolution is available?

What is the Ubuntu version you installed? 
I assume it's Warty (XFree86) and not Hoary(Xorg)?

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops]("http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops")

Search for "widescreen" on this page and you'll probably find necessary infos on how to configure.
Some people are reporting it works out of the box other not.
Another thread:

[http://www.ubuntuforums.org/showthread.php?t=5464&highlight=50-185]("http://www.ubuntuforums.org/showthread.php?t=5464&highlight=50-185")


There are loads of entries if you search the forums with "1280x80" btw ;-)
Hope this helps.

---

### Post by Diego F. on 2005-03-29
I'm using Warty and I have a Toshiba M30 series laptop. I was searching but I found posts refering xorg.conf. I didn't know it was only for hoary. Thank for that info ;)

---

### Post by erkki70 on 2005-03-29
Ok.
I think you should try to reconfigure your X server.
This is very well documented on the forums.
It is always a good idea to backup your existing configuration file in case something goes wrong so you can restore easily.
Anyway, before manually editing your XF86Config file IMHO you can try in a console

 ```
sudo dpkg-reconfigure xserver-xfree86
``` 

This will regenerate a config file, and you just have to answer the questions about your ATI card, the modules you want, keyboard, mouse then you'll have a list of available resolution to choose from and you should find 1280x800 in there I guess.
It's pretty straight forward and the default choices are the good ones usually.
If it doesn't work you'll probably have to edit manually and make a previous backup of the config file.

Again, all these steps are really well documented on the forums.
Good luck.

---

### Post by Diego F. on 2005-03-29
It's solved  \\:D/ 

I was following the tweaking post and installed nvidia drivers. After rebooting the 1280x800 resolution was selected and it's working OK now.

Thanks.

---

