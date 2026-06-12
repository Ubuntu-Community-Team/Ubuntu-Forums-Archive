---
title: "apt-get / dpkg problem ..."
date: 2006-07-12
forum: Desktop Environments
---

### Post by RaZer0r on 2006-07-12
whenever I try to install any program using dpkg of apt-get (havent tried the ./configure yet) i get this error.
```

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb (--unpack):
 unable to open files list file for package `gtk2-engines-mist': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone any suggestions? I allready tried:
- sudo dpkg -S gtk2-engines-mist
- sudo apt-get dist-upgrade
- sudo apt-get --reinstall install dpkg

tried a reinstall from synaptic.. uninstall, , complete uninstall, none of them did anything that got me forward...

---

### Post by snellgrove on 2006-07-12
I'm getting this a lot lately :(

i can always fix it by typing in:

sudo apt-get clean
sudo apt-get autoclean

and then typing in sudo apt-get install <whatever it was>

and it generally works, as it clears the local apt packages, and forces Apt-get to fetch them from the servers again.

dunno why its doing it though, hope this helps :)

---

### Post by RaZer0r on 2006-07-12
trying now.. lets see if this solves it

---

### Post by philippe_carlo on 2006-07-12
Could it be that your disk (or var-partition) is close to being full?

---

### Post by RaZer0r on 2006-07-12
nop, it didn't do the trick, quite anoying, i'm an update freak :p...

---

### Post by RaZer0r on 2006-07-12
nop... 
partitions all more or less good enough...
/ : 1.8 gig free
/home : 16 gig free

those are the only 2 partitions that realy matter (don't have a /var /usr /boot /temp /whatever...

---

### Post by philippe_carlo on 2006-07-12
Maybe the package is broken. You should try if you have the same problems with other packages. If that is not the case, you should post a bug report.

---

### Post by RaZer0r on 2006-07-12
it has this with every thing i try to install/uninstall/upgrade... bit stuck here

---

### Post by philippe_carlo on 2006-07-12
Yes, apt will try to install the broken package first. You should remove it with apt-get remove or with dpkg first.

---

### Post by RaZer0r on 2006-07-12
wont do :)

```

rein@ubuntu:~$ sudo apt-get remove gtk2-engines-mist
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gnome-themes gtk2-engines-mist ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 28 not upgraded.
Need to get 0B of archives.
After unpacking 2204kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing ubuntu-desktop (--remove):
 unable to open files list file for package `gtk2-engines-mist': Input/output error
Errors were encountered while processing:
 ubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by philippe_carlo on 2006-07-12
Are there a lot of packages in /var/cache/apt/archives? If so remove them, especially the one for `gtk2-engines-mist'. Then try again. Otherwise, you must have to remove the dependency from dpkg itself with 
sudo dpkg -r --force-all <package-name>

Hope that helps.

---

### Post by RaZer0r on 2006-07-12
none of those methods worked ...
I cleared the /var/cache/apt/archives folder with sudo rm *.bin, and tried to get an dist-upgrade... failed

the force-all didn't work either...
output:
```

rein@ubuntu:~$ sudo dpkg -r --force-all gtk2-engines-mist
dpkg: gtk2-engines-mist: dependency problems, but removing anyway as you request:
 gnome-themes depends on gtk2-engines-mist.
 ubuntu-desktop depends on gtk2-engines-mist.
(Reading database ... dpkg: error processing gtk2-engines-mist (--remove):
 unable to open files list file for package `gtk2-engines-mist': Input/output error
Errors were encountered while processing:
 gtk2-engines-mist
Processing was halted because there were too many errors.

```

---

### Post by SigmaX on 2006-07-12
> **RaZer0r said:**
> none of those methods worked ...
I cleared the /var/cache/apt/archives folder with sudo rm *.bin, and tried to get an dist-upgrade... failed


Um...  unless I missed something, Debian packages end in .deb, not .bin.  If you want to clear all the packages this will do it automatically:

```
$ sudo apt-get clean
```

SigmaX

---

### Post by RaZer0r on 2006-07-12
sorry my mistake i did "sudo rm *.deb" :) just a mistake :) (i verified if the folder was empty and it was )

The apt-get clean i allready did.. getting a bit frustrated

---

### Post by RaZer0r on 2006-07-13
no-one with any ideas? damit, this sux, never had this one before...

---

### Post by SigmaX on 2006-07-13
Not sure if it'll help, but a similar issue is here:

[https://lists.ubuntu.com/archives/kubuntu-users/2006-May/005765.html](https://lists.ubuntu.com/archives/kubuntu-users/2006-May/005765.html)

SigmaX

---

### Post by RaZer0r on 2006-07-14
just did a reinstall, hope it never fails again... but hey, a reinstall just took 10 mins ;)

---

