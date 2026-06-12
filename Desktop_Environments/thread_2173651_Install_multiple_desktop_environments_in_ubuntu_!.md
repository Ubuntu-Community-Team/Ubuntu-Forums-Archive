---
title: "Install multiple desktop environments in ubuntu !"
date: 2013-09-10
forum: Desktop Environments
---

### Post by Logic_Defyer on 2013-09-10
I decided to try and install gnome 3 and cinnamon on ubuntu , but i found that gnome 3 either wiped cinnamon of it was the other way around , is there any remedy to the problem , i also mean to install kde on the same installation .

---

### Post by TheFu on 2013-09-10
Always create a new user account when testing new DEs.  That's really the only advice I have.  This will keep the settings from clobbering each other, since you'll login using a different userid and different HOME for each user.

---

### Post by ibjsb4 on 2013-09-10
If your box is up to it, you could turn it into a [VirtualBox]("https://www.virtualbox.org/") :)

Their is a learning curve, but I think its worth the effort.  Once you get the hang of it, exploring different distro's and flavors is easy.  No more need to burn a cd/dvd.  Make a big mistake?  You can go back in time, before the mistake and try again.  Your hdd size is the limit of how many different environments you can have.

---

### Post by deadflowr on 2013-09-10
What version of Ubuntu are you running?
If 13.04(raring) both gnome shell(w/classic/fallback/flashback) and cinnamon are in the repos.
Previous versions of Ubuntu cinnamon has a ppa
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

Both work fine, since only one can run at a time, per user session.
Multiple users running different desktops work fine as well.
Installing gnome is actually easier then you might expect.
run
```
sudo apt-get update
sudo apt-get install gnome-tweak-tool
```
when this is installed, you'll get the full gnome desktop plus of course the tweak tool, which is a big plus.

But getting back on point, what do you mean by gnome3 and cinnamon wipe each other out?

---

### Post by Logic_Defyer on 2013-09-11
Looks like installing Cinnamon with aptitude solved the problems , strange i also have a fedora install , there stuff works just fine with no tweaking . 
Looks like gnome 3 updates a few wayward packages. 


$ sudo apt-get install aptitude
$ sudo aptitude install cinnamon
[sudo] password for <USER>: 
The following NEW packages will be installed:
  cinnamon{b} gir1.2-muffin-3.0{a} libmuffin0{a} muffin-common{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,255 kB of archives. After unpacking 9,065 kB will be used.
The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0 which is a virtual package.
            Depends: libmozjs185-1.0 (>= 1.8.5-1.0.0+dfsg) but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     cinnamon [Not Installed]                           



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Install the following packages:                                                           
1)     libmozjs185-1.0 [1.8.5-1.0.0+dfsg-4 (raring)]                                           

     Downgrade the following packages:                                                         
2)     gjs [1.36.1+js17-0ubuntu1~raring0 (now, raring) -> 1.34.0-0ubuntu1 (raring)]            
3)     gnome-shell [3.8.1-0ubuntu1~raring1.2 (now, raring) -> 3.6.3.1-0ubuntu6 (raring)]       
4)     gnome-shell-common [3.8.1-0ubuntu1~raring1.2 (now, raring) -> 3.6.3.1-0ubuntu6 (raring)]
5)     gnome-sushi [3.8.0-1~ubuntu13.04.2 (now, raring) -> 3.6.1-0ubuntu1 (raring)]            
6)     libgjs0c [1.36.1+js17-0ubuntu1~raring0 (now, raring) -> 1.34.0-0ubuntu1 (raring)]       



Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  gjs gnome-shell gnome-shell-common gnome-sushi libgjs0c 
The following NEW packages will be installed:
  cinnamon gir1.2-muffin-3.0{a} libmozjs185-1.0{a} libmuffin0{a} muffin-common{a} 
0 packages upgraded, 5 newly installed, 5 downgraded, 0 to remove and 0 not upgraded.
Need to get 4,992 kB of archives. After unpacking 12.4 MB will be used.
Do you want to continue? [Y/n/?] y

---

### Post by deadflowr on 2013-09-11
Are you running ppa's for gnome?
Cinnamon has had known compatibility issues with gnome3.8.
hence the need to downgrade from the 3.8 series to the 3.6 series.
gnome 3.6 is what raring is locked on.

---

