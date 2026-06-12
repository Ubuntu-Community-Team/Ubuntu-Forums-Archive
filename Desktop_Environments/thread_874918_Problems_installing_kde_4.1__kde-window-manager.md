---
title: "Problems installing kde 4.1 / kde-window-manager"
date: 2008-07-30
forum: Desktop Environments
---

### Post by relativity on 2008-07-30
I am trying to install kde 4.1 but I am having a problem. 

  kde-window-manager
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main kde-window-manager 4:4.1.0-0ubuntu1~hardy1~ppa1 [1396kB]
Fetched 1396kB in 2min18s (10.1kB/s)
(Reading database ... 210268 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do i fix the problem?

---

### Post by yeats on 2008-07-30
I just got the same error message myself when trying to install kde4 alongside kubuntu Hardy.  Maybe a bug?

Chris

---

### Post by kuja on 2008-07-30
Try this maybe?

```
sudo apt-get remove kde-window-manager kdebase-runtime-data
sudo apt-get clean
sudo apt-get update
sudo apt-get install kubuntu-kde4-desktop
```

---

### Post by yeats on 2008-07-30
Actually . . .  try this.

Either in the Adept Package Manager or in the terminal, purge kubuntu-kde4-desktop and remove any other kde4 packages you see, then use the terminal and reinstall:

```
sudo apt-get install kubuntu-kde4-desktop
```

The second time it installed for me without errors and I was able to log out and log into KDE 4.

If *that* doesn't work, um. . . I'm not sure! :)

Chris

---

### Post by ukblacknight on 2008-08-01
I'm having the exact same problem as the OP.  I've tried 'sudo apt-get -f install', however this fails too.

```
tom@BlacKnight:~$ sudo apt-get remove kubuntu-kde4-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  kwin-kde4: Depends: kde-window-manager but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
tom@BlacKnight:~$ 

```

```
tom@BlacKnight:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  kde-window-manager
The following NEW packages will be installed
  kde-window-manager
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
28 not fully installed or removed.
Need to get 0B/1394kB of archives.
After this operation, 4477kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 162528 files and directories currently installed.)
Unpacking kde-window-manager (from .../kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb) ...
Replacing files in old package kdebase-workspace-data ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/doc/kde4/HTML/en/kcontrol/kwindecoration/index.docbook', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@BlacKnight:~$ 

```

This is really annoying, because I'm unable to use my package manager!  I can't even install/remove anything using the terminal, as it wishes to fix this broken package using sudo apt-get -f install.

---

### Post by dagamant on 2008-08-01
iv got a similar problem, but im able to use spt-get and synaptic normally. heres my output:

dagamant@dagamant-laptop:~$ sudo apt-get install kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-kde4-desktop: Depends: ark-kde4 but it is not going to be installed
                        Depends: dolphin-kde4 but it is not going to be installed
                        Depends: juk-kde4 but it is not going to be installed
                        Depends: kde-window-manager but it is not going to be installed
                        Depends: kdebase-bin-kde4 but it is not going to be installed
                        Depends: kdebase-runtime-bin-kde4 but it is not going to be installed
                        Depends: kdebase-workspace-bin but it is not going to be installed
                        Depends: kdemultimedia-kio-plugins-kde4 but it is not going to be installed
                        Depends: kdm-kde4 but it is not going to be installed
                        Depends: khelpcenter-kde4 but it is not going to be installed
                        Depends: kmix-kde4 but it is not going to be installed
                        Depends: knetworkconf-kde4 but it is not going to be installed
                        Depends: konsole-kde4 but it is not going to be installed
                        Depends: kscd-kde4 but it is not going to be installed
                        Depends: ksnapshot-kde4 but it is not going to be installed
                        Depends: okular-kde4 but it is not going to be installed
                        Depends: systemsettings-kde4 but it is not going to be installed
                        Recommends: dragonplayer but it is not going to be installed
                        Recommends: gwenview-kde4 but it is not going to be installed
                        Recommends: kamera-kde4 but it is not going to be installed
                        Recommends: kate-kde4 but it is not going to be installed
                        Recommends: kdesudo-kde4 but it is not going to be installed
                        Recommends: klipper-kde4 but it is not going to be installed
                        Recommends: kmilo-kde4 but it is not going to be installed
                        Recommends: konqueror-kde4 but it is not going to be installed
                        Recommends: konqueror-nsplugins-kde4 but it is not going to be installed
                        Recommends: kopete-kde4 but it is not going to be installed
                        Recommends: kppp-kde4 but it is not going to be installed
                        Recommends: krdc-kde4 but it is not going to be installed
                        Recommends: krfb-kde4 but it is not going to be installed
                        Recommends: ksysguard-kde4 but it is not going to be installed
                        Recommends: kwalletmanager-kde4 but it is not going to be installed
E: Broken packages
dagamant@dagamant-laptop:~$ 

iv tried:
 sudo apt-get clean
 sudo apt-get install -f
 sudo apt-get --fix-missing
 sudo dpkg --configure -a
 i installed gtkorphan and removed all orphaned packages
 tried to filter broken packages in synaptic but none are found
 double checked that i had the right repository


any other ideas? it dosnt tell me what package is broken.

---

### Post by GS2 on 2008-08-01
As far as I know apt-get does not have a log file, you may wish to try aptitude instead (man aptitude for details), log file is located /var/log/aptitude.

Although this log only displays actions (i.e. things removed/installed).

Problems with packages may be displayed in /var/log/dpkg.log - much more verbose and informative

---

### Post by ukblacknight on 2008-08-01
sudo aptitude purge fixed missing dependencies problem for me!  Cheers!  I'll try and install the kubuntu-kde-desktop again, and see what happens.

---

### Post by kuja on 2008-08-01
Okay, I went through this with someone yesterday in #kubuntu-kde4 and have a way that should work 100%, it's a bit red-buttonish, but it works very well.

If you have a lot of kde4 stuff outside of the "default" installed already, do this first.

```
sudo apt-cache rdepends kdebase-runtime-data | grep "^ .*" | tr '\n' ' ' > ~/backed_up_package_list
```

```
sudo dpkg --remove $(apt-cache rdepends kdebase-runtime-data | grep "^ .*" | tr '\n' ' ') kdebase-runtime-data
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-kde4-desktop
```

If you backed some things up earlier, you can restore them now:

```
sudo apt-get install $(cat ~/backed_up_package_list)
```

---

### Post by Quasaur on 2008-08-04
If there are ANY kde4 packages that are version 4.0.x remove them, then do the other things recommended in this post.

dpkg-query --list *kde4* | grep ii

or

dpkg-query --list *kde4* | grep 4.0


this will show you what kde4 packages are installed version 4.0.x and need to be removed.

...good fortune!

---

