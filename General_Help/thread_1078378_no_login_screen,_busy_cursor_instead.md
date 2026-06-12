---
title: "no login screen, busy cursor instead"
date: 2009-02-23
forum: General Help
---

### Post by pirveli on 2009-02-23
Hi!
Today I wanted to install matplotlib-0.98.5 from Jaunty repos for my Ubuntu Intrepid system. To do so I edited /etc/apt/sources.list and copied some of the entries changing intrepid to jaunty. After that I managed to update matplotlib. Just after that I wasn't able to run vim any more:
```
vim: error while loading shared libraries: libgailutil.so.18: cannon open shared object file: No such file or directory
```
Apparently the file exists and is located in /usr/lib and /usr/lib/32... I tried to install libgail18 using Synaptic but 'it has no available version but it exists in database'. Then I removed matplotlib completely, reverted /etc/apt/sources.list and reinstalled matplotlib from Intrepid repos. libgailutil still is giving problems, but additionally I'm unable to login to gnome. After splash screen I can see cross cursor which transforms into busy and that's all.
Somewhere here I found that I could stop gdm and startx to desktop, but all I have is bw checked desktop with no panels at all, but fortunately I can use Yakuake to issue commands.
So right now you know how I messed up my system. The question is: how to make it run again?

regards
chriss

---

### Post by mgol on 2009-02-23
When You updated matplotlib, which other packages have You also updated? (I believe there were some dependencies that caused that). You can check Your last packages that was involved in "some activities" by executing:
```
ls -lrt /var/lib/dpkg/info/*.list
```
In this file packages are sorted via this order, the last column contains names like:
/var/lib/dpkg/info/PACKAGE_NAME.list
Look at the dates, You'll probably need to reinstall all the packages that was somehow changed after You messed up Your repositories list. You can try to reinstall those packages by:
```
sudo aptitude reinstall LIST_OF_ALL_THIS_PACKAGES
```
They should go back to their Intrepid versions.
If the number of affected packages is small, You can write them by Yourself. If not, it would be easier to select only names by using some console stuff, that is:
```
ls -lrt /var/lib/dpkg/info/*.list | tail -NNN | awk '{ printf "%s\n", $8 }' | cut -f6 -d/ | cut -f1 -d. | awk '{ printf "%s ", $1 }'
```
Where NNN is the number of last lines to display - select as big NNN as to cover (only) all affected packages.
This long command will produce a nice list of packages names separated by spaces. To use it, save it to file PACKAGES by adding:
```
 > PACKAGES
```
at the end this long command and then execute:
```
sudo aptitude reinstall `cat PACKAGES`
```

I hope it's somehow clear. ;)

---

### Post by pirveli on 2009-02-23
mgol, thanks for the reply...
I found several packages that were involved into disaster ;)
x11proto-input-dev
libxrandr2
libxi6
gtk2-engines-pixbuf
libgtk2.0-0
libgail-gnome-module
From the above list I was able to reinstall only the latter. For the rest I got an error :
```
E: I wasn't able to locate the file for the xxx package. This might mean you might have to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```
In Synaptic I have them checked but cannot 'Mark for Reinstallation'. Is there any way to have whole system rebuilt based on installed software? Everything was installed using Synaptic from stable sources. What else instead of reinstalling Ubuntu can I do to recover my system?

regards
chriss

---

### Post by mgol on 2009-02-23
Maybe flush first Your packages cache... Info is there:
[http://ubuntuforums.org/showpost.php?p=6528443&postcount=11](http://ubuntuforums.org/showpost.php?p=6528443&postcount=11)
And only then try reinstalling the above packages.

---

### Post by pirveli on 2009-02-23
Nope, that doesn't work. I still get the same errors and empty file named `lock` is created in /var/lib/apt/lists.

---

### Post by mgol on 2009-02-23
This lock file is normal.

Hmm... Maybe You should do:
```
sudo aptitude update
```
**twice** after flushing, then
```
sudo aptitude safe-upgrade
```
then:
```
sudo aptitude install -f
```
and only then try to reinstall all these packages?...

---

### Post by pirveli on 2009-02-23
Both updates went ok. Then upgrade did nothing (nothing to install) and after that I still get those errors.
I tried to reinstall gdm but I got the same error.
EDIT: that also didn't help

---

### Post by mgol on 2009-02-23
What about this solution:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)
?

---

### Post by pirveli on 2009-02-23
Still the same. I was able to reinstall libgail-gnome-module only (the one that gave no errors previously).
I really appreciate your help --- thanks :)

---

### Post by mgol on 2009-02-23
Have You tried reinstalling it using:
```
sudo apt-get --reinstall install PACKAGES_LIST
```
instead of:
```
sudo aptitude reinstall PACKAGES_LIST
```
? They are both dependent on apt, but they handle some things differently, it's worth to try both of them. Maybe try also:
```
sudo aptitude update && sudo aptitude dist-upgrade
```
dist-upgrade sometimes solves problems - mostly with dependencies, but it won't hurt to try...

I'm running out of ideas. I had some problems with apt, but all of them were able to be solved by one of the means I proposed at the beginning... :/

---

### Post by pirveli on 2009-02-24
Ok...
I just updated system from jaunty repos and everything is ok now. Thank you for your help.

regards
chriss

---

