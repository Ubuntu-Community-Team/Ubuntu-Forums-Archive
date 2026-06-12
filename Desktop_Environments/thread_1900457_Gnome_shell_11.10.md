---
title: "Gnome shell 11.10"
date: 2011-12-26
forum: Desktop Environments
---

### Post by Randymanme on 2011-12-26
Hello,  
 

 I'm following instructions at  [http://blog.flexion.org/2011/12/09/gnome-3-shell-ubuntu-11-10-oneiric/](http://blog.flexion.org/2011/12/09/gnome-3-shell-ubuntu-11-10-oneiric/), to replace Unity with Gnome Shell.  At some point in the process, folks wanting to accomplish that are directed to use the following command:
 

 sudo apt-purge unity unity-2d unity-2d-launcher unity-asset-pool unity-common unity-greeter unity-lens-applications unity-lens-music libunity-misc4
 

 Well, here's what I get:
 

 randyman@Gnome11:~$ sudo apt-purge unity unity-2d unity-2d-launcher unity-asset-pool unity-common unity-greeter unity-lens-applications unity-lens-music libunity-misc4 
 [sudo] password for randyman:  
 sudo: apt-purge: command not found 
 randyman@Gnome11:~$  
 

 Before I make any newbie assumptions, let me just ask, should that be “sudo apt-get purge” for complete removal or is “sudo apt-get remove”  is what's intended?  Does Unity have dependencies that might be needed by Gnome Shell?
 

 Of course I've looked for an answer, e.g., [http://ubuntuforums.org/showthread.php?t=1100838](http://ubuntuforums.org/showthread.php?t=1100838) **How to remove with apt-get (questions).  ****But I don't know what's appropriate without knowing what's intended.**
 

 As always, any help will be much appreciated.

---

### Post by cybergalvez on 2011-12-26
using purge will remove all the configuration options as well as the packages, remove only removes the packages while leaving any configuration files.

With that said I would not remove unity 2d or 3d I would simply add gnome-shell and use the session manager to select gnome rather than unity, this give you a fall-back should something go wrong, or an additional shell should you or another user ever want to use it

---

### Post by Randymanme on 2011-12-26
Since the tutorial said, "sudo apt-purge . . ." instead of "sudo apt-remove . . .," I assume it to have meant, "sudo apt-get purge . . .."  I tried it and gnome shell works just fine, more or less.

---

### Post by Randymanme on 2012-02-15
The recently released, stable, Cinnamon Desktop 1.2 is even better.  Not only do you get Cinnamom, but it also drags in Gnome Shell and Gnome Classic as dependencies. 

See it at: [http://www.youtube.com/watch?v=-yPqR-nKsE4](http://www.youtube.com/watch?v=-yPqR-nKsE4)

Get it at: [http://www.webupd8.org/2012/01/cinnamon-12-released-with-desktop.html](http://www.webupd8.org/2012/01/cinnamon-12-released-with-desktop.html)

---

