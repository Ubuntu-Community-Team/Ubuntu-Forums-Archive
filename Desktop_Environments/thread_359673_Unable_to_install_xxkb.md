---
title: "Unable to install xxkb"
date: 2007-02-12
forum: Desktop Environments
---

### Post by MasterOfMuppets on 2007-02-12
Hi all, I'm running KDE Edgy here and I can't install xxkb for switching between keyboard layouts. Got this log for a

```
sudo apt-get install xxkb
```

command.

```
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
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  xxkb: Depends: libx11-6 but it is not going to be installed
        Depends: libxpm4 but it is not going to be installed
        Depends: libxt6 but it is not going to be installed
E: Broken packages

```

Any ideas? I'll try to re-install all the dependencies.

EDIT:
When I manage to turn on the synaptic and try to install it, it says the same thing but also wants to install GNOME again (I went for pure KDE).

---

### Post by an.echte.trilingue on 2007-02-12
This is just a shot in the dark, but when was the last time you updated your package lists?

```
sudo apt-get update
```

---

### Post by an.echte.trilingue on 2007-02-12
Also, there is a kde-native package for this that is called (I think) kbstate.  Might work better for you.

---

### Post by MasterOfMuppets on 2007-02-12
kb state only shows what language I can type. It doesn't  switch between keyboard layouts...

---

### Post by an.echte.trilingue on 2007-02-12
You can't right click on it and add languages?

Also, your error with xxkb might be caused by your system being a bit stale... when was the last time you upgraded?

---

### Post by MasterOfMuppets on 2007-02-12
My system is fully up to date...
Is there any way to go around this?

---

### Post by an.echte.trilingue on 2007-02-12
I am not sure what is causing this; I just installed xxkb and it works fine.  I was just browsing your OP again...

Just out of curiosity, did you upgrade from dapper to edgy?

---

### Post by MasterOfMuppets on 2007-02-12
Nope... I installed Ubuntu, upgraded to Kubuntu, went down to pure KDE and that's that.

---

### Post by MasterOfMuppets on 2007-02-12
An update!
As I am getting more and more emotionally unstable, I looked up the manual for apt-get and tried the --fix-broken option and got this:
```
moshewe@moshewe-laptop:~$ sudo apt-get install xxkb --fix-broken
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
  xxkb: Depends: libx11-6 but it is not going to be installed
        Depends: libxpm4 but it is not going to be installed
        Depends: libxt6 but it is not going to be installed
E: Broken packages

```

Hope it helps...

---

### Post by MasterOfMuppets on 2007-02-12
Another update!
This time I used sudo aptitude install xxkb and this is what I got:

```
moshewe@moshewe-laptop:~$ sudo aptitude install xxkb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  x11-common
The following NEW packages will be installed:
  xxkb
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.1kB of archives. After unpacking 188kB will be used.
The following packages have unmet dependencies:
  x11-common: Conflicts: xxkb (<= 1.10-2.1) but 1.10-2.1 is to be installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

So then I tried sudo aptitude reinstall x11-common and got this:

```
moshewe@moshewe-laptop:~$ sudo aptitude reinstall x11-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  x11-common
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 291kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com edgy-updates/main x11-common 1:7.1.1ubuntu6.2 [291kB]
Fetched 291kB in 2s (102kB/s)
Preconfiguring packages ...
(Reading database ... 136901 files and directories currently installed.)
Preparing to replace x11-common 1:7.1.1ubuntu6.2 (using .../x11-common_1%3a7.1.1ubuntu6.2_i386.deb) ...
Unpacking replacement x11-common ...
Setting up x11-common (7.1.1ubuntu6.2) ...
 System startup links for /etc/init.d/x11-common already exist.

```

Can anyone tell me how to edit what to make this work :confused: ?

---

### Post by MasterOfMuppets on 2007-02-13
Update...
In despair I re-installed with the Kubuntu live CD, but the problem persists. Help... :(

---

### Post by 444 on 2007-10-25
Also in gutsy.... any ideas? The three mentioned packages are all there already.

```

sudo apt-get install xxkb
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
  xxkb: Depends: libx11-6 but it is not going to be installed
        Depends: libxpm4 but it is not going to be installed
        Depends: libxt6 but it is not going to be installed
E: Broken packages

```

---

