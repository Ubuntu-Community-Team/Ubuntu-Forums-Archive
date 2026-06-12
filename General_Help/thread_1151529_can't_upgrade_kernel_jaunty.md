---
title: "can't upgrade kernel jaunty"
date: 2009-05-07
forum: General Help
---

### Post by americano70e10 on 2009-05-07
What did I do????
package manager says there is a new version of the linux kernel available but I can't upgrade it due to either:

1) Incomplete upgrade
II) Unofficial program packages not suported by ubuntu
or
C) Normal alterations of a Ubuntu development version

actually I don't know how they would look like in the english version (because my ubuntu is in portuguese) but that's what shows the upgrade manager.

Still, I don't remember doing an incomplete upgrade, and I have skype, picasa and picasa photo viewer that was not installed using apt-get but I did use .deb package files to install them, there's guake also but that one I compiled from source file (maybe it's him that's causing this), the rest was either apt-get or synaptic, and my ubuntu instalation was not from a beta version nor it was an upgrade from 8.10, I did a clean install with the publicly released version.

Can anyone help me out?

Thanks in advance...

---

### Post by geirha on 2009-05-07
First off, open a terminal and run ```
export LANG=
```
That will turn off translations for all commands run from that terminal.

Next, run ```
sudo dpkg --configure -a
``` If an update got interrupted while updating, that command should pick up where it left off, and finish it.

Next ```
sudo aptitude update
update-manager
```
And try upgrading again.

---

### Post by americano70e10 on 2009-05-07
well did all that but still have the same problem, but here's what the update-manager says:

Not all updates can be installed
This can be caused by:
A previous update which didn't complete
Problems with some of the isntalled software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-released vesion of Ubuntu

P.S.: Is there a way to make that "Export LANG=" permanent on the terminal? Because I have to use the portuguese version because of the "ç" which is not available in the english version (it would be like "&#347;", but instead of an "s" it would be a "c" and not like the "ç" that I need), but I would prefer if the terminal were in english.

---

### Post by geirha on 2009-05-07
> **americano70e10 said:**
> well did all that but still have the same problem, but here's what the update-manager says:

Not all updates can be installed
This can be caused by:
A previous update which didn't complete
Problems with some of the isntalled software
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-released vesion of Ubuntu


Hm. That message is indeed not very helpful. Try with
```
sudo aptitude safe-upgrade
# or possibly
sudo aptitude full-upgrade
```
Hopefully aptitude will be more specific.

> **americano70e10 said:**
> 
P.S.: Is there a way to make that "Export LANG=" permanent on the terminal? Because I have to use the portuguese version because of the "ç" which is not available in the english version (it would be like "&#347;", but instead of an "s" it would be a "c" and not like the "ç" that I need), but I would prefer if the terminal were in english.

As long as System -> Preferences -> Keyboard -> [Layouts] has Portuguese layout set, you can run Ubuntu in any language, and still be able to type Portuguese characters.

To answer your question though, adding ```
export LANG=en_US.utf8
``` at the end of the file ~/.profile should make all terminal commands run in English. It's better to set it to an utf8 locale (en_US.utf8) when you want to make it permanent. Make sure first though, that ```
locale -a
``` lists en_US.utf8 as a possible locale.

---

### Post by americano70e10 on 2009-05-07
```
felipe@rukia:~$ sudo aptitude safe-upgrade
[sudo] password for felipe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
The following packages have been kept back:
  linux-generic linux-image-generic linux-restricted-modules-generic 
The following packages will be REMOVED:
  python2.5{u} python2.5-minimal{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 15.0MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 124764 files and directories currently installed.)
Removing python2.5 ...
Removing python2.5-minimal ...
Unlinking and removing bytecode for runtime python2.5
    python-pkg-resources: 2.5, 2.6 (['install', 'ok', 'installed'])
    apturl: current (['install', 'ok', 'installed'])
    language-selector: current (['install', 'ok', 'installed'])
    python-fstab: all (['install', 'ok', 'installed'])
    jockey-common: 2.5, 2.6 (['install', 'ok', 'installed'])
    computer-janitor: all (['install', 'ok', 'installed'])
    python-software-properties: >= 2.4 (['install', 'ok', 'installed'])
    python-launchpad-integration: 2.5, 2.6 (['install', 'ok', 'installed'])
    gnome-app-install: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-apport: 2.5, 2.6 (['install', 'ok', 'installed'])
    gdebi-core: current (['install', 'ok', 'installed'])
    python-xkit: all (['install', 'ok', 'installed'])
    python-newt: 2.5, 2.6 (['install', 'ok', 'installed'])
    update-manager-core: 2.5, 2.6 (['install', 'ok', 'installed'])
    usb-creator: current (['install', 'ok', 'installed'])
    python-cairo: 2.5, 2.6 (['install', 'ok', 'installed'])
    alacarte: >= 2.4 (['install', 'ok', 'installed'])
    checkbox: current (['install', 'ok', 'installed'])
    gmountiso: all (['install', 'ok', 'installed'])
    gnome-codec-install: >= 2.4 (['install', 'ok', 'installed'])
    python-problem-report: 2.5, 2.6 (['install', 'ok', 'installed'])
    ufw: 2.5, 2.6 (['install', 'ok', 'installed'])
    command-not-found: current (['install', 'ok', 'installed'])
    launchpad-integration: all (['install', 'ok', 'installed'])
    python-xapian: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-gst0.10: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-numpy: 2.5, 2.6 (['install', 'ok', 'installed'])
    gdebi: current (['install', 'ok', 'installed'])
    screen-resolution-extra: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-pyatspi: >= 2.4 (['install', 'ok', 'installed'])
    python-launchpad-bugs: >= 2.4 (['install', 'ok', 'installed'])
    python-virtkey: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-imaging: 2.5, 2.6 (['install', 'ok', 'installed'])
    ubuntu-system-service: current (['install', 'ok', 'installed'])
    python-apt: 2.5, 2.6 (['install', 'ok', 'installed'])
    nvidia-common: 2.5, 2.6 (['install', 'ok', 'installed'])
    onboard: current (['install', 'ok', 'installed'])
    language-selector-common: current (['install', 'ok', 'installed'])
    update-manager: 2.5, 2.6 (['install', 'ok', 'installed'])
    python-uno: 2.6 (['install', 'ok', 'installed'])
    software-properties-gtk: >= 2.4 (['install', 'ok', 'installed'])
    python-pysqlite2: 2.5, 2.6 (['install', 'ok', 'installed'])
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

felipe@rukia:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  linux-restricted-modules-generic 
The following NEW packages will be installed:
  linux-image-2.6.28-12-generic 
The following packages will be upgraded:
  linux-generic linux-image-generic 
3 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6MB of archives. After unpacking 95.7MB will be used.
The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.28-12-generic which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic

Keep the following packages at their current version:
linux-restricted-modules-generic [2.6.28.11.15 (jaunty, now)]

Score is 189

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-generic [2.6.28.11.15 (jaunty, now)]
linux-image-generic [2.6.28.11.15 (jaunty, now)]
linux-restricted-modules-generic [2.6.28.11.15 (jaunty, now)]

Score is 260

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic
linux-restricted-modules-generic

Score is 188

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.


```

I did both but it seems "safe-upgrade"removed python 2.5 and full-upgrade is trying to remove the kernel without replacing it (I don't know much about these things).

Also setting the keyboard layout to ABNT (brazilian layout) doen't work because my keyboard layout is USA intl, and the problem is that when I press ' + "c" I get that "&#347;" but with a "c"underneath instead of the "s" and the one I need is "ç". But no need to focus on this problem, I just want to fix that kernel update problem...

---

### Post by geirha on 2009-05-07
Well, now we know what the problem is. The package linux-restricted-modules-generic is broken for some reason. Not sure how to fix that. Try reinstalling the package
```
sudo aptitude reinstall linux-restricted-modules-generic
```

---

### Post by americano70e10 on 2009-05-07
I did that but no change...

---

### Post by geirha on 2009-05-07
Hm, ok, try this: [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by fabertawe on 2009-05-07
I also have this problem. linux-restricted-modules-generic wants to update from 2.6.8.28.11.15 to 2.6.8.28.11.16 but linux-restricted-modules-common and linux-restricted-modules-2.6.28-11-generic are still at version 2.6.8.28.11.15 and 2.6.28-11.15 respectively.

Presumably the repo will update, soon hopefully, with the missing new packages. Until then I just boot with the previous kernel.

---

### Post by LaDeuce on 2009-05-07
Just wanted to check-in that I'm seeing this also (you are not alone).  Waiting for the repository to be updated to fix the problem.

---

### Post by americano70e10 on 2009-05-07
yeah, gotta wait then... But thanks for your help and interest geirha...

---

### Post by lifereversal on 2009-05-07
from terminal:

> sudo apt-get dist-upgrade

---

### Post by bmw on 2009-06-09
Took me four days to find this fix. This totally did it for me.  Seems pretty simple (and obvious) to include in the distribution and to fix such a major problem.  I was several x.x.versions-x behind. Can't imagine the performance hit. We'll see after the download, install and reboot.

> **geirha said:**
> First off, open a terminal and run ```
export LANG=
```
That will turn off translations for all commands run from that terminal.

Next, run ```
sudo dpkg --configure -a
``` If an update got interrupted while updating, that command should pick up where it left off, and finish it.

Next ```
sudo aptitude update
update-manager
```
And try upgrading again.

---

