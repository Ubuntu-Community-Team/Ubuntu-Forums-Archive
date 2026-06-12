---
title: "[Help] GNOME to KDE"
date: 2005-08-07
forum: Desktop Environments
---

### Post by johe07 on 2005-08-07
Hi, I'm Ubuntu Newbie.
I just fisnished install my Ubuntu with GNOME.

I would like to use KDE, it prompt me error.

here is my sources list:
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#KDE-3.4.2
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

When I ***sudo apt-get update***, it propmt me the following error:
> Fetched 4770kB in 2m16s (35.0kB/s)
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD recognized by APT. apt-get update cannot be used to add new CDs
Reading Package Lists... Done
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

After that, I go and ***sudo apt-get install kubuntu-desktop***
if show me:

> Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: python-imaging-sane but it is not going to be installed
                   Depends: python-newt but it is not going to be installed
                   Depends: xorg-driver-synaptics but it is not going to be installed
E: Broken packages

Is it my source list any problem?
Or my step wrongly??
May someone help me to correct it?

Thanks.

---

### Post by Reb on 2005-08-07
try removing the cdrom entry from /etc/apt/sources.list.

---

### Post by johe07 on 2005-08-07
Hi,

Thanks for reply. I had try it, but it still can't install the kubuntu-desktop.
It prompt me the same message after I ***apt-get install kubuntu-desktop***

---

### Post by drizek on 2005-08-07
[QUOTE=johe07]Hi,

Thanks for reply. I had try it, but it still can't install the kubuntu-desktop.
It prompt me the same message after I ***apt-get install kubuntu-desktop***[/QUOTE]
 try doing "apt-get install kde" then

---

### Post by johe07 on 2005-08-08
hi, drizek

Iit really work!!! I'm installing now...
It need around 894MB !!!

May I know why the previous command can't work?
Anyone can explain that the meaning of each line in the source list?


Thanks a lot!!! \\:D/  \\:D/

---

### Post by johe07 on 2005-08-08
Install failed.....

After download the packages, and when installing...
It got error...

After that when I restart, I can't loggin into e my default session. it prompt me:
> 
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could means that there is some installation problem or that you may be out of diskspace. Try loggin in with one of the failsafe session to see if you can fix this problem. 

When I install the KDE, I sure I will have around 15GB on the HDD. So it is impossible that I had out of diskspace, right?

May someone know how to solve the problem?
Help me....now I only can loggin to failsafe session, and I got no idea what I should do... :neutral:  :neutral:  :neutral:

---

### Post by drizek on 2005-08-08
thats something to do with messed up permissions or something. since you jsut installed ubuntu yesterday, why not just download a kubuntu iso and reinstall? there is a way to fix all this, but its a hassle.

---

### Post by johe07 on 2005-08-08
Because I wish to try manually install... because after I install ubuntu,  I just mention there had KDE ubuntu.

So it means there no way to fix it? have to re-install?

---

### Post by johe07 on 2005-08-08
[QUOTE=johe07]Because I wish to try manually install... because after I install ubuntu,  I just mention there had KDE ubuntu.

So it means there no way to fix it? have to re-install?[/QUOTE]
 Here is the ~/.xsession-error file:

> 
/etc/gdm/PreSession/Default: Registering you session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.xservers" -h "" -l ":0" "star07"

/etc/gdm/Xsession: Beginning session setup...

Failed to start message bus: Failed to read directory "/usr/lib/dbus-1.0/services": no such file or directory

EOF in dbus-launch reading address from bus daemon


---

### Post by johe07 on 2005-08-09
I re-update, and try install again, this time, it prompt me:

> 
Reading pakage list... Done
Building dependency tree... Done
kde is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following pakages have unmet dependencies:
  mozilla-firefox-gnome-support: Depends: firefox-gnoma-support but it is not
  going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packaged (or specify a solution).


Then I follow the instruction, just use ***apt-get -f install***
It works!  So it start installing the firefox package again...
But, I prompt me again:
> 
The following extra packages will be installed:
   firefox-xft-fonts xprint
The following NEW packages will be installed:
  firefox0 firefox-gnoma-support
0 upgraded, 2 newly installed, 0 to remove and 515 not upgraded.
696 not fully installed or removed.
Need to get 0B/9009kB of archives.
After unpacking 25.4MB of additional disk space will be used.
Do you want to continue [y/n] Y
WARNING: The following packages cannot be authenticated!
  firefox firefox-gnoma-support
Install there packages without verification [y/N]? Y

Preconfiguring packages ...
(Reading databse ... 110760 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.0.60lubuntul~5.05ubpl_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_1.0.6-lubuntul~5.04ubpl_i386.deb (- -unpack):
  trying to overwrite '/usr.lib/mozilla-firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf', which is also in package mozilla-firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking firefox-gnome-support )from .../firefox-gnoma-support_1.0.6-lubuntul~5.05ubpl_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox-gnoma-support_1.0.6-lubuntul~5.05ubpl_i386.deb (- -unpack):
  trying to overwrite '/usr/lib/mozilla-firefox/components/libnkgnomavfs.so', which is also in package mozilla-firefox
dbkg-deb: subprocess paste killed by signal (Broken pipe)
Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extensions/installed-extentions.txt still present. Registration might have gone wrong.
done.
Errors were encountered while processing:
  /var/cache/apt/archives/firefox_1.0.6-lubuntul~5.05ubpl_i386.deb
  /var/cache/apt/archives/firefox-gnoma-support_1.0.6-lubuntul~5.05ubpl_i386.deb
E: Sub-process /usr/bin/dbkg returned an error code (1)


---

### Post by poofyhairguy on 2005-08-09
You have to close Fireofx, then do that.

---

### Post by johe07 on 2005-08-10
Now i only can run on failsafe session, and my firefox cannot working already...
So, it means I not using the firefox when i running this installation.

Or, just assume it is running, and may I know how to manually close the running program?

---

