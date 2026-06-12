---
title: "Authentication Rejected error with gksu _application_"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Belyel on 2006-09-01
Well I have some great troubleshooting times with linux.  today's particular error is undoubtedly caused by my tinkering with things I shouldn't be messing with.  I started by wanting to install gnomad so I would be able to manage my zen micro in Linux (one of a few more things keeping me from deleting WinXP).  However, I don't have internet on my laptop while I'm at work because I'm behind a proxy.  I followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=83401&highlight=update+proxy") trying to get to the internet through the proxy, but never got anywhere.  So I gave up on that avenue, and started following [this guide]("http://www.ubuntuforums.org/showthread.php?t=199250&highlight=howto+install+gnomad") to install gnomad.  As far as I know everything was still working on my system at this point.  I downloaded the source from the links in the tutorial, and checked the dependencies.  I then proceded to do the tedious process of downloading the debian packages for each of the dependencies and their dependants etc on my workstation then transfer them via pen drive to my laptop and dpkg them.  

The first problem I had was when I tried to install the libwww-perl and libhtml-tree packages.  For some reason each of them said it required the other, so neither would install.  So I extracted libwww-perl manually to the file system.  Still libhtml-perl wouldn't work, so I gave up on that and decided to persue the updating through a proxy a little more.  I edited my /etc/bash.bashrc as noted in the first guide I linked, and had done so before, and tried to update through the proxy.  It still didn't work.  Then I realized that my ethernet was turned off through network-admin, so I tried to run network-admin through the menu, it asked for my password, I entered it and got the error message> The entered password is invalid
Check that you typed it correctly and that you haven't activated the "caps lock" key
So I double checked, and I was able to *sudo* still, so I figured that it had to be something with that specific application. It is important to note that I undid all of the steps in the proxy guide, too.

However, I also tried using users-admin through the menu and got the same result.  In fact, I am unable to us any of the gui admin tools including: disks-admin, network-admin, services-admin, shares-admin, time-admin, or users-admin.  I searched the forums here and found someone suggesting that I set a seperate root password, so I use su passwd to set a root password.  I set it as the same as my user password for simplicity, but if I keep it I will change it for security.  Still didn't work.

I have tried running the applications from the terminal using gksu network-admin.  When I do this, I get an error in the terminal window in addition to the pop-up quoted above.  The error states: > GnomeUI-Warning **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I am able to run synaptic, although without internet it doesn't do me a lot of good.  I can also run other admin tasks than the ones listed above.  When using the test command ```
gksu /usr/bin/x-terminal-emulator
```I get the same error, but it does open a root terminal.  Likewise when I use gksu nautilus, I get an error in the terminal but it opens up nautilus in root.  gksu firefox works with a terminal error, too.

I'm almost literally pulling my hair out here.  I can still sudo stuff, and I think I'll be able to use apt-get and/or synaptic once I get internet again, but without network-admin, I'm not sure I can get internet again... Help!

PS: it's not really relevant, but at one point in trying to get this to work I had inadvertantly removed myself from the admin group and had to use my suse install (susu < ubuntu) to fix my groups so I was an admin again.  No net change though.

---

### Post by Nikos_M on 2006-09-01
As far as the problem of launching gui applications as root see this: [http://www.ubuntuforums.org/showthread.php?t=166863&page=2](http://www.ubuntuforums.org/showthread.php?t=166863&page=2)

---

### Post by Belyel on 2006-09-02
Well, this is an anticlimatic solution, but as soon as I got internet, I was able to sudo apt-get update and apt-get upgrade -f, I got about a dozen broken packages fixed and my problem was solved.  Just happy that Ubuntu can fix my stupidity sometimes.

---

