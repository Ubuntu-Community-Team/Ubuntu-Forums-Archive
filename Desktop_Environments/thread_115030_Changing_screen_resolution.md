---
title: "Changing screen resolution?"
date: 2006-01-09
forum: Desktop Environments
---

### Post by joshotter on 2006-01-09
Hi, I just installed ubuntu 5.10 and am also new to the whole linux thing.  I was wondering on how to change the screen resolution.  When I go to change it there is only one option present.  Ive been searching around and cant seem to find any help.  Also if anyone can tell me a simple way to install software I would appritiate it alot.  Im trying to get limewire but after it downloads I cant seem to find/install it.  Thanks for any help in advance.

---

### Post by shade11 on 2006-01-09
The easiest way to install software is apt-get. Also an easier way is Synaptic. You can also install Debain packages that you can decompress and it installs automatically. RPM files can be converted to debain packages and installed from there with alien.

In the terminal you can do this:

Install alien

```
sudo apt-get install alien
```

use alien to convert RPM files

```
sudo alien /link/to/rpm/file
```

and then go to your home folder to find the file and type in:

```
sudo dpkg -i /link/to/deb/file
```

Which installs the deb file.

You can also install from shell source which gets complicated. There is more than one way to install from shell source. And I have problems installing from shell so dont ask me.

You might want to get automatix ([http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)) It will help with some stuff you can install.

As for screen resolution i cant help you there because I am running Windows at the moment. And i don't remember how to. But with a community this huge, someone is bound to help you. you might also want to try the [Ubuntu Wiki]("http://wiki.ubuntu.com/") for help.

---

### Post by Maelgwyn on 2006-01-10
If there's only one option available for your screen resolution, then I'd imagine that means that the other resolutions aren't supported by your computer/monitor... You may need to update your drivers!

What gfx card are you running? Is it a CRT or flat-screen monitor?

---

### Post by brohan on 2006-01-10
I've ran into the same issue once or twice, oddly enough the solution for me was to restart xwindows (Ctrl-Alt-Backspace) it until it worked. Suprisingly I got up to a higher resolution.

Though if you're looking to change your screen resolution look first in System > Prefrences > Screen resolution before you go start mucking around with X windows.

---

### Post by benco on 2006-01-10
I had a similar problem : at the end of the installation, the XServer starts with the correct resolution (1024*768) but after the next reboot, it starts in 640*480 and I have no other choice in the resolution settings screen.
First, I suspected the post-install updates. So I reinstalled Ubuntu and rebooted just after I got Gnome running in 1024*768. and at the next reboot ... ka-bam ... 640*480 again.
So I tried to manually reconfigure xserver-xorg and it worked fine. I now have the best resolution my card/screen can offer.
To do that, just kill gdm with :
> 
# sudo /etc/init.d/gdm stop

Then, in text mode :
> 
# sudo dpkg-reconfigure xserver-xorg

Just hit enter on every screen to accept the default option.
And restart X (or reboot).

Hope it will help !

---

### Post by Gustav on 2006-01-10
For the best result look at this: [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973) .

You need to know your monitor specs for that though, but they are mostly easely googled.

---

### Post by joshotter on 2006-01-29
I will give all of these a try.  But I did go back to windows temporarly because I was forced too!  I bought a mp3 player and had to load songs and wasnt patient enough to give it a shot in ubuntu.  But now that I have that done I'm going to try again since I love everything except not knowing how to install software which Im sure I will get down eventually.  But thanks for the help and any more would be appreciated.  Is there a guide or easier way to software installation anywhere?

---

