---
title: "aptitude wildcards"
date: 2006-08-03
forum: Desktop Environments
---

### Post by aptget on 2006-08-03
I've recently read on Psychocats about the wonders of aptitude and decided to convert to it. I have this bash .sh script that I run after a new install is patched up to the latest packages and restarted if kernel is upgraded.

The problem lies within wildcard package installation. When running it, it would say it couldn't find packages, but then listed all the packages that were found. First thought for help was the man page and I read this (paraphrased):

"if a package name contains ~, it will be treated as a search pattern and every package matching the pattern will be installed"

So, I try that but I got a message saying no packages would be installed.

The man page says (see the section "Search Patterns" in the aptitude reference manual), when talking about wildcards but it doesn't say where it is.

---

### Post by aysiu on 2006-08-03
I think this is what the *man* page means: ```
sudo aptitude install win-baghira
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "win-baghira".  However, the following
packages contain "win-baghira" in their name:
  kwin-baghira
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
``` It couldn't find *win-baghira*, so it suggested the next closest thing--*kwin-baghira*.

---

### Post by aptget on 2006-08-03
First result from the bash script using * as a wildcard:

```

~$ sudo aptitude install gstreamer0.10-plugin*
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "gstreamer0.10-plugin*".  However, the following
packages contain "gstreamer0.10-plugin*" in their name:
  gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-base-dbg
  gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-good-doc
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-base
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Second result from me running the command manually with ~ as a wildcard:

```

~$ sudo aptitude install gstreamer0.10-plugin~
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Not really sure where the ~ goes.

---

### Post by 5-HT on 2006-08-03
> **aptget said:**
> 
The problem lies within wildcard package installation. When running it, it would say it couldn't find packages, but then listed all the packages that were found. First thought for help was the man page and I read this (paraphrased):

"if a package name contains ~, it will be treated as a search pattern and every package matching the pattern will be installed"

So, I try that but I got a message saying no packages would be installed.

The man page says (see the section "Search Patterns" in the aptitude reference manual), when talking about wildcards but it doesn't say where it is.

The reference manual with a section on available search patterns (e.g., ~c for residual config) can be found in /usr/share/aptitude/README.
The ~ is not synonymous with a wildcard character, but is rather used along with other defined characters to specify a certain search pattern (which are all documented in the README).

Hope that helps.

---

### Post by aptget on 2006-08-03
> **5-HT said:**
> The reference manual with a section on available search patterns (e.g., ~c for residual config) can be found in /usr/share/aptitude/README.
The ~ is not synonymous with a wildcard character, but is rather used along with other defined characters to specify a certain search pattern (which are all documented in the README).

Hope that helps.

Sweet. I found out what I was looking for. It's 'install ~n<package name>'.

Only problem is that I get something really weird. I'm assuming it's from aptitude automatically selecting 'recommends' packages also:

```

~$ sudo aptitude install ~ngstreamer0.10-plugin-
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-media rhythmbox serpentine sound-juicer totem-gstreamer
  ubuntu-desktop
The following packages will be REMOVED:
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2712kB will be freed.
The following packages have unmet dependencies:
  gnome-media: Depends: gstreamer0.10-plugins-base (>= 0.10.3) but it is not ins tallable
               Depends: gstreamer0.10-plugins-good but it is not installable
  rhythmbox: Depends: gstreamer0.10-plugins-base but it is not installable
             Depends: gstreamer0.10-plugins-good but it is not installable
  ubuntu-desktop: Depends: gstreamer0.10-plugins-base-apps but it is not install able
  totem-gstreamer: Depends: gstreamer0.10-plugins-base but it is not installable
                   Depends: gstreamer0.10-plugins-good but it is not installable
  serpentine: Depends: gstreamer0.10-plugins-base but it is not installable
              Depends: gstreamer0.10-plugins-good but it is not installable
  sound-juicer: Depends: gstreamer0.10-plugins-base but it is not installable
                Depends: gstreamer0.10-plugins-good but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Keep the following packages at their current version:
gstreamer0.10-plugins-base [0.10.7-0ubuntu4 (dapper, now)]
gstreamer0.10-plugins-good [0.10.3-0ubuntu4 (dapper, now)]

Score is -399

Accept this solution? [Y/n/q/?]

```

Other than this, I'm all set.

---

### Post by 5-HT on 2006-08-03
> **aptget said:**
> Sweet. I found out what I was looking for. It's 'install ~n<package name>'.

Only problem is that I get something really weird. I'm assuming it's from aptitude automatically selecting 'recommends' packages also...

About the conflicts, what about removing that last '-' from your command and adding an 's' in its place? Also, it is always a good idea to do a simulated dry-run (using the -s flag; no need for sudo) just to make sure aptitude's doing what you'd like. 

About treating recommended packages as dependencies, that is the default setting for aptitude in Ubuntu. To change the setting you can either do it from the aptitude's pseudo-GUI mode, edit ~/.aptitude/config (settings are described in the README), or use the *-R *flag for a one time thing.


HTH

---

### Post by aptget on 2006-08-03
> **5-HT said:**
> About the conflicts, what about removing that last '-' from your command and adding an 's' in its place? Also, it is always a good idea to do a simulated dry-run (using the -s flag; no need for sudo) just to make sure aptitude's doing what you'd like. 

About treating recommended packages as dependencies, that is the default setting for aptitude in Ubuntu. To change the setting you can either do it from the aptitude's pseudo-GUI mode, edit ~/.aptitude/config (settings are described in the README), or use the *-R *flag for a one time thing.


HTH

Ahhh, the problem was the - at the end like you suggested. I forgot to change that after I got rid of the * from regular apt-get. Works good now:

```

~$ sudo aptitude install ~ngstreamer0.10-plugins
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for gstreamer0.10-plugins
The following NEW packages will be automatically installed:
  liba52-0.7.4 libfaad2-0 libgsm1 libid3tag0 libmms0 libmpeg2-4 libsidplay1 libswfdec0.3
  libwavpack0
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-good-dbg
  gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg
  gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse liba52-0.7.4 libfaad2-0
  libgsm1 libid3tag0 libmms0 libmpeg2-4 libsidplay1 libswfdec0.3 libwavpack0
0 packages upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 4760kB of archives. After unpacking 13.9MB will be used.
Do you want to continue? [Y/n/?]

```

Whoo hoo! :D

---

