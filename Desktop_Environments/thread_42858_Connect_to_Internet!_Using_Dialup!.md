---
title: "Connect to Internet! Using Dialup!"
date: 2005-06-19
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-06-19
Hello!


  I am running 5.04 of Ubuntu GNU/Linux.

  I am also using AOL! (no Linux software)

  How can I use my ext. Modem to connect to the internet!? And how do I turn my modem's speaker on, so that I hear what number it is dialing!?

  Thank you and regards!


-

---

### Post by netrattler on 2005-06-19
Well there is 2 dialers for AOL that I know of but have never tried them since I don't use AOL, first one is called penggy which is included in the universe repo. Another one not included in Ubuntu is called peng you can find it here but you will have to compile it. So you might want to try the one in universe first.

[http://sourceforge.net/projects/pengaol/](http://sourceforge.net/projects/pengaol/)

Joe

---

### Post by Prudentissimus on 2005-06-20
[QUOTE=netrattler]Well there is 2 dialers for AOL that I know of but have never tried them since I don't use AOL, first one is called penggy which is included in the universe repo. Another one not included in Ubuntu is called peng you can find it here but you will have to compile it. So you might want to try the one in universe first.

[http://sourceforge.net/projects/pengaol/](http://sourceforge.net/projects/pengaol/)

Joe[/QUOTE]
 how do i install penggy of universe repo???

what is universe repo??

---

### Post by netrattler on 2005-06-20
Here is a link on how to add the repositories to your /etc/apt/sources.list. Basically the repositories hold the software that allows you to download and install it to your computer.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Once you have added the repos then all you have to do is go to Applications -> System Tools -> Terminal -> than type sudo apt-get install penggy
or if you would like to use the graphical version of Apt you can go to System -> Administration -> Synaptic Package Manager.

Other apt commands are 

sudo apt-get remove appname (Will uninstall software)
sudo apt-get update (Will update your repositories)
sudo apt-get upgrade (Updates your software)

Joe

---

