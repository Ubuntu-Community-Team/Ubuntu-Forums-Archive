---
title: "After hard shutdown, APT packages corrupted and no hardware detected"
date: 2015-04-08
forum: Desktop Environments
---

### Post by Alessandro_Antonel on 2015-04-08
Hi,
a few minutes ago I had to use a hard shutdown on my Ubuntu 14.04 while the system was struck working with the HDD (I had many tabs open on Chromium, it was probably busy moving swap memory).

Since then, Ubuntu doesn't recognize most of my laptop's hardware features: mouse isn't detected and I can only use touchpad and keyboard, screen resolution is set at 800x600 and can't be changed, network isn't working at all (wifi doesn't seem to exist anymore, and connecting via Ethernet cable or even USB tethering with my Android smartphone doesn't work either).
My user account, files and applications are still there and working.

It seems that some APT packages are corrupted, because when the updates manager prompted me to install updates, it crashed and suggested me to run the command
```
sudo apt-get install -f
```
but obviously I'm not able to run this command since it needs network connection which doesn't work.
I tried entering Ubuntu recovery mode, but the "repair broken packages" option needs network aswell; and the "system-summary" option says that APT package is **not **intact.

I'm writing this post from my laptop using Windows 8 where everything works as usual, so it's not an hardware problem.

Is there a way to fix it?

---

### Post by Bashing-om on 2015-04-08
Alessandro_Antonel; Hello;

In such situations of an inappropriate shut-down; I run a simple file system check :
```

sudo touch /forcefsck
sudo shutdown -r now

```
If that returns with errors, boot the liveDVD and run deeper file system repairs.
Next I would verify the package management system:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

``` fingers crossed that all goes well.

[INDENT][INDENT][INDENT]else;
[INDENT][INDENT][INDENT][INDENT]something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alessandro_Antonel on 2015-04-08
Thank you for replying!
> **Bashing-om said:**
> Alessandro_Antonel; Hello;

In such situations of an inappropriate shut-down; I run a simple file system check :
```

sudo touch /forcefsck
sudo shutdown -r now

```
If that returns with errors, boot the liveDVD and run deeper file system repairs.
 
I performed these steps and luckily I didn't get any error.

> **Bashing-om said:**
> 
Next I would verify the package management system

I performed these too but nothing changed. Under each you can see a summary of what I got as output (roughly translated from Italian system language), but in most cases the command couldn't reach the repositories on the Internet because network isn't detected either.

```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)

```
I got some lines ending with "Done"
```

sudo apt-get autoremove

```
I got some lines ending with" Done", then "executing apt-get -f install is useful to fix that", then a list of packages with unsatisfacted dependencies and then "E: dependencies not found. Retry using - f"
```

sudo apt-get clean
#refresh

```
Didn't display any output.
```

sudo apt-get update #resync package index

```
I get a huge list of "Unable to retrieve "http://ppa.launchpad.net ..." and "Unable to parse "archive.canonical.com" or similar addresses, the list ends with "W: unable to download some index files: they will be ignored, or old ones will be used instead"
```

sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories

```
Same output as sudo apt-get autoremove.
```

#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade

```
Same again. 
```

sudo apt-get -f install

```
Some output lines, then it says that the following packages are not needed anymore:
kde-ln10n-engb kde-l10n-it linux-headers-3.13.0-32
linux-headers-3.13.0-32-generic linux-image-3.13.0-32-generic
linux-image-extra-3.13.0-32-generic linux-singned-image-3.13.0.32-generic
The following packages will be installed:
libwebkitgtk-3.0-0
And the following packages will be updated:
libwebkitgtk-3.0-0
Then it says it needs to download 7230kB of archives and 5120 B of space will be occupied after this task. I press Y but error lines starting with "Unable to resolve"  and "Unable to download" appear again, and at the end it says "E: unable to download some packages. It may be useful to execute apt-get update or trying the --fix-missing option".
```

sudo dpkg --configure -a

```
This one doesn't display any output.

Thank you for the help but nothing seems to have changed :( Hope reporting all the outputs is useful to detect the problem!

---

### Post by Bashing-om on 2015-04-08
Alessandro_Antonel; Well ..

Not all bad. Seems now the big thing is no internet connectivity.

Can you connect to a wired connection ?
From a wired connection, what returns:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
Get on the 'net and get you updated.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by Alessandro_Antonel on 2015-04-09
No, there is no way to connect to the Internet. It looks like the entire network card has been removed from my laptop (while it works on Windows).
I tried connecting via an ethernet cable to my router but nothing happened, no notification appeared, even on my router the LED remained off, as if no device was plugged to that ethernet port.
I tried also USB tethering with my Android smartphone, but it didn't work either.

I just tried again and typed the commands you gave me. I always get the following outputs, both using ethernet cable and using USB tethering, and also when both are unplugged.

```
 
connect: Network is unreachable

ping: unknown host ubuntu.com

```

PS: I took a picture of the screen in which you can see the error icon that appeared at the top of the screen, and the error window that appears when the update manager crashes after trying to install updates:
[http://it.tinypic.com/r/2rom1y8/8](http://it.tinypic.com/r/2rom1y8/8)
The messages are in Italian, but basically the one at the top says that a package error occurred and the message is "BrokenCount >0" and that typically means there are unsolved dependencies; the other one says that the package system is corrupted and tells to run "sudo apt-get install -f"; the last one is the crash report window.

---

### Post by dino99 on 2015-04-09
Some times ago i have had a similar headache; after searching every corner cases i've finally found lot of broken links inside the various /etc/rc?.d folders
Simple delete them if you have some of them also as they are able to broke a system.
The other way is to glance at System-monitor and/or htop for problematic processes

---

### Post by Alessandro_Antonel on 2015-04-09
> **9d9 said:**
> Some times ago i have had a similar headache; after searching every corner cases i've finally found lot of broken links inside the various /etc/rc?.d folders
Simple delete them if you have some of them also as they are able to broke a system.
The other way is to glance at System-monitor and/or htop for problematic processes

Thank you for replying! I had 8 of these and I moved them to the desktop, but after turning the laptop off and then on again there was no improvement.
What do you mean by "htop for problematic processes"?

---

