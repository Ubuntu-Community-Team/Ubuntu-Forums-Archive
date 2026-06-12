---
title: "Xorg will not start after -f of some packages"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Psquared on 2005-11-09
I installed Enlightenment from one of the how-tos in this forum. It was working but I could not compile some of the modules. I started tinkering and found a thread which gave the following instructions. I already had these packages, but I thought perhaps I had the wrong versions. The error compiling had to do with locales.

This is what I did (with -f )

> First, you are going to need some debs direct from Debian (this is the part that I would do but I wouldn't recommend that you do but I would do anyway). 

Get:

libc6 from here 
libc6-dev from here 
libc6-i686 from here 
locales from here 
libvorbis0a from here
libextractor1 from here 

(Note: for all of the links above, scroll down to where it says "Download". There you will find versions for multiple architectures. Remember though, that this theoretically only works for x86, AMD64 and PPC. Maybe not even AMD64 and PPC.)

Then do 

sudo dpkg -i /location/of/libc6_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-dev_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/libc6-i686_2.3.2.ds1-22_i386.deb
sudo dpkg -i /location/of/locales_2.3.2.ds1-22_all.deb
sudo dpkg -i /location/of/libvorbis0a_1.1.0-1_i386.deb


[http://www.ubuntuforums.org/showthread.php?t=61488&highlight=enlightenment](http://www.ubuntuforums.org/showthread.php?t=61488&highlight=enlightenment)

Afterwards Synaptic told me I had 1045 broken packages. Like a dummy, rather than uninstall the packages I decided to reboot thinking it would clear up. Now xserver will not connect. (I am at work so I don't have the exact message, but I got a blue screen telling me to fix the xorg issues and then try to start GDM. I have no idea how to fix the xorg xserver issues.

Am I screwed? Is this fixable? I can get to a console and I have internet access using ethernet.

Next time I'll leave well enough alone. :( :(

---

### Post by Remmelas on 2005-11-09
Uninstall the debian packages, then use apt-cache search to find the Ubuntu equivalents and reinstall them.  Sounds like you'll have to do this from the command line.  That will at least get you back to Ubuntu specific X packages, it will also fix the broken packages message.

---

### Post by Kyral on 2005-11-09
Yah....mixing Debian packages is nasty....

---

### Post by Psquared on 2005-11-09
[QUOTE=Remmelas]Uninstall the debian packages, then use apt-cache search to find the Ubuntu equivalents and reinstall them.  Sounds like you'll have to do this from the command line.  That will at least get you back to Ubuntu specific X packages, it will also fix the broken packages message.[/QUOTE]

I tried that. The debian packages won't uninstall because of dependencies. I guess I'm screwed. I'd love to try and fix it, but I think I'll just reinstall fresh. All I will lose are some emails and music files. Most of my docs and important stuff I put on my jumpdrive. 

Unless someone can think of a way to get the deb stuff off and reinstall the Ubuntu stuff without reinstalling the OS.

---

### Post by Psquared on 2005-11-09
Or, if someone can think of a way I can create a partition to copy my mp3 collection to that a reinstall won't erase. ](*,)

---

### Post by RAOF on 2005-11-10
You should be able to 
```
sudo dpkg -r libc6
```
etc, forcing if necessary, shouldn't you?  Then apt-get install the ubuntu versions.

---

### Post by Psquared on 2005-11-10
[QUOTE=RAOF]You should be able to 
```
sudo dpkg -r libc6
```
etc, forcing if necessary, shouldn't you?  Then apt-get install the ubuntu versions.[/QUOTE]

I'll try again, but it didn't work before.

Thanks for the idea.

---

