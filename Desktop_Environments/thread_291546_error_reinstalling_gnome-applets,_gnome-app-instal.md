---
title: "error reinstalling gnome-applets, gnome-app-install"
date: 2006-11-02
forum: Desktop Environments
---

### Post by Belyel on 2006-11-02
I'm using Dapper after a botched upgrade to Edgy.  And I'd like to preface this with an admission that I definitely know that I caused the problem.  I was in /usr/bin and accidentally used sudo rm *.* thinking I was in another directory.  Whoops.  I'm not sure what files I deleted, and they are permanently gone I think.

The error I'm getting is when I tried to add/remove... on the gnome applets menu, it says "Could not launch menu item.  Details: Failed to execute child process "/usr/bin/gnome-app-install" (No such file or directory)."

So I tried to reinstall gnome-app-install to no effect.  I also thought I should reinstall the other gnome-applet packages, but they, too, failed.  I tried sudo apt-get remove --purge for all the relevant packages.  They are downloaded to my computer, but when I try to install, I get this:

> stephen@pimpline-lx:~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/393kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
(Reading database ... 116788 files and directories currently installed.)
Preparing to replace gnome-applets 2.14.3-0ubuntu1 (using .../gnome-applets_2.14.3-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
/var/lib/dpkg/info/gnome-applets.postrm: /usr/sbin/update-gconf-defaults: /usr/bin/python: bad interpreter: No such file or directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: /usr/sbin/update-gconf-defaults: /usr/bin/python: bad interpreter: No such file or directory
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.14.3-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: /usr/sbin/update-gconf-defaults: /usr/bin/python: bad interpreter: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.14.3-0ubuntu1_i3

I haven't found any other thread with this problem, so I think I must be the only guy dumb enough to erase his /usr/bin folder contents.  I'll keep trying to find the solution, too.  Thanks.

---

### Post by Belyel on 2006-11-06
Ok, I'm still having this problem.  I looked at other posts where the poster (or friend) had deleted /usr/bin and had to reinstall linux.  However, my apt-get is still working, dpkg is still working, synaptic, etc are still working.  I've reinstalled python, dpkg, ubuntu-desktop, and several other possibly related packages, but still cannot reinstall gnome-applets or any related packages.  I'm wondering if I broke a symbolic link between python and something else for dpkg, though, as the specific error seems to be with python:
> Preparing to replace gnome-applets 2.14.3-0ubuntu1 (using .../gnome-applets_2.14.3-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-applets ...
/var/lib/dpkg/info/gnome-applets.postrm: /usr/sbin/update-gconf-defaults: /usr/bin/python: bad interpreter: No such file or directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: /usr/sbin/update-gconf-defaults: /usr/bin/python: bad interpreter: No such file or directory


Is there a way to reconnect such a link?  Or is it not a link between dpkg and python, but maybe something removed from the path?  Any suggestions would be excellent.  My system is working, but it bugs the crap outta me to have anything broken.

Edit:  Doing more searches allowed me to gather more info.  Along with this problem, I am also unable to compile anything because everything returns the error that I have no c compiler.  I have reinstalled build-essential (and did dpkg --configure -a to make sure it was configured), and still get the same problem.  I don't think my system knows where to look for gcc and python, despite their binaries being in /usr/bin.  The output of ```
$echo $PATH
``` is > /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

As you can see, the path seems to point to /usr/bin still, so where else should I look for links to python, gcc, etc??

---

### Post by Belyel on 2006-11-09
Ok, problem solved.  I booted up the live CD, copied the contents of the /usr/bin of the temporary filesystem using ```
 sudo cp /usr/bin/*.* /media/UDISK20X/bin/ 
``` and figured that would catch all the files that I accidentally deleted with my rm *.* .  It seems to be working just fine now. I haven't tried to compile anything yet, but I was able to get gnome-app programs installed without errors.  woot woot.

---

