---
title: "Minimal Desktop for Ubuntu 15.10 help please"
date: 2016-06-03
forum: Desktop Environments
---

### Post by pappo2 on 2016-06-03
I have an older PC that I use for a home NAS primarily.  I usually use the command line only for admin, but want to show my children how Ubuntu can be a regular desktop
Currently with my PC, Compiz is taking up 56% of the CPU and slows all desktop activities.
I would appreciate a link to how to change my desktop, remove Compiz and the 15.10 default desktop, and go to a more minimal desktop environment.
I have read a little about Xubuntu and Lubuntu, but have not tried them yet.

Any help would be appreciated.

---

### Post by Bucky Ball on 2016-06-03
Yes, you can try the desktop environment of either Xubuntu or Lubuntu without installing the full OS. Simply install xfce4 for the Xubuntu DE, logout, choose the xfce4 session from the Sessions menu (will be there somewhere on the login screen). If you don't have a DE already, you probably won't need to choose. To install the Lubuntu DE, install lxde. Same procedure. 

You might be interested in something like Xubuntu-core. I use it on all my machines now, low and high spec, and love it as minimal and I only need to install what I actually use. Here's some links for Xubuntu-core.

[http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

You can also do a minimal install and add whichever desktop you like, but if you use xfce4, it will end up pretty much like Xubuntu-core anyway. 

Hope that helps and good luck.

(PS: To my knowledge, neither of these desktop environments require or use Compiz. I am using Xubuntu-core and it is not installed by default. More expert heads can probably give more specific details on that. I haven't used Ubuntu in years and have never used Unity, so ...)

---

### Post by egeezer on 2016-06-05
Agree with Bucky Ball about Xubuntu Core; I'm running the 16.04 version on 3 machines (2009 era and up).  Compiz is not required, but I install it for the visuals - this setup gives me maximal eye-candy at minimal load.

---

### Post by sudodus on 2016-06-05
There is another alternative, if the only purpose of the graphical desktop is demo (to show your children).

Do the demo from a live session - boot from Lubuntu, Xubuntu or Ubuntu MATE - download the desktop iso files, flash them into a USB pendrive, try them and show the children the system you like the best.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

-o-

Keep the server light, and use no desktop environment (unless you need it for some server task). Notice that 15.10 reaches end of life in July, so prepare to upgrade to 16.04 LTS near the end of July. This new version has long time support, 5 years for Ubuntu Server

---

### Post by Bucky Ball on 2016-06-06
> **sudodus said:**
> This new version has long time support, 5 years for Ubuntu Server

Xubuntu and Lubuntu have three years LTS support. No idea about Mate.

---

### Post by oldrocker99 on 2016-06-06
> **Bucky Ball said:**
> Xubuntu and Lubuntu have three years LTS support. No idea about Mate.

Ubuntu MATE has a three year LTS supoprt, just like Xubuntu and Lubuntu.

---

### Post by QDR06VV9 on 2016-06-06
> **oldrocker99 said:**
> Ubuntu MATE has a three year LTS supoprt, just like Xubuntu and Lubuntu.

+1 And here from Whimpy
> WimpyProject Leader

Let's clarify this. Traditionally Ubuntu proper has a 5yr LTS and will do again for 16.04. Most other flavours only apply for a 3yr LTS.

16.04 is our first properly official LTS and after some discussion with members of the Ubuntu Technical Board, we've decided to follow what most other flavours do which is a 3yr LTS.

What does this mean? We will support Ubuntu MATE 16.04 upto the 16.04.5 release. After that, the Ubuntu MATE bits won't get updates and fixes but the underlying Ubuntu base will. &#65279;
Source:  [https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/9](https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/9) 
Regards

---

